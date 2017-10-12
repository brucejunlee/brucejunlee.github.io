---
layout: post
title: "TensorFlow(二)：应用"
author: "李军"
categories: journal
tags: [tensorflow, deep learning]
image:
  feature: tf.jpg
  teaser: tf-teaser.jpg
  credit: 
  creditlink: ""
---

## 注意事项
### 在Jupyter notebook中，定义新节点前，我们需要开始调用*tf.reset\_default\_graph()*以清空符号图。

### 张量初始值

```python
weights = tf.Variable(tf.random_normal([784, 200], stddev=0.35),
                      name="weights")
# Create another variable with the same value as 'weights'.
w2 = tf.Variable(weights.initialized_value(), name="w2")
# Create another variable with twice the value of 'weights'
w_twice = tf.Variable(weights.initialized_value() * 0.2, name="w_twice")
```

### 张量的静态／动态形状(Shape)
```python
import tensorflow as tf

t = tf.placeholder(tf.float32, [None, 128])
static_shape = t.shape.as_list()
t.set_shape([32, 128])

dynamic_shape = tf.shape(t)
t.set_shape([None, 128])

t = tf.reshape(t, [32, 128])
```
### 作用域(Scope)
*tf.name\_scope*只影响由*tf.Variable*创建的张量和变量的名称, 并不影响由*tf.get\_variable*创建的变量名称。但如果重名，*tf.get_variable*会返回**ValueError**，如果想重用名称，需要设置参量`reuse=True`

```python
with tf.variable_scope("scope"):
  a = tf.constant(1, name="a")
  print(a.name)  # prints "scope/a:0"

  b = tf.Variable(1, name="b")
  print(b.name)  # prints "scope/b:0"

  c = tf.get_variable(name="c", shape=[])
  print(c.name)  # prints "scope/c:0"
  
with tf.variable_scope("scope"):
  a1 = tf.get_variable(name="a", shape=[])
  a2 = tf.get_variable(name="a", shape=[])  # Disallowed
  
with tf.variable_scope("scope"):
  a1 = tf.get_variable(name="a", shape=[])
with tf.variable_scope("scope", reuse=True):
  a2 = tf.get_variable(name="a", shape=[])  # OK
```

### 广播机制(broadcasting)
在TensorFlow计算中，使用广播时要非常小心仔细，尤其是在*tf.squeeze*时。一般经验是使用时总是显式给出维度信息。

### TensorFlow中数据读取方式

+ *tf.constant*

+ 使用占位符，然后`feed_dict`

+ *tf.py\_func*

+ 推荐使用数据集API

	```python
	actual_data = np.random.normal(size=[100])
	dataset = tf.contrib.data.Dataset.from_tensor_slices(actual_data)
	data = dataset.make_one_shot_iterator().get_next()
	```
 
 或从文件中读入
 
 ```python
 dataset = tf.contrib.data.Dataset.TFRecordDataset(path_to_data)
 ```
 
 然后进行数据(预)处理
 
 ```python
 dataset = dataset.cache()
if mode == tf.estimator.ModeKeys.TRAIN:
    dataset = dataset.repeat()
    dataset = dataset.shuffle(batch_size * 5)
dataset = dataset.map(parse, num_threads=8)
dataset = dataset.batch(batch_size)
 ```

### 切片
切片是一个非常低效的操作，我们尽量使用*tf.unstack*操作来代替使用**slice**，尤其是在切片数非常多时。

```python
import tensorflow as tf
import time

x = tf.random_uniform([500, 10])

z = tf.zeros([10])
for i in range(500):
	z += x[i]
	
sess = tf.Session()
start = time.time()
sess.run(z)
print("It took %f seconds." % (time.time() - start))

```

更好的方式是使用*tf.unstack*操作将矩阵一次性切分成向量列表

```python
z = tf.zeros([10])
for x_i in tf.unstack(x):
	z += x_i
```

最合适做法

```python
z = tf.reduce_sum(x, axis=0)
```

### 运算符重载(overload)
+ `x += y`, `x **= 2`是合法的
+ **and**, **or**, **not**等关键字不能被重载，代替地，我们使用*tf.logical\_and*, *tf.logical\_or*, *tf.logical\_xor*, *tf.logical\_not*
+ 张量不能作为布尔值用于判断，代替地，我们可以使用*tf.cond(x, ...)*, 或者*if x is None*
+ ==, !=不能被重载, 代替地，我们使用*tf.equal*, *tf.not\_equal*

### 循环控制
经常出现在RNN构造计算中

+ tf.cond
+ tf.where
+ tf.while_loop

例：记录当前数值的Fibonacci数列

```python
n = tf.constant(5)

c = tf.TensorArray(tf.int32, n)
c = c.write(0, 1)
c = c.write(1, 1)

def cond(i, a, b, c):
    return i < n

def body(i, a, b, c):
    c = c.write(i, a + b)
    return i + 1, b, a + b, c

i, a, b, c = tf.while_loop(cond, body, (2, 1, 1, c))

c = c.stack()

print(tf.Session().run(c))
```

