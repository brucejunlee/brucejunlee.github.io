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

Google [TensorFlow](www.tensorflow.org)是表示机器学习算法的接口，并且是执行这些算法的实现平台。使用TensorFlow表示的计算可以在多种多样的系统中几乎无修改地执行。这些系统包括从手机、平板电脑等移动设备到数以百计的机器和数以千计的**GPU**等计算设备组成的大规模分布式系统。这样的系统非常灵活，可以被用来表示大量算法，包括深度神经网络模型的训练和推理。它也被运用到研究中，以及将机器学习系统部署到横跨数十个计算机科学和其它领域的生产中，包括语音识别，计算机视觉，机器人学，信息检索，自然语言处理，地理信息抽取和计算药物发现等。

## 熟悉编程环境
下面的程序均在python 3.5中测试通过
### Hello World

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

![image](https://github.com/brucejunlee/brucejunlee.github.io/blob/master/assets/img/tf_lr.jpg)

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

## 应用
### Inception
Inception是图像识别领域当前最好的卷积神经网络。这个系统将224x224像素图像分类到1000个标签(如cheetah猎豹、garbage truck垃圾货车等)上。这样的模型由1.36千万个学习参数和TensorFlow计算图中的3.6万个操作组成。在单张图像上运行推理需要20亿个乘-加操作。

### 图片标题

### 运动检测
