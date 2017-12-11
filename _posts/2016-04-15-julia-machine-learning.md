---
layout: post
title: "Julia编程(五): 机器学习"
author: "李军"
categories: journal
tags: [Julia, machine learning]
image:
  feature: juliabasics.jpg
  teaser: juliabasics-teaser.jpg
  credit:
  creditlink:
---

本文是Julia编程系列的第五篇文章，着重讲述它在机器学习方面的应用。

## 常见库
+ ScikitLearn.jl: 类似Python的scikit-learn 
+ TextAnalysis.jl

## Machine Learning from Scratch

+ linear regression

```julia
using Gadfly

f(x) = π*x
plot([f, x->x],0,1)

xys = [(x, f(x)) for x in rand(17)]
plot(
  layer(f, 0, 1), 
  layer(x=[x for (x,_) in xys], y=[y for (_,y) in xys], Geom.point)
  )
  
mutable struct LinearModel
    # Weight(s)
    w::Float64
end
# Initialisation doesn't have to be random, but it makes the step to neural models more natural.
LinearModel() = LinearModel(randn())
m             = LinearModel()
predict(m, x) = m.w*x
plot([f, x -> predict(m, x)], 0, 1)

# Objective (or loss), how "good" is our current model given the data?
# Mean Square Objective, note the "magic" divide by two.
objective(m, x, y) = (y - predict(m, x))^2/2
objective(m, xys)  = mean(objective(m, x, y) for (x, y) in xys)
# So, how "good" is our current random model?
objective(m, xys)

# Our gradient, but now in code.
∇objective(m, x, y) = x*(m.w*x - y)
∇objective(m, xys)  = mean(∇objective(m, x, y) for (x, y) in xys)
∇objective(m, xys)

finitediff(f, x; ϵ=10.0^-8.0) = (f(x + ϵ) - f(x - ϵ))/(2ϵ)
# In practice use Calculus.jl's `check_gradient` instead!
g(x)  = x^3
g′(x) = 3x^2
plot([g, g′, x -> finitediff(g, x)], -5, 5)

# Trusting plots can be a bit flaky, so let's calculate an error as well. 
mean((g′(x) - finitediff(g, x))^2 for x in linspace(-5, 5, 1024))
mean((∇objective(LinearModel(w), xys) - finitediff(v -> objective(LinearModel(v), xys), w))^2 for w in linspace(-5, 5, 1024))
plot([w -> ∇objective(LinearModel(w), xys), w -> finitediff(v -> objective(LinearModel(v), xys), w)], 0, 1)

# Learning rate (or step size).
μ = 0.1
# Save models for plotting.
models = LinearModel[deepcopy(m)]
# Gradient descent.
for _ in 1:128
    m.w -= μ*∇objective(m, xys)
    push!(models, deepcopy(m))
end
objective(m, xys)
plot(y=[objective(m, xys) for m in models], Geom.line)
plot([x -> predict(models[j], x) for j in (convert(Int, floor(i)) for i in linspace(1, length(models), 16))], 0, 1)

# A more powerful model.
mutable struct LinearModelWithBias
    w::Float64
    b::Float64
end
LinearModelWithBias() = LinearModelWithBias(randn(), 0)
m                     = LinearModelWithBias()
predict(m, x)         = m.w*x + m.b

objective(m, x, y) = (f(x) - predict(m, x))^2/2
objective(m, xys)  = mean(objective(m, x, y) for (x, y) in xys)

# Gradients left as an exercise, replace y′ with mw + b this time and work from there.
∇objective(m, x, y) = [x*((m.w*x + m.b) - y), (m.w*x + m.b) - y]
∇objective(m, xys)  = mean(∇objective(m, x, y) for (x, y) in xys)

models = LinearModelWithBias[deepcopy(m)]        
        
for _ in 1:512
    ∇w, ∇b = ∇objective(m, xys)
    m.w -= μ*∇w
    m.b -= μ*∇b
    push!(models, deepcopy(m))
end

objective(m, xys)
plot(y=[objective(m, xys) for m in models], Geom.line)
plot([x -> predict(models[j], x) for j in (convert(Int, floor(i)) for i in linspace(1, length(models), 16))], 0, 1)
```