### 数值稳定性

浮点数最大／最小值

```python
print(np.nextafter(np.float32(0), np.float32(1))) # prints 1.4013e-45
print(np.finfo(np.float32).max) # prints 3.40282e+38
```

ln(3.40282e+38)=88.7,所以任何超出这个数字的值都将导致结果`NAN`

`softmax`

```python
import tensorflow as tf

def unstable_softmax(logits):
    exp = tf.exp(logits)
    return exp / tf.reduce_sum(exp)

tf.Session().run(unstable_softmax([1000., 0.]))  # prints [ nan, 0.]
```

`cross entropy`

```python
def unstable_softmax_cross_entropy(labels, logits):
    logits = tf.log(softmax(logits))
    return -tf.reduce_sum(labels * logits)

labels = tf.constant([0.5, 0.5])
logits = tf.constant([1000., 0.])

xe = unstable_softmax_cross_entropy(labels, logits)

print(tf.Session().run(xe))  # prints inf
```

稳定版本

```python
import tensorflow as tf

def softmax(logits):
    exp = tf.exp(logits - tf.reduce_max(logits))
    return exp / tf.reduce_sum(exp)

tf.Session().run(softmax([1000., 0.]))  # prints [ 1., 0.]
```

```python
def softmax_cross_entropy(labels, logits):
    scaled_logits = logits - tf.reduce_max(logits)
    normalized_logits = scaled_logits - tf.reduce_logsumexp(scaled_logits)
    return -tf.reduce_sum(labels * normalized_logits)

labels = tf.constant([0.5, 0.5])
logits = tf.constant([1000., 0.])

xe = softmax_cross_entropy(labels, logits)

print(tf.Session().run(xe))  # prints 500.0
```

### IPython交互式环境

```python
import tensorflow as tf
sess = tf.InteractiveSession()  #代替tf.Session()

x = tf.Variable([1.0, 2.0])
a = tf.constant([3.0, 3.0])

# 使用初始化器 initializer op 的 run() 方法初始化 'x' 
x.initializer.run()

# 增加一个减法 sub op, 从 'x' 减去 'a'. 运行减法 op, 输出结果 
sub = tf.sub(x, a)
print sub.eval()  #使用Operation.run和Tensor.eval代替sess.run
# ==> [-2. -1.]
```

## 熟悉编程环境
下面的程序均在python 3.5中测试通过
### Hello World
其实，在深度学习方向，一般将MNIST手写字符识别作为该领域的<u>Hello World</u>应用的。

```python
import tensorflow as tf
hello_byte = tf.constant("Hello, TensorFlow!")
sess = tf.Session()
hello_str = sess.run(hello_byte).decode()
print(hello_str)
```

输出：

Hello, TensorFlow!

### 数学运算

```python
import tensorflow as tf
a = tf.constant(2)
b = tf.constant(3)
with tf.Session() as sess:
    print("a=2, b=3")
    print("Addition with constants: %i" % sess.run(a+b))
    print("Multiplication with constants: %i" % sess.run(a*b))
```

输出：

a=2, b=3

Addition with constants: 5

Multiplication with constants: 6

### placeholder占位符

```python
import tensorflow as tf
a = tf.placeholder(tf.int16)
b = tf.placeholder(tf.int16)
add = tf.add(a, b)
mul = tf.multiply(a, b)
with tf.Session() as sess:
    # Run every operation with variable input
    print("Addition with variables: %i" % sess.run(add, feed_dict={a: 2, b: 3}))
    print("Multiplication with variables: %i" % sess.run(mul, feed_dict={a: 2, b: 3}))
matrix1 = tf.constant([[3., 3.]])
matrix2 = tf.constant([[2.],[2.]])
product=tf.matmul(matrix1,matrix2)
with tf.Session() as sess:
    result = sess.run(product)
    print(result)
```

输出：

Addition with variables: 5

Multiplication with variables: 6

[[ 12.]]

### 函数近似

$$y = 5 x^2 + 3$$

```python
import numpy as np
import tensorflow as tf

# Placeholders are used to feed values from python to TensorFlow ops. We define
# two placeholders, one for input feature x, and one for output y.
x = tf.placeholder(tf.float32)
y = tf.placeholder(tf.float32)

# Assuming we know that the desired function is a polynomial of 2nd degree, we
# allocate a vector of size 3 to hold the coefficients. The variable will be
# automatically initialized with random noise.
w = tf.get_variable("w", shape=[3, 1])

# We define yhat to be our estimate of y.
f = tf.stack([tf.square(x), x, tf.ones_like(x)], 1)
yhat = tf.squeeze(tf.matmul(f, w), 1)

# The loss is defined to be the l2 distance between our estimate of y and its
# true value. We also added a shrinkage term, to ensure the resulting weights
# would be small.
loss = tf.nn.l2_loss(yhat - y) + 0.1 * tf.nn.l2_loss(w)

# We use the Adam optimizer with learning rate set to 0.1 to minimize the loss.
train_op = tf.train.AdamOptimizer(0.1).minimize(loss)

def generate_data():
    x_val = np.random.uniform(-10.0, 10.0, size=100)
    y_val = 5 * np.square(x_val) + 3
    return x_val, y_val

sess = tf.Session()
# Since we are using variables we first need to initialize them.
sess.run(tf.global_variables_initializer())
for _ in range(1000):
    x_val, y_val = generate_data()
    _, loss_val = sess.run([train_op, loss], {x: x_val, y: y_val})
    print(loss_val)
print(sess.run([w]))
```

