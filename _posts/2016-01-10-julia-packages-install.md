---
layout: post
title: "Julia包安装问题：关于qt5.6.2字符编码问题的一种解决方案"
author: "李军"
categories: journal
tags: [Julia, package]
image:
  feature: juliabasics.jpg
  teaser: juliabasics-teaser.jpg
  credit:
  creditlink:
---

从事数据科学相关研究、工作时，我们知道有些方法使得安装极其便捷，conda便是其中之一。我们可以使用anaconda或者miniconda来进行安装，并设置运行环境。但是在Julia包安装时，尤其涉及qt相关包时，会出现令人恼火的问题。其实python一些包安装时同样会出现类似问题。在查阅很多文章后发现，conda4.3与python环境存在一些冲突。

下面我将以macOS Sierra系统，python2.7，miniconda为例来描述并给出问题的一种解决方案。

## 安装Julia（graphical／command-line）并设置路径

```shell
vi .bash_profile
```

并在文件中添加Julia执行路径

```nothing
export PATH=“$/Applications/Julia-0.5.app/Contents/Resources/julia/bin:$PATH"
```

## 安装conda

### 在根目录下 

```shell
bash Miniconda2-latest-MacOSX-x86_64.sh
```

### 设置.bash_profile文件中的conda路径

```shell
vi .bash_profile
```

并在文件中添加Jconda路径

```nothing
export PATH=“/Users/xxx/miniconda2/bin:$PATH"
```

### 更新conda环境

```shell
conda update conda
```

### 设置conda4.2版本

```shell
conda install conda=4.2
```

### 用conda安装相关包

(安装qt时会提示升级conda版本至4.3，输入yes)

```shell
conda install qt
conda install scipy
conda install matplotlib
conda install jupyter
```

## 安装PyCall和PyPlot包

### 设置python环境

```julia
ENV[“PYTHON”] = “Users/xxx/miniconda2/bin/python”
```

### 安装包

```julia
Pkg.add(“PyCall”)
Pkg.build(“PyCall”)
Pkg.add(“PyPlot”)
```

### 此时使用@pyimport 需要首先调用PyCall包

(如果同时调用PyPlot包，可能会发生plt重名冲突)

```julia
using PyCall
@pyimport matplotlib.pyplot as plt
```

## 安装IJulia包

### 设置jupyter环境

```julia
ENV[“JUPYTER”] = “Users/xxx/miniconda2/bin/jupyter”
```

### 安装包

```julia
Pkg.build(“PyCall”)
Pkg.add(“IJulia”)
```

## 最后，我们强调将问题限制在conda包环境内，可以使得问题非常容易跟踪、查找和解决。