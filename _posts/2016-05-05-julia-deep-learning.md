---
layout: post
title: "Julia编程(六): 深度学习"
author: "李军"
categories: journal
tags: [Julia, deep learning]
image:
  feature: juliabasics.jpg
  teaser: juliabasics-teaser.jpg
  credit:
  creditlink:
---

本文是Julia编程系列的第六篇文章深度学习方面的应用。

## 1 引言

**深度学习=大数据+超强计算力**

这两个缺一不可。神经网络从上世纪80-90年代开始急速发展，但是由于数据量和计算力的不足，导致在实际生活中应用很少，以至于神经网络从2000到2010年沉寂了近10年。从2009年开始神经网络开始应用于语音识别、计算机视觉等领域，神经网络又开始流行了。神经网络还是那个神经网络，复苏的主要驱动力就是数据量和计算力。

## 2 机器配置

* Best GPU overall (by a small margin): Titan Xp
* Cost efficient but expensive: GTX 1080 Ti, GTX 1070, GTX 1080
* Cost efficient and cheap: GTX 1060 (6GB)
* I work with data sets > 250GB: GTX Titan X (Maxwell), NVIDIA Titan X Pascal, or NVIDIA Titan Xp
* I have little money: GTX 1060 (6GB)
* I have almost no money: GTX 1050 Ti (4GB)
* I am a researcher: GTX 1080 Ti. In some cases, like natural language processing, a GTX 1070 or GTX 1080 might also be a solid choice — check the memory requirements of your current models
* I started deep learning and I am serious about it: Start with a GTX 1060 (6GB). Depending of what area you choose next (startup, Kaggle, research, applied deep learning) sell your GTX 1060 and buy something more appropriate
* I want to try deep learning, but I am not serious about it: GTX 1050 Ti (4 or 2GB)

## 3 常见库
+ Mocha.jl
+ MXNet.jl
+ TensorFlow.jl：封装了TensorFLow
+ Flux.jl
+ Knet.jl ⭐️

## 4 Neural Networks

### 4.1 A simplified Neural Network

y = f(Xw) where f is the activation function, e.g., sigmoid function f(z) = 1/(1 + exp(-z)), f_deriv(a) = a*(1-a).

e.g., X=[0 0 1;0 1 1;1 0 1;1 1 1]

y = [0,0,1,1]’

#### 3 inputs, 1 hidden layer, 1 output

pseudo code:

```julia
seed(1)
w = 2 * rand(3,1) -1
forloop
  l0 = X # 0th layer, that is input
  l1 = f(l0 * w) # 1th layer, that is hidden
  l1_error = y - l1
  l1_delta = l1_error * f_deriv(l1)
  w += l0’ * l1_delta
end
```

#### 3 inputs, 2 hidden layer, 1 output

pseudo code:

```julia
seed(1)
w1 = 2 * rand(3,4) -1
w2 = 2 * rand(4,1) -1
forloop
  l0 = X # 0th layer, that is input
  l1 = f(l0 * w1) # 1th hidden layer
  l2 = f(l1 * w2) # 2th hidden layer
  l2_error = y - l2
  l2_delta = l2_error * f_deriv(l2)
  l1_error = l2_delta * w2
  l1_delta = l1_error * f_deriv(l1)
  w2 += l1’ * l2_delta
  w1 += l0’ * l1_delta
end
```

### 4.2 using BackpropNeuralNet

#### 2 inputs, 1 layer with 3 neurons, 2 outputs

+ net=init_network([2,3,2])

#### inputs-outputs

+ train(net,[0.15,0.7],[0.1,0.9])

#### evaluate outputs

+ net_eval(net,[0.15,0.7])

### 4.3 using ANN

```julia
n_hidden_units = 20

ann = ArtificialNeuralNetwork(n_hidden_units)

n_obs = 150
n_feats = 80

X = rand(Float64, n_obs, n_feats)
y = rand(Int64, n_obs)

fit!(ann, X, y)

n_new_obs = 60
X_new = rand(Float64, n_new_obs, n_feats)

y_pred = predict(ann, X_new)
```

### 4.4 Mathematica program