输出：

array([[  4.98141575e+00],
       [  4.86645894e-03],
       [  4.09156847e+00]]

### 线性回归

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
rng = np.random

# Parameters
learning_rate = 0.01
training_epochs = 2000
display_step = 200

# Training Data
train_X = np.asarray([3.3,4.4,5.5,6.71,6.93,4.168,9.779,6.182,7.59,2.167,7.042,10.791,5.313,7.997,5.654,9.27,3.1])
train_Y = np.asarray([1.7,2.76,2.09,3.19,1.694,1.573,3.366,2.596,2.53,1.221,2.827,3.465,1.65,2.904,2.42,2.94,1.3])
n_samples = train_X.shape[0]

# tf Graph Input
X = tf.placeholder("float")
Y = tf.placeholder("float")

# Create Model

# Set model weights
W = tf.Variable(rng.randn(), name="weight")
b = tf.Variable(rng.randn(), name="bias")

# Construct a linear model
activation = tf.add(tf.multiply(X, W), b)

# Minimize the squared errors
cost = tf.reduce_sum(tf.pow(activation-Y, 2))/(2*n_samples) #L2 loss
optimizer = tf.train.GradientDescentOptimizer(learning_rate).minimize(cost) #Gradient descent

# Initializing the variables
init = tf.global_variables_initializer()

# Launch the graph
with tf.Session() as sess:
    sess.run(init)

    # Fit all training data
    for epoch in range(training_epochs):
        for (x, y) in zip(train_X, train_Y):
            sess.run(optimizer, feed_dict={X: x, Y: y})

        #Display logs per epoch step
        if epoch % display_step == 0:
            print("Epoch:", '%04d' % (epoch+1), "cost=", \
                "{:.9f}".format(sess.run(cost, feed_dict={X: train_X, Y:train_Y})), \
                "W=", sess.run(W), "b=", sess.run(b))

    print("Optimization Finished!")
    print("cost=", sess.run(cost, feed_dict={X: train_X, Y: train_Y}), \
          "W=", sess.run(W), "b=", sess.run(b))

    #Graphic display
    plt.plot(train_X, train_Y, 'ro', label='Original data')
    plt.plot(train_X, sess.run(W) * train_X + sess.run(b), label='Fitted line')
    plt.legend()
    plt.show()
```

输出：

Epoch: 0001 cost= 1.389398336 W= 0.0237372 b= 0.688595

Epoch: 0201 cost= 0.077215351 W= 0.258199 b= 0.739563

Epoch: 0401 cost= 0.077126071 W= 0.256327 b= 0.75303

Epoch: 0601 cost= 0.077071890 W= 0.254862 b= 0.763568

Epoch: 0801 cost= 0.077039108 W= 0.253715 b= 0.771816

Epoch: 1001 cost= 0.077019304 W= 0.252818 b= 0.77827

Epoch: 1201 cost= 0.077007398 W= 0.252116 b= 0.783319

Epoch: 1401 cost= 0.077000320 W= 0.251567 b= 0.787267

Epoch: 1601 cost= 0.076996110 W= 0.251139 b= 0.790352

Epoch: 1801 cost= 0.076993659 W= 0.250803 b= 0.792765

Optimization Finished!

cost= 0.0769922 W= 0.250542 b= 0.794643

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/tf_lr.jpg)

### 逻辑回归

```python
import tensorflow as tf
# Import MINST data
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("/tmp/data/", one_hot=True)

# Parameters
learning_rate = 0.01
training_epochs = 50
batch_size = 100
display_step = 10

# tf Graph Input
x = tf.placeholder(tf.float32, [None, 784]) # mnist data image of shape 28*28=784
y = tf.placeholder(tf.float32, [None, 10]) # 0-9 digits recognition => 10 classes

# Set model weights
W = tf.Variable(tf.zeros([784, 10]))
b = tf.Variable(tf.zeros([10]))

# Construct model
pred = tf.nn.softmax(tf.add(tf.matmul(x, W), b)) # Softmax

# Minimize error using cross entropy
cost = tf.reduce_mean(-tf.reduce_sum(y * tf.log(pred), reduction_indices=1))
# Gradient Descent
optimizer = tf.train.GradientDescentOptimizer(learning_rate).minimize(cost)

# Initializing the variables
init = tf.global_variables_initializer()

# Launch the graph
with tf.Session() as sess:
    sess.run(init)

    # Training cycle
    for epoch in range(training_epochs):
        avg_cost = 0.
        total_batch = int(mnist.train.num_examples/batch_size)
        # Loop over all batches
        for i in range(total_batch):
            batch_xs, batch_ys = mnist.train.next_batch(batch_size)
            # Run optimization op (backprop) and cost op (to get loss value)
            _, c = sess.run([optimizer, cost], feed_dict={x: batch_xs,
                                                          y: batch_ys})
            # Compute average loss
            avg_cost += c / total_batch
        # Display logs per epoch step
        if (epoch+1) % display_step == 0:
            print("Epoch:", '%04d' % (epoch+1), "cost=", "{:.9f}".format(avg_cost))

    print("Optimization Finished!")

    # Test model
    correct_prediction = tf.equal(tf.argmax(pred, 1), tf.argmax(y, 1))
    # Calculate accuracy
    accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))
    print("Accuracy:", accuracy.eval({x: mnist.test.images, y: mnist.test.labels}))
