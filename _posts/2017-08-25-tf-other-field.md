---
layout: post
title: "TensorFlow：在其它学科中的应用"
author: "李军"
categories: journal
tags: [tensorflow, mathematics, PDE]
image:
  feature: tf.jpg
  teaser: tf-teaser.jpg
  credit: 
  creditlink: ""
---

本教程与机器学习几乎没有任何关系，但这对于将TensorFlow运用于机器学习以外更广泛的领域是很好、很有趣的。

下面代码在Python2.7环境下测试通过，Python3.5环境下没有cStringIO库，如果想在Python3.5环境下运行，请如下操作

```python
import io

ios = io.StringIO()
```

## Mandelbrot集可视化

导入库

```python
# 导入仿真库
import tensorflow as tf
import numpy as np

# 导入可视化库
import PIL.Image
from cStringIO import StringIO
from IPython.display import clear_output, Image, display
import scipy.ndimage as nd
```

迭代图像显示的定义

```python
def DisplayFractal(a, fmt='jpeg'):
  """显示迭代计算出的彩色分形图像。"""
  a_cyclic = (6.28*a/20.0).reshape(list(a.shape)+[1])
  img = np.concatenate([10+20*np.cos(a_cyclic),
                        30+50*np.sin(a_cyclic),
                        155-80*np.cos(a_cyclic)], 2)
  img[a==a.max()] = 0
  a = img
  a = np.uint8(np.clip(a, 0, 255))
  f = StringIO()
  PIL.Image.fromarray(a).save(f, fmt)
  display(Image(data=f.getvalue()))
```

变量设置

```python
sess = tf.InteractiveSession()

# 使用NumPy创建一个在[-2,2]x[-2,2]范围内的2维复数数组
Y, X = np.mgrid[-1.3:1.3:0.005, -2:1:0.005]
Z = X+1j*Y

xs = tf.constant(Z.astype("complex64"))
zs = tf.Variable(xs)
ns = tf.Variable(tf.zeros_like(xs, "float32"))

init = tf.global_variables_initializer()
sess.run(init)
```

运算

```python
# 计算一个新值z: z^2 + x
zs_ = zs*zs + xs

# 这个新值会发散吗？
not_diverged = tf.complex_abs(zs_) < 4

# 更新zs并且迭代计算。
#
# 说明：在这些值发散之后，我们仍然在计算zs，这个计算消耗特别大！
#      如果稍微简单点，这里有更好的方法来处理。
#
step = tf.group(
  zs.assign(zs_),
  ns.assign_add(tf.cast(not_diverged, "float32"))
  )
  
for i in range(200): step.run()

DisplayFractal(ns.eval())
```

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/mandelbrot.jpg)

## 偏微分方程
仿真几滴落入一块方形水池的雨点

导入库

```python
#导入模拟仿真需要的库
import tensorflow as tf
import numpy as np

#导入可视化需要的库
import PIL.Image
from cStringIO import StringIO
from IPython.display import clear_output, Image, display
```

池塘表面状态的定义

```python
def DisplayArray(a, fmt='jpeg', rng=[0,1]):
  """Display an array as a picture."""
  a = (a - rng[0])/float(rng[1] - rng[0])*255
  a = np.uint8(np.clip(a, 0, 255))
  f = StringIO()
  PIL.Image.fromarray(a).save(f, fmt)
  display(Image(data=f.getvalue()))
```

会话

```python
sess = tf.InteractiveSession()
```

函数

```python
def make_kernel(a):
  """Transform a 2D array into a convolution kernel"""
  a = np.asarray(a)
  a = a.reshape(list(a.shape) + [1,1])
  return tf.constant(a, dtype=1)

def simple_conv(x, k):
  """A simplified 2D convolution operation"""
  x = tf.expand_dims(tf.expand_dims(x, 0), -1)
  y = tf.nn.depthwise_conv2d(x, k, [1, 1, 1, 1], padding='SAME')
  return y[0, :, :, 0]

def laplace(x):
  """Compute the 2D laplacian of an array"""
  laplace_k = make_kernel([[0.5, 1.0, 0.5],
                           [1.0, -6., 1.0],
                           [0.5, 1.0, 0.5]])
  return simple_conv(x, laplace_k)
```

PDE定义

```python
N = 500  #方形池塘的边长

# Initial Conditions -- some rain drops hit a pond

# Set everything to zero
u_init = np.zeros([N, N], dtype="float32")
ut_init = np.zeros([N, N], dtype="float32")

# Some rain drops hit a pond at random points
for n in range(40):
  a,b = np.random.randint(0, N, 2)
  u_init[a,b] = np.random.uniform()

DisplayArray(u_init, rng=[-0.1, 0.1])
```

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/rainpoint.jpg)

参数设置

```python
# Parameters:
# eps -- time resolution
# damping -- wave damping
eps = tf.placeholder(tf.float32, shape=())
damping = tf.placeholder(tf.float32, shape=())

# Create variables for simulation state
U  = tf.Variable(u_init)
Ut = tf.Variable(ut_init)

# Discretized PDE update rules
U_ = U + eps * Ut
Ut_ = Ut + eps * (laplace(U) - damping * Ut)

# Operation to update the state
step = tf.group(
  U.assign(U_),
  Ut.assign(Ut_))
```

仿真

```python
# Initialize state to initial conditions
init = tf.global_variables_initializer()
sess.run(init)

# Run 1000 steps of PDE
for i in range(1000):
  # Step simulation
  step.run({eps: 0.03, damping: 0.04})
  # Visualize every 50 steps
  if i % 50 == 0:
    clear_output()
    DisplayArray(U.eval(), rng=[-0.1, 0.1])
```

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/ripple.jpg)