```mathematica
# SLP 
# linear transformation by a matrix of specified dimension
# or net = NetChain[{5}]
net = NetChain[{LinearLayer[5]}]
# activation function
# or net = NetChain[{Ramp}]
# or ConvolutionLayer[]
# or LongShortTermMemoryLayer[]
net = NetChain[{ElementwiseLayer[Ramp]}]
net = NetChain[{ElementwiseLayer[Tanh]}]
net = NetChain[{ElementwiseLayer[LogisticSigmoid]}]
# initialize with some random weights and bias
net = NetInitialize[net]
```

### 4.5 MLP

```mathematica
# data acquisition
resource = ResourceObject["MNIST"];
data = ResourceData[resource, "TrainingData"];
sample = RandomSample[data, 100];

# establishing NN
net = NetChain[{ConvolutionLayer[20, 5], Ramp, PoolingLayer[2, 2],
              ConvolutionLayer[50, 5], Ramp, PoolingLayer[2, 2],
              FlattenLayer[], 500, Ramp, 10, SoftmaxLayer[]}];

# training NN
net = NetTrain[net, sample];
## relatively small sample
Table[{net[sample[[i, 1]]], sample[[i, 1]]}, {i, 1, 100}]

# classifying and predicting
Classify[]
Predict[]
```

## 5 应用

### 5.1 手写数字识别

```julia
using Mocha
srand(12345678)
 
data_layer  = AsyncHDF5DataLayer(name="train-data", source="data/train.txt", batch_size=64, shuffle=true)
conv_layer  = ConvolutionLayer(name="conv1", n_filter=20, kernel=(5,5), bottoms=[:data], tops=[:conv])
pool_layer  = PoolingLayer(name="pool1", kernel=(2,2), stride=(2,2), bottoms=[:conv], tops=[:pool])
conv2_layer = ConvolutionLayer(name="conv2", n_filter=50, kernel=(5,5), bottoms=[:pool], tops=[:conv2])
pool2_layer = PoolingLayer(name="pool2", kernel=(2,2), stride=(2,2), bottoms=[:conv2], tops=[:pool2])
fc1_layer   = InnerProductLayer(name="ip1", output_dim=500, neuron=Neurons.ReLU(), bottoms=[:pool2], tops=[:ip1])
fc2_layer   = InnerProductLayer(name="ip2", output_dim=10, bottoms=[:ip1], tops=[:ip2])
loss_layer  = SoftmaxLossLayer(name="loss", bottoms=[:ip2,:label])
 
backend = DefaultBackend()
init(backend)
 
common_layers = [conv_layer, pool_layer, conv2_layer, pool2_layer, fc1_layer, fc2_layer]
net = Net("MNIST-train", backend, [data_layer, common_layers..., loss_layer])
 
exp_dir = "snapshots-$(Mocha.default_backend_type)"
 
method = SGD()
params = make_solver_parameters(method, max_iter=10000, regu_coef=0.0005,
                                mom_policy=MomPolicy.Fixed(0.9),
                                lr_policy=LRPolicy.Inv(0.01, 0.0001, 0.75),
                                load_from=exp_dir)
solver = Solver(method, params)
 
setup_coffee_lounge(solver, save_into="$exp_dir/statistics.jld", every_n_iter=1000)
 
# report training progress every 100 iterations
add_coffee_break(solver, TrainingSummary(), every_n_iter=100)
 
# save snapshots every 5000 iterations
add_coffee_break(solver, Snapshot(exp_dir), every_n_iter=5000)
 
# show performance on test data every 1000 iterations
data_layer_test = HDF5DataLayer(name="test-data", source="data/test.txt", batch_size=100)
acc_layer = AccuracyLayer(name="test-accuracy", bottoms=[:ip2, :label])
test_net = Net("MNIST-test", backend, [data_layer_test, common_layers..., acc_layer])
add_coffee_break(solver, ValidationPerformance(test_net), every_n_iter=1000)
 
solve(solver, net)
 
#Profile.init(int(1e8), 0.001)
#@profile solve(solver, net)
#open("profile.txt", "w") do out
#  Profile.print(out)
#end
 
destroy(net)
destroy(test_net)
shutdown(backend)
```