```

输出：

Epoch: 0010 cost= 0.392357300

Epoch: 0020 cost= 0.345426296

Epoch: 0030 cost= 0.325015054

Epoch: 0040 cost= 0.312834605

Epoch: 0050 cost= 0.304482930

Optimization Finished!

Accuracy: 0.9191


## 常见框架

### 前馈神经网络(FeedForward Neural Network, FNN)

```python
def neural_network(data):
	# 定义第一层"神经元"的权重和biases
	layer_1_w_b = {'w_':tf.Variable(tf.random_normal([n_input_layer, n_layer_1])), 'b_':tf.Variable(tf.random_normal([n_layer_1]))}
	# 定义第二层"神经元"的权重和biases
	layer_2_w_b = {'w_':tf.Variable(tf.random_normal([n_layer_1, n_layer_2])), 'b_':tf.Variable(tf.random_normal([n_layer_2]))}
	# 定义输出层"神经元"的权重和biases
	layer_output_w_b = {'w_':tf.Variable(tf.random_normal([n_layer_2, n_output_layer])), 'b_':tf.Variable(tf.random_normal([n_output_layer]))}
 
	# w·x+b
	layer_1 = tf.add(tf.matmul(data, layer_1_w_b['w_']), layer_1_w_b['b_'])
	layer_1 = tf.nn.relu(layer_1)  # 激活函数
	layer_2 = tf.add(tf.matmul(layer_1, layer_2_w_b['w_']), layer_2_w_b['b_'])
	layer_2 = tf.nn.relu(layer_2 ) # 激活函数
	layer_output = tf.add(tf.matmul(layer_2, layer_output_w_b['w_']), layer_output_w_b['b_'])
 
	return layer_output
 
# 每次使用50条数据进行训练
batch_size = 50
 
X = tf.placeholder('float', [None, len(train_dataset[0][0])]) 
#[None, len(train_x)]代表数据数据的高和宽（矩阵），好处是如果数据不符合宽高，tensorflow会报错，不指定也可以。
Y = tf.placeholder('float')
# 使用数据训练神经网络
def train_neural_network(X, Y):
	predict = neural_network(X)
	cost_func = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(predict, Y))
	optimizer = tf.train.AdamOptimizer().minimize(cost_func)  # learning rate 默认 0.001 
 
	epochs = 13
	with tf.Session() as session:
		session.run(tf.initialize_all_variables())
		epoch_loss = 0
 
		i = 0
		random.shuffle(train_dataset)
		train_x = dataset[:, 0]
		train_y = dataset[:, 1]
		for epoch in range(epochs):
			while i < len(train_x):
				start = i
				end = i + batch_size
 
				batch_x = train_x[start:end]
				batch_y = train_y[start:end]
 
				_, c = session.run([optimizer, cost_func], feed_dict={X:list(batch_x),Y:list(batch_y)})
				epoch_loss += c
				i += batch_size
 
			print(epoch, ' : ', epoch_loss)
 
		text_x = test_dataset[: ,0]
		text_y = test_dataset[:, 1]
		correct = tf.equal(tf.argmax(predict,1), tf.argmax(Y,1))
		accuracy = tf.reduce_mean(tf.cast(correct,'float'))
		print('准确率: ', accuracy.eval({X:list(text_x) , Y:list(text_y)})) 
```

### 卷积神经网络(Convolutional Neural Network, CNN)
常用于图像识别、语音分析等领域

```python
import tensorflow as tf
import numpy as np
 
# 下载mnist数据集
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets('/tmp/', one_hot=True)
 
 
n_output_layer = 10
 