+ logistic regression

```julia
apples  = Set([1, 3, 4, 5])
oranges = Set([2, 6, 7, 8])
lemons  = Set([9, 10])

# Format: Label, Height, Width, Mass.
fruit_data = readdlm("res/fruit_data.tsv")

# Remove apples and make labels binary.
fruit_data                                 = fruit_data[fruit_data[:, 1] .∈ oranges ∪ lemons, :]
fruit_data[fruit_data[:, 1] .∈ oranges, 1] = 1
fruit_data[fruit_data[:, 1] .∈ lemons, 1]  = 0
# Only work with width and mass to make visualisation easier.
fruit_data = fruit_data[:, [1, 3, 4]]

plot(x=fruit_data[:, 2], y=fruit_data[:, 3], color=fruit_data[:, 1])

# Use a random subset for training, then evaluate generalisation on the rest.
intrain = rand(Bool, size(fruit_data, 1))

train = let
    w = fruit_data[intrain, :]
    [(w[i, 2:end], w[i, 1]) for i in 1:size(w, 1)]
end

plot(x=[x[1] for (x, y) in train], y=[x[2] for (x, _) in train], color=[y for (_, y) in train])

test = let
    w = fruit_data[.!intrain, :]
    [(w[i, 2:end], w[i, 1]) for i in 1:size(w, 1)]
end

plot(x=[x[1] for (x, _) in test], y=[x[2] for (x, _) in test], color=[y for (_, y) in test])

σ(x)  = 1/(1 + exp(-x))
σ′(x) = σ(x)*(1 - σ(x))

plot([σ, σ′], -5, 5)

# Our first classification model.
mutable struct ClassificationModel
    w::Array{Float64}
    b::Float64
end
# Be careful with the initialisation, too large weights hampers learning and may even break it.
ClassificationModel() = ClassificationModel(randn(2)/128, 0)
m                     = ClassificationModel()
predict(m, x)         = σ(m.w'*x + m.b)

println("y", '\t', "y′", '\t', "is orange?")
for (x, y) in train
    println(y, '\t', round(predict(m, x), 3), '\t', predict(m, x) > 0.5)
end

# Negative Log-Likelihood, maximise the probability of the training data given the model.
objective(m, x, y) = -(y*log(predict(m, x)) + (1 - y)*log(1 - predict(m, x)))
objective(m, xys)  = mean(objective(m, x, y) for (x, y) in xys)
# Precision is more humanly interpretable.
prec(m, xys)       = mean((predict(m, x) > 0.5) == (y == 1) for (x, y) in xys)

(objective(m, train), objective(m, test), prec(m, train), prec(m, test))

# Warning, this gradient is significantly more difficult to derive -- but it turns out to be beautiful.
∇objective(m, x, y) = [x.*(σ(m.w'*x + m.b) - y), σ(m.w'*x + m.b) - y]
# We can no longer use `mean`, but this is functionally equivalent.
function ∇objective(m, xys)
    ∇ws = zero(m.w)
    ∇bs = zero(m.b)
    for (x, y) in xys
        ∇w, ∇b = ∇objective(m, x, y)
        ∇ws += ∇w
        ∇bs += ∇b
    end
    (∇ws/length(xys), ∇bs/length(xys))
end
 
∇objective(m, train)

models = ClassificationModel[deepcopy(m)]        

for _ in 1:2048
    ∇w, ∇b  = ∇objective(m, train)
    m.w    -= μ*∇w
    m.b    -= μ*∇b
    push!(models, deepcopy(m))
end

(objective(m, train), objective(m, test), prec(m, train), prec(m, test))

plot(
layer(y=[objective(m, train) for m in models], Geom.line),
    layer(y=[objective(m, test) for m in models], Geom.line),
)

println("y", '\t', "y′", '\t', "is orange?")
for (x, y) in train
    println(y, '\t', round(predict(m, x), 3), '\t', predict(m, x) > 0.5)
end

println("y", '\t', "y′", '\t', "is orange?")
for (x, y) in test
    println(y, '\t', round(predict(m, x), 3), '\t', predict(m, x) > 0.5)
end
```

