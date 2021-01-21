
---
title: "Working with matrices"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Now we are ready to start working with matrices. You can initialize the matrix by listing its elements in the square brackets []; rows are separated with semi-colons.

~~~
A = [1 2 3; 4 5 6; 7 8 9]
~~~
{: .matlab}

~~~
A =

     1     2     3
     4     5     6
     7     8     9
~~~
{: .output}

~~~
size (A)
~~~
{: .matlab}

~~~
ans =
     3     3
~~~
{: .output}

You can get to the element in the (i)th row and (j)th column of the `A` matrix with `A(i,j)`. 

~~~
A(1, 2)
~~~
{: .matlab}

~~~
ans =
     2
~~~
{: .output}

~~~
A(2, 3)
~~~
{: .matlab}

~~~
ans =
     6
~~~
{: .output}

~~~
A(2, 3) = 0
~~~
{: .matlab}

~~~
A =
     1     2     3
     4     5     0
     7     8     9
~~~
{: .output}

You can see that the element in the second row, third column is set to zero. You can also use ranges to index a matrix:

~~~
A(1, 1:2)
~~~
{: .matlab}

~~~
ans =
     1     2
~~~
{: .output}

~~~
A(2:3, 1:2)
~~~
{: .matlab}

~~~
ans =
     4     5
     7     8
~~~
{: .output}

You can also use `:` by itself to get an entire row (or column) of a matrix. You can index a whole first row of `A` by typing `A(1, :)`. Similarly, `A(:, 2)` indexes the whole second column of A.

~~~
A(1, :)
~~~
{: .matlab}

~~~
ans =
     1     2     3
~~~
{: .output}


~~~
A(:, 2)
~~~
{: .matlab}

~~~
ans =
     2
     5
     8
~~~
{: .output}

An interesting feature of MATLAB which is extremely useful sometimes is turning a matrix into a vector. This is done by `(:)`. The result is a column vector; the first column of A goes first, followed by the second column of A, etc.

~~~
A(:)
~~~
{: .matlab}

~~~
ans =
     1
     4
     7
     2
     5
     8
     3
     6
     9
~~~
{: .output}

Just like with vectors, you an use the `size` function to get the size of a matrix:

~~~
[m,n] = size(A)
~~~
{: .matlab}

~~~
m =
     3

n =
     3
~~~
{: .output}

Here, we called the `size` function which, in this case, returns two results: the first one is the number of rows, and the second is the number of columns. 

To get the diagonal values of a matrix, you can use the `diag` function:

~~~
diag(A)
~~~
{: .matlab}

~~~
ans =

     1
     5
     9
~~~
{: .output}

You an transpose a matrix just like you can transpose a vector. This turns rows into columns, and columns into rows

A'
A*A
A*A'

[A A']
[A; A']

eye(5)
zeros(5)
zeros(5,3)
ones(3,4)
rand(5)
randn(5)

X = rand(5)
mean (X)
std (X)
mean (X(:))

Y = randn (5)
mean (Y)
std (Y)
mean (Y(:))

sum (X)
sum (X')
sum (X(:))

X+Y
X*Y
X.*Y
inv(X)
det(X)

Y>0
Y.*(Y>0)






{% include links.md %}