# 定义待训练的神经网络
def convolutional_neural_network(data):
    weights = {'w_conv1':tf.Variable(tf.random_normal([5,5,1,32])),
              'w_conv2':tf.Variable(tf.random_normal([5,5,32,64])),
              'w_fc':tf.Variable(tf.random_normal([7*7*64,1024])),
              'out':tf.Variable(tf.random_normal([1024,n_output_layer]))}
 
    biases = {'b_conv1':tf.Variable(tf.random_normal([32])),
              'b_conv2':tf.Variable(tf.random_normal([64])),
              'b_fc':tf.Variable(tf.random_normal([1024])),
              'out':tf.Variable(tf.random_normal([n_output_layer]))}
 
    data = tf.reshape(data, [-1,28,28,1]) #第2，第3维对应图片的宽、高，最后一维代表图片的颜色通道数：灰度图为1，RGB彩色图为3
 
    conv1 = tf.nn.relu(tf.add(tf.nn.conv2d(data, weights['w_conv1'], strides=[1,1,1,1], padding='SAME'), biases['b_conv1']))
    conv1 = tf.nn.max_pool(conv1, ksize=[1,2,2,1], strides=[1,2,2,1], padding='SAME')
 
    conv2 = tf.nn.relu(tf.add(tf.nn.conv2d(conv1, weights['w_conv2'], strides=[1,1,1,1], padding='SAME'), biases['b_conv2']))
    conv2 = tf.nn.max_pool(conv2, ksize=[1,2,2,1], strides=[1,2,2,1], padding='SAME')
 
    fc = tf.reshape(conv2, [-1,7*7*64])
    fc = tf.nn.relu(tf.add(tf.matmul(fc, weights['w_fc']), biases['b_fc']))
 
    # dropout剔除一些"神经元"
    #fc = tf.nn.dropout(fc, 0.8)
 
    output = tf.add(tf.matmul(fc, weights['out']), biases['out'])
    return output
 
 
# 每次使用100条数据进行训练
batch_size = 100
 
X = tf.placeholder('float', [None, 28*28]) 
Y = tf.placeholder('float')
# 使用数据训练神经网络
def train_neural_network(X, Y):
    predict = convolutional_neural_network(X)
    cost_func = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=predict, labels=Y))
    optimizer = tf.train.AdamOptimizer().minimize(cost_func)  # learning rate 默认 0.001 
 
    epochs = 100
    with tf.Session() as session:
        session.run(tf.global_variables_initializer())
        epoch_loss = 0
        for epoch in range(epochs):
            for i in range( int(mnist.train.num_examples/batch_size) ):
                x, y = mnist.train.next_batch(batch_size)
                _, c = session.run([optimizer, cost_func], feed_dict={X:x,Y:y})
                epoch_loss += c
            print(epoch, ' : ', epoch_loss)
 
        correct = tf.equal(tf.argmax(predict,1), tf.argmax(Y,1))
        accuracy = tf.reduce_mean(tf.cast(correct,'float'))
        print('准确率: ', accuracy.eval({X:mnist.test.images, Y:mnist.test.labels}))
 
train_neural_network(X,Y)
```

### 循环神经网络(Recurrent Neural Network, RNN)

```python
import tensorflow as tf
import numpy as np
 
# 下载mnist数据集
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets('/tmp/', one_hot=True)
 
 
#一张图片是28*28,FNN是一次性把数据输入到网络，RNN把它分成块
chunk_size = 28
chunk_n = 28
 
rnn_size = 256
 
n_output_layer = 10   # 输出层
 
X = tf.placeholder('float', [None, chunk_n, chunk_size]) 
Y = tf.placeholder('float')
# 定义待训练的神经网络
def recurrent_neural_network(data):
    layer = {'w_':tf.Variable(tf.random_normal([rnn_size, n_output_layer])), 'b_':tf.Variable(tf.random_normal([n_output_layer]))}
 
    lstm_cell = tf.nn.rnn_cell.BasicLSTMCell(rnn_size)
 
    data = tf.transpose(data, [1,0,2])
    data = tf.reshape(data, [-1, chunk_size])
    data = tf.split(0, chunk_n, data)
    outputs, status = tf.nn.rnn(lstm_cell, data, dtype=tf.float32)
 
    ouput = tf.add(tf.matmul(outputs[-1], layer['w_']), layer['b_'])
 
    return ouput
 
# 每次使用100条数据进行训练
batch_size = 100
 
# 使用数据训练神经网络
def train_neural_network(X, Y):
    predict = recurrent_neural_network(X)
    cost_func = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=predict, labels=Y))
    optimizer = tf.train.AdamOptimizer().minimize(cost_func)
 
    epochs = 13
    with tf.Session() as session:
        session.run(tf.global_variables_initializer())
        epoch_loss = 0
        for epoch in range(epochs):
            for i in range( int(mnist.train.num_examples/batch_size) ):
                x, y = mnist.train.next_batch(batch_size)
                x = x.reshape([batch_size, chunk_n, chunk_size])
                _, c = session.run([optimizer, cost_func], feed_dict={X:x,Y:y})
                epoch_loss += c
            print(epoch, ' : ', epoch_loss)
 
        correct = tf.equal(tf.argmax(predict,1), tf.argmax(Y,1))
        accuracy = tf.reduce_mean(tf.cast(correct,'float'))
        print('准确率: ', accuracy.eval({X:mnist.test.images.reshape(-1, chunk_n, chunk_size), Y:mnist.test.labels}))
 