+ a real-world dataset

```julia
# Housing prices in Boston from 1978.
# https://archive.ics.uci.edu/ml/datasets/Housing

# Format:
#    1.  Crime rate,
#    2.  Proportion of residential land
#    3.  Proportion of non-retail business
#    4.  Bounds river
#    5.  Nitric oxides concentration
#    6.  Average number of rooms
#    7.  Proportion of units built prior to 1940
#    8.  Weighted distances to five Boston employment centres
#    9.  Accessibility to radial highways
#    10. Property-tax rate
#    11. Pupil-teacher ratio
#    12. Proportion of blacks
#    13. Percentage of lower-status residents
#    14. Median value of homes
housing = readdlm("res/housing.tsv")

# Inputs, stored column-wise.
xs = housing[:, 1:13]'
# Normalise the data, often essential for regression problems.
xs = (xs .- mean(xs, 2))./std(xs, 2)
ys = housing[:, 14:14]' * 1_000

randomhouse = rand(1:size(xs, 2))
(randomhouse, xs[:, randomhouse], ys[randomhouse])

m = [
    # Weights.
    randn(1, size(xs, 1))/128,
    # Bias.
    0,
]
predict(m, xs)       = m[1]*xs .+ m[2]
objective(m, xs, ys) = mean((ys .- predict(m, xs)).^2./2)

predict(m, xs)[randomhouse]

objective(m, xs, ys)

using Knet

∇objective = grad(objective)

∇objective(m, xs[:, randomhouse], ys[randomhouse])

μ = 0.01

models = [m]

for _ in 1:1024
    ∇ = ∇objective(m, xs, ys)
    for i in 1:length(∇)
        m[i] -= μ.*∇[i]
    end
    push!(models, deepcopy(m))
end

objective(m, xs, ys)

using Gadfly

plot(
    y = [objective(m, xs, ys) for m in models], Geom.line,
)

(predict(m, xs)[randomhouse], ys[randomhouse])

labels = [
    "Crime rate",
    "Proportion of residential land",
    "Proportion of non-retail business",
    "Bounds river",
    "Nitric oxides concentration",
    "Average number of rooms",
    "Proportion of units built prior to 1940",
    "Weighted distances to five Boston employment centres",
    "Accessibility to radial highways",
    "Property-tax rate",
    "Pupil-teacher ratio",
    "Proportion of blacks",
    "Percentage of lower-status residents",
]
for (i, lbl) in enumerate(labels)
    @printf("%.4f\t%s\n", m[1][i], lbl)
end

m      = [
    # Weights.
    randn(64, size(xs, 1))/128,
    # Bias.
    0,
    randn(32, 64)/128,
    0,
    randn(1, 32)/128,
    0,
]
relu(x) = max(0, x)
function predict(m, xs)
    y′ = relu(m[1]*xs .+ m[2])
    for i in 3:2:length(m)
        y′ = m[i]*y′ .+ m[i + 1]
        if i < length(m) - 1
            y′ = relu(y′)
        end
    end
    y′
end

objective(m, xs, ys) = mean((ys .- predict(m, xs)).^2./2)
∇objective           = grad(objective)

for _ in 1:4096
    ∇ = ∇objective(m, xs, ys)
    for i in 1:length(∇)
        m[i] -= μ.*∇[i]
    end
    push!(models, deepcopy(m))
end

objective(m, xs, ys)

plot(
    y = [objective(m, xs, ys) for m in models], Geom.line,
)

(predict(m, xs)[randomhouse], ys[randomhouse])
```




















