

# week 1
this was mainly in the papers and with lecs


# Week 2
## Octave Tutorial

### basic operations
```MATLAB
format long
format short
```
matrix creation

```MATLAB
A = [1 2; 3 4 ; 5 6]
```
it's 3 x 2 matrix A

```MATLAB
A = [
1 2;
3 4;
5 6
]
```

vector

```MATLAB
V = [1;2;3]
```

start from 1 and increament 0.1 till you reach 2

```m
V = 1: 0.1 :2
```
```m
ones(2,3)
zeros(row,column)
rand(row,column) % from 0 to 1 normal distripution
randn(m,n) % from gussaun distripution
eye(m,n)
```
plots
```m
hist(something)
hist(something,bins)
```
####the help

```m
help eye
help rand
```

### moving data

```m
size(A)
```
```m
size(A,1)

length(the largest to find )

```
current directory and list

```m
pwd
ls
```
load the data
```m
load file.ext
```
show the curent
```m
who
whos

```
assign part to var

```m
V  = priceY(1:10)
```
save file
```m
save name.ext variable;
```

indexing

```m
A(3,2)
 % : means every elemnt along that row/column
 A(2,:) % every elemnt in the second row
 A(:,2) % every elemnt in the second column
 A([1 3],:) %every elemnt in 1 and  3 row and every column
 A(:) % make them into single vector
```
append another column vecto to the right

```m
A = [A, [100; 101; 102 ]] % must use ;
C = [A B] %to the rright
C = [A;B] = [A,B] % add top bottom
```
multiple

```m
A*B % normal matrix multiplication
A .* B % to the other elemnt
A .^2 %square them
1 ./ A % inverse of the matrix
log(v)
abs(v)
exp(v)
-v
v + ones(length(v),1) %add one to each line
ones(row,column)
%or just
V + 1
A ' %transpose
max(A)
ind >>> return the indexing
max(matrix) = column matrix
a < 3 % element comparation
magic(3)
sum(a)
sum(A,1) %sum the columns
sum(A,2) %sum for rows
flipud(eye(8))

pinv(A) %invert of


prod(a)
floor(a)
ceil(a)
```

![noimg](week2/Untitled.png)


max per row and column


![noimg](week2/screenshot_37.png)


### plots


```m
plot(x,y)
```

hold on
```m

plot(x,y,y)
xlabel('something')
ylabel('something')
legend ('for y1' , 'for y2')
title('the title')
print - dpng 'name.png'
```
```m
figure(1); plot()
figure(1); plot()

subplot(r,c, number)
plot()
subplot(r,c, number)
plot()
```
change axis scale
```m
axis( [])
```

### control stetment

```m
for i = 1:20;
    v(i) = 2^i;
  end;
```
if statemnt
```m
if ;
  ssss
elsif;
  sssss
else;
  asdasd
```

define function
```m
function nameit(variable)
y = x^2;
```
we can add path

```m
addpath('path')
```

###Week 3

to look at
maximum likelihood estimation

#### use Advanced optimization

code to it

first we define function

```m
function [jVal, gradient] = costFunction(theta)
  jVal = [...code to compute J(theta)...];
  gradient = [...code to compute derivative of J(theta)...];
end
```
then we use it with fminunc to calc the theta
```m
options = optimset('GradObj', 'on', 'MaxIter', 100);
initialTheta = zeros(2,1);
   [optTheta, functionVal, exitFlag] = fminunc(@costFunction, initialTheta, options);
```

#Week 4 Neural Networks: Representation
Neural networks is a model inspired by how the brain works. It is widely used today in many applications: when your phone interprets and understand your voice commands, it is likely that a neural network is helping to understand your speech; when you cash a check, the machines that automatically read the digits also use neural networks.

#Week 6 Advice for Applying Machine Learning
In Week 6, you will be learning about systematically improving your learning algorithm. The videos for this week will teach you how to tell when a learning algorithm is doing poorly, and describe the 'best practices' for how to 'debug' your learning algorithm and go about improving its performance.

We will also be covering machine learning system design. To optimize a machine learning algorithm, you’ll need to first understand where the biggest improvements can be made. In these lessons, we discuss how to understand the performance of a machine learning system with multiple parts, and also how to deal with skewed data.

When you're applying machine learning to real problems, a solid grasp of this week's content will easily save you a large amount of work.

## Evaluating a Hypothesis
Once we have done some trouble shooting for errors in our predictions by:

1. Getting more training examples
2. Trying smaller sets of features
3. Trying additional features
4. Trying polynomial features
5. Increasing or decreasing λ

We can move on to evaluate our new hypothesis.

A hypothesis may have a low error for the training examples but still be inaccurate (because of overfitting). Thus, to evaluate a hypothesis, given a dataset of training examples, we can split up the data into two sets: a training set and a test set. Typically, the training set consists of 70 % of your data and the test set is the remaining 30 %.

### machine learning diagnostic
diagnostic is a test that you can run to gain insight what is/isn't working with learning algorithm and how to improve it

#### Model Selection and Train/Validation/Test Sets
One way to break down our dataset into the three sets is:

Training set: 60%
Cross validation set: 20%
Test set: 20%

We can now calculate three separate error values for the three different sets using the following method:

1. Optimize the parameters in Θ using the training set for each polynomial degree.
2. Find the polynomial degree d with the least error using the cross validation set.
3. Estimate the generalization error using the test set with J<sub>test</sub>Θ (d = theta from polynomial with lower error);

#### Diagnosing Bias vs. Variance

In this section we examine the relationship between the degree of the polynomial d and the underfitting or overfitting of our hypothesis.

We need to distinguish whether bias or variance is the problem contributing to bad predictions.
High bias is underfitting and high variance is overfitting. Ideally, we need to find a golden mean between these two.
The training error will tend to decrease as we increase the degree d of the polynomial.

At the same time, the cross validation error will tend to decrease as we increase d up to a point, and then it will increase as d is increased, forming a convex curve.

High bias (underfitting): both J_{train}(\Theta)J train  (Θ) and J_{CV}(\Theta)JCV (Θ) will be high. Also, J_{CV}(\Theta) \approx J_{train}(\Theta)J CV (Θ)≈J train (Θ).

High variance (overfitting): J_{train}(\Theta)J train (Θ) will be low and J_{CV}(\Theta)JCV (Θ) will be much greater than J_{train}(\Theta)J train (Θ).

The is summarized in the figure below:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/I4dRkz_pEeeHpAqQsW8qwg_bed7efdd48c13e8f75624c817fb39684_fixed.png?expiry=1602201600000&hmac=jCqun1nBqql80MRqHcT1ZJ6qqmQ6FDHbpeBzuMqblmE)