train_neural_network(X,Y)
```

## 模型

### LeNet

### GoogleNet

### AlexNet

### ResNet

## 重要函数

### KL散度

```python
def gaussian_kl(q, p=(0., 0.)):
  """Computes KL divergence between two isotropic Gaussian distributions.

  To ensure numerical stability, this op uses mu, log(sigma^2) to represent
  the distribution. If q is not provided, it's assumed to be unit Gaussian.

  Args:
    q: A tuple (mu, log(sigma^2)) representing a multi-variatie Gaussian.
    p: A tuple (mu, log(sigma^2)) representing a multi-variatie Gaussian.
  Returns:
    A tensor representing KL(q, p).
  """
  mu1, log_sigma1_sq = q
  mu2, log_sigma2_sq = p
  return tf.reduce_sum(
    0.5 * (log_sigma2_sq - log_sigma1_sq +
           tf.exp(log_sigma1_sq - log_sigma2_sq) +
           tf.square(mu1 - mu2) / tf.exp(log_sigma2_sq) -
           1), axis=-1)
```

与Radon-Nikodym定理之间的关联：如果µ和ν是X上的测度，并且µ<<ν，那么从µ到ν的Kullback-Leibler散度可以定义成

$$D_{KL}(\mu||\nu) = \int_X \log(\frac{d\mu}{d\nu})d\mu$$

### Leaky ReLU

```python
def leaky_relu(tensor, alpha=0.1):
    """Computes the leaky rectified linear activation."""
    return tf.maximum(tensor, alpha * tensor)
```

## 应用

### 手写字符识别

#### 数据集
+ [中文字符集](http://www.nlpr.ia.ac.cn/CN/folder/folder8.shtml)

```shell
wget http://www.nlpr.ia.ac.cn/databases/download/feature_data/HWDB1.1trn_gnt.zip
wget http://www.nlpr.ia.ac.cn/databases/download/feature_data/HWDB1.1tst_gnt.zip
```

+ MNIST图像集

#### 预处理

```python
import os
import numpy as np
import struct
from PIL import Image


data_dir = '../data'
train_data_dir = os.path.join(data_dir, 'HWDB1.1trn_gnt')
test_data_dir = os.path.join(data_dir, 'HWDB1.1tst_gnt')


def read_from_gnt_dir(gnt_dir=train_data_dir):
    def one_file(f):
        header_size = 10
        while True:
            header = np.fromfile(f, dtype='uint8', count=header_size)
            if not header.size: break
            sample_size = header[0] + (header[1]<<8) + (header[2]<<16) + (header[3]<<24)
            tagcode = header[5] + (header[4]<<8)
            width = header[6] + (header[7]<<8)
            height = header[8] + (header[9]<<8)
            if header_size + width*height != sample_size:
                break
            image = np.fromfile(f, dtype='uint8', count=width*height).reshape((height, width))
            yield image, tagcode
    for file_name in os.listdir(gnt_dir):
        if file_name.endswith('.gnt'):
            file_path = os.path.join(gnt_dir, file_name)
            with open(file_path, 'rb') as f:
                for image, tagcode in one_file(f):
                    yield image, tagcode
char_set = set()
for _, tagcode in read_from_gnt_dir(gnt_dir=train_data_dir):
    tagcode_unicode = struct.pack('>H', tagcode).decode('gb2312')
    char_set.add(tagcode_unicode)
char_list = list(char_set)
char_dict = dict(zip(sorted(char_list), range(len(char_list))))
print(len(char_dict))
import pickle
f = open('char_dict', 'wb')
pickle.dump(char_dict, f)
f.close()
train_counter = 0
test_counter = 0
for image, tagcode in read_from_gnt_dir(gnt_dir=train_data_dir):
    tagcode_unicode = struct.pack('>H', tagcode).decode('gb2312')
    im = Image.fromarray(image)
    dir_name = '../data/train/' + '%0.5d'%char_dict[tagcode_unicode]
    if not os.path.exists(dir_name):
        os.mkdir(dir_name)
    im.convert('RGB').save(dir_name+'/' + str(train_counter) + '.png')
    train_counter += 1
for image, tagcode in read_from_gnt_dir(gnt_dir=test_data_dir):
    tagcode_unicode = struct.pack('>H', tagcode).decode('gb2312')
    im = Image.fromarray(image)
    dir_name = '../data/test/' + '%0.5d'%char_dict[tagcode_unicode]
    if not os.path.exists(dir_name):
        os.mkdir(dir_name)
    im.convert('RGB').save(dir_name+'/' + str(test_counter) + '.png')
    test_counter += 1
