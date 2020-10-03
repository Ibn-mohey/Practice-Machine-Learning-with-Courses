

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