```

#### 读取数据

```python
def batch_data(file_labels,sess, batch_size=128):
    image_list = [file_label[0] for file_label in file_labels]
    label_list = [int(file_label[1]) for file_label in file_labels]
    print('tag2 {0}'.format(len(image_list)))
    images_tensor = tf.convert_to_tensor(image_list, dtype=tf.string)
    labels_tensor = tf.convert_to_tensor(label_list, dtype=tf.int64)
    input_queue = tf.train.slice_input_producer([images_tensor, labels_tensor])

    labels = input_queue[1]
    images_content = tf.read_file(input_queue[0])
    # images = tf.image.decode_png(images_content, channels=1)
    images = tf.image.convert_image_dtype(tf.image.decode_png(images_content, channels=1), tf.float32)
    # images = images / 256
    images =  pre_process(images)
    # print(images.get_shape())
    # one hot
    labels = tf.one_hot(labels, 3755)
    image_batch, label_batch = tf.train.shuffle_batch([images, labels], batch_size=batch_size, capacity=50000,min_after_dequeue=10000)
    # print('image_batch', image_batch.get_shape())

    coord = tf.train.Coordinator()
    threads = tf.train.start_queue_runners(sess=sess, coord=coord)
    return image_batch, label_batch, coord, threads
```

#### 数据增强：图像翻转、改变亮度等基本操作

```python
def pre_process(images):
    if FLAGS.random_flip_up_down:
        images = tf.image.random_flip_up_down(images)
    if FLAGS.random_flip_left_right:
        images = tf.image.random_flip_left_right(images)
    if FLAGS.random_brightness:
        images = tf.image.random_brightness(images, max_delta=0.3)
    if FLAGS.random_contrast:
        images = tf.image.random_contrast(images, 0.8, 1.2)
    new_size = tf.constant([FLAGS.image_size,FLAGS.image_size], dtype=tf.int32)
    images = tf.image.resize_images(images, new_size)
    return images
```

#### 网络构建：两个卷积层+一个全连接层

```python
def network(images, labels=None):
    endpoints = {}
    conv_1 = slim.conv2d(images, 32, [3,3],1, padding='SAME')
    max_pool_1 = slim.max_pool2d(conv_1, [2,2],[2,2], padding='SAME')
    conv_2 = slim.conv2d(max_pool_1, 64, [3,3],padding='SAME')
    max_pool_2 = slim.max_pool2d(conv_2, [2,2],[2,2], padding='SAME')
    flatten = slim.flatten(max_pool_2)
    out = slim.fully_connected(flatten,3755, activation_fn=None)
    global_step = tf.Variable(initial_value=0)
    if labels is not None:
        loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(out, labels))
        train_op = tf.train.AdamOptimizer(learning_rate=0.0001).minimize(loss, global_step=global_step)
        accuracy = tf.reduce_mean(tf.cast(tf.equal(tf.argmax(out, 1), tf.argmax(labels, 1)), tf.float32))
        tf.summary.scalar('loss', loss)
        tf.summary.scalar('accuracy', accuracy)
        merged_summary_op = tf.summary.merge_all()
    output_score = tf.nn.softmax(out)
    predict_val_top3, predict_index_top3 = tf.nn.top_k(output_score, k=3)

    endpoints['global_step'] = global_step
    if labels is not None:
        endpoints['labels'] = labels
        endpoints['train_op'] = train_op
        endpoints['loss'] = loss
        endpoints['accuracy'] = accuracy
        endpoints['merged_summary_op'] = merged_summary_op
    endpoints['output_score'] = output_score
    endpoints['predict_val_top3'] = predict_val_top3
    endpoints['predict_index_top3'] = predict_index_top3
    return endpoints
```

#### 训练

```python
def train():
    sess = tf.Session()
    file_labels = get_imagesfile(FLAGS.train_data_dir)
    images, labels, coord, threads = batch_data(file_labels, sess)
    endpoints = network(images, labels)
    saver = tf.train.Saver()
    sess.run(tf.global_variables_initializer())
    train_writer = tf.train.SummaryWriter('./log' + '/train',sess.graph)
    test_writer = tf.train.SummaryWriter('./log' + '/val')
    start_step = 0
    if FLAGS.restore:
        ckpt = tf.train.latest_checkpoint(FLAGS.checkpoint_dir)
        if ckpt:
            saver.restore(sess, ckpt)
            print("restore from the checkpoint {0}".format(ckpt))
            start_step += int(ckpt.split('-')[-1])
    logger.info(':::Training Start:::')
    try:
        while not coord.should_stop():
        # logger.info('step {0} start'.format(i))
            start_time = time.time()
            _, loss_val, train_summary, step = sess.run([endpoints['train_op'], endpoints['loss'], endpoints['merged_summary_op'], endpoints['global_step']])
            train_writer.add_summary(train_summary, step)
            end_time = time.time()
            logger.info("the step {0} takes {1} loss {2}".format(step, end_time-start_time, loss_val))
            if step > FLAGS.max_steps:
                break
            # logger.info("the step {0} takes {1} loss {2}".format(i, end_time-start_time, loss_val))
            if step % FLAGS.eval_steps == 1:
                accuracy_val,test_summary, step = sess.run([endpoints['accuracy'], endpoints['merged_summary_op'], endpoints['global_step']])
                test_writer.add_summary(test_summary, step)
                logger.info('===============Eval a batch in Train data=======================')
                logger.info( 'the step {0} accuracy {1}'.format(step, accuracy_val))
                logger.info('===============Eval a batch in Train data=======================')
            if step % FLAGS.save_steps == 1:
                logger.info('Save the ckpt of {0}'.format(step))
                saver.save(sess, os.path.join(FLAGS.checkpoint_dir, 'my-model'), global_step=endpoints['global_step'])
    except tf.errors.OutOfRangeError:
        # print "============train finished========="
        logger.info('==================Train Finished================')
        saver.save(sess, os.path.join(FLAGS.checkpoint_dir, 'my-model'), global_step=endpoints['global_step'])
    finally:
        coord.request_stop()
    coord.join(threads)
    sess.close()
```

#### 验证

```python
def validation():
    # it should be fixed by using placeholder with epoch num in train stage
    sess = tf.Session()

    file_labels = get_imagesfile(FLAGS.test_data_dir)
    test_size = len(file_labels)
    print(test_size)
    val_batch_size = FLAGS.val_batch_size
    test_steps = test_size / val_batch_size
    print(test_steps)
    # images, labels, coord, threads= batch_data(file_labels, sess)
    images = tf.placeholder(dtype=tf.float32, shape=[None, 64, 64, 1])
    labels = tf.placeholder(dtype=tf.int32, shape=[None,3755])
    # read batch images from file_labels
    # images_batch = np.zeros([128,64,64,1])
    # labels_batch = np.zeros([128,3755])
    # labels_batch[0][20] = 1
    #
    endpoints = network(images, labels)
    saver = tf.train.Saver()
    ckpt = tf.train.latest_checkpoint(FLAGS.checkpoint_dir)
    if ckpt:
        saver.restore(sess, ckpt)
        # logger.info("restore from the checkpoint {0}".format(ckpt))
    # logger.info('Start validation')
    final_predict_val = []
    final_predict_index = []
    groundtruth = []
    for i in range(test_steps):
        start = i* val_batch_size
        end = (i+1)*val_batch_size
        images_batch = []
        labels_batch = []
        labels_max_batch = []
        logger.info('=======start validation on {0}/{1} batch========='.format(i, test_steps))
        for j in range(start,end):
            image_path = file_labels[j][0]
            temp_image = Image.open(image_path).convert('L')
            temp_image = temp_image.resize((FLAGS.image_size, FLAGS.image_size),Image.ANTIALIAS)
            temp_label = np.zeros([3755])
            label = int(file_labels[j][1])
            # print(label)
            temp_label[label] = 1
            # print("====",np.asarray(temp_image).shape)
            labels_batch.append(temp_label)
            # print("====",np.asarray(temp_image).shape)
            images_batch.append(np.asarray(temp_image)/255.0)
            labels_max_batch.append(label)
        # print(images_batch)
        images_batch = np.array(images_batch).reshape([-1, 64, 64, 1])
        labels_batch = np.array(labels_batch)
        batch_predict_val, batch_predict_index = sess.run([endpoints['predict_val_top3'],
                        endpoints['predict_index_top3']], feed_dict={images:images_batch, labels:labels_batch})
        logger.info('=======validation on {0}/{1} batch end========='.format(i, test_steps))
        final_predict_val += batch_predict_val.tolist()
        final_predict_index += batch_predict_index.tolist()
        groundtruth += labels_max_batch
    sess.close()
    return final_predict_val, final_predict_index, groundtruth
```

#### 推理

```python
def inference(image):
    temp_image = Image.open(image).convert('L')
    temp_image = temp_image.resize((FLAGS.image_size, FLAGS.image_size),Image.ANTIALIAS)
    sess = tf.Session()
    logger.info('========start inference============')
    images = tf.placeholder(dtype=tf.float32, shape=[None, 64, 64, 1])
    endpoints = network(images)
    saver = tf.train.Saver()
    ckpt = tf.train.latest_checkpoint(FLAGS.checkpoint_dir)
    if ckpt:
        saver.restore(sess, ckpt)
    predict_val, predict_index = sess.run([endpoints['predict_val_top3'],endpoints['predict_index_top3']], feed_dict={images:temp_image})
    sess.close()
    return final_predict_val, final_predict_index
```

### Inception
Inception是图像识别领域当前最好的卷积神经网络。这个系统将224x224像素图像分类到1000个标签(如cheetah猎豹、garbage truck垃圾货车等)上。这样的模型由1.36千万个学习参数和TensorFlow计算图中的3.6万个操作组成。在单张图像上运行推理需要20亿个乘-加操作。

### 图片标题

### 运动检测
