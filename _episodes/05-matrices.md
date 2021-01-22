---
title: "Working with matrices"
teaching: 0
exercises: 0
questions:
- "how to initialize a matrix"
- "how to access and modify elements in a matrix"
objectives:
- "matrix indexing"
- "matrix transposing"
- "`zeros`, `ones`, `eye`"
- "random matrices"
- "matrix inversion"
keypoints:
- "in matrix indexing, row goes first and column goes second"
- "`:` could be used to get an entire row or column of a matrix"
- "when multiplying two matrices, the number of columns in the first matrix must be equal to the number of rows of the second matrix"
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
     0
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

You an transpose a matrix just like you can transpose a vector. This turns rows into columns, and columns into rows:

~~~
A
~~~
{: .matlab}

~~~
ans =

     1     2     3
     4     5     0
     7     8     9
~~~
{: .output}

~~~
A'
~~~
{: .matlab}

~~~
ans =

     1     4     7
     2     5     8
     3     0     9
~~~
{: .output}

You can do matrix multiplication by using `*`. Remember that matrix multiplication does not work the same way as regular multiplication: A times B is not necessarily B times A. Also remember that, when you multiply two matrices, the number of columns in the first matrix must be equal to the number of rows in the second matrix. 

~~~
A*A
~~~
{: .matlab}

~~~
ans =

    30    36    30
    24    33    12
   102   126   102
~~~
{: .output}


~~~
A*A'
~~~
{: .matlab}

~~~
ans =

    14    14    50
    14    41    68
    50    68   194
~~~
{: .output}


~~~
A'*A
~~~
{: .matlab}

~~~
ans =

    66    78    66
    78    93    78
    66    78    90
~~~
{: .output}

Just like with vectors, `.*` is element-by-element multiplication. In order for it to work, both matrices need to have the same number of rows and the same number of columns. 

~~~
A'.*A
~~~
{: .matlab}

~~~
ans =

     1     8    21
     8    25     0
    21     0    81
~~~
{: .output}

If the dimensions don't match, you will get an error:

~~~
B = A(1:2, :)
~~~
{: .matlab}

~~~
ans =

     1     2     3
     4     5     0
~~~
{: .output}


~~~
A*B
~~~
{: .matlab}

~~~
Error using  * 
Incorrect dimensions for matrix multiplication. Check that the number of columns in the first matrix
matches the number of rows in the second matrix. To perform elementwise multiplication, use '.*'.
~~~
{: .error}

~~~
A.*B
~~~
{: .matlab}

~~~
Matrix dimensions must agree.
~~~
{: .error}

When you get the error like this, you can check the size of the matrices by using the `size` function to see where you went wrong. There is a lot of matrix multiplications in a typical MATLAB project, so the `size` function becomes very handy.

You can also stack the matrices together (concatenation), in horizontal or vertical direction:

~~~
[A A']
~~~
{: .matlab}

~~~
ans =

     1     2     3     1     4     7
     4     5     0     2     5     8
     7     8     9     3     0     9
~~~
{: .output}

~~~
[A; A']
~~~
{: .matlab}

~~~
ans =
     1     2     3
     4     5     0
     7     8     9
     1     4     7
     2     5     8
     3     0     9
~~~
{: .output}

Now, let's talk about creating some specific matrices. To create a matrix of zeros, you can use the `zeros` function, specifying the size in parenthesis:

~~~
zeros (4, 4)
~~~
{: .matlab}

~~~
ans =
     0     0     0     0
     0     0     0     0
     0     0     0     0
     0     0     0     0
~~~
{: .output}

Likewise, a matrix of ones can be created by the `ones` function:
~~~
ones (2, 5)
~~~
{: .matlab}

~~~
ans =
     1     1     1     1     1
     1     1     1     1     1
~~~
{: .output}

An important special matrix is an *identity matrix*, often called I in math texts, which has ones in the main diagonal and zeros everywhere else. It is important because multiplying any matrix by the identity matrix produces the original matrix: A\*I = I\*A = A. In a regular scalar world, number one is the identity: any number, multiplied by one, remains the same. In the matrix world, the identity matrix is the equivalent of number one. An identity matrix of size m-by-n can be created with `eye(m,n)`.

~~~
ones (3,3)
~~~
{: .matlab}

~~~
ans =
     1     0     0   
     0     1     0     
     0     0     1
~~~
{: .output}

An *inverse* of a matrix A is a matrix which, when multiplied by A, produces the identity matrix. In a scalar world, the inverse of number *x* is 1/*x* (the product of *x* and 1/*x* is the identity, or number one). In the matrix world, the inverse of a matrix is pretty tricky to compute by hand, but, luckily, in MATLAB you can do it easily by calling the `inv` function:


~~~
inv(A)
~~~
{: .matlab}

~~~
ans =
   -1.2500   -0.1667    0.4167
    1.0000    0.3333   -0.3333
    0.0833   -0.1667    0.0833
~~~
{: .output}

~~~
A*inv(A)
~~~
{: .matlab}

~~~
ans =
    1.0000         0    0.0000
         0    1.0000    0.0000
    0.0000         0    1.0000
~~~
{: .output}

~~~
inv(A)*A
~~~
{: .matlab}

~~~
ans =
    1.0000         0    0.0000
         0    1.0000    0.0000
    0.0000         0    1.0000
~~~
{: .output}

For those of us who use MATLAB for more advanced linear algebra, there are many more functions for matrix operations, such as `det` (for determinant), `eig` (for eigenvectors and eigenvalues), `svd` (for singular value decomposition), and others. 

In many situations, you need to generate random numbers, and matrices of random numbers. To generate a random number with uniform distribution between 0 and 1, you can use `rand` function; to generate m-by-n matrix of random numbers, you can use the same function as `rand (m,n)`: 

~~~
rand(3,4)
~~~
{: .matlab}

~~~
ans =
    0.8147    0.9134    0.2785    0.9649
    0.9058    0.6324    0.5469    0.1576
    0.1270    0.0975    0.9575    0.9706
~~~
{: .output}

If you want to generate random numbers with normal (Gaussian) distribution with mean of zero and standard deviation of one, you can use the `randn` function:

~~~
rand(3,4)
~~~
{: .matlab}

~~~
ans =
    0.7254   -0.2050    1.4090   -1.2075
   -0.0631   -0.1241    1.4172    0.7172
    0.7147    1.4897    0.6715    1.6302
~~~
{: .output}

You can use this to genrate normally-distributed numbers with any mean and standard deviation. For example, to generate a matrix of normally-distributed random variables with mean 2 and standard deviation 3, you can use `2 + 3*rand(3,4)`.

Let's say we have generated a matrix with zero-mean random Guassian numbers, and we want to "filter out" the negative numbers, that is, to set them to zero. We can do this with element-by-element multiplication:

~~~
Y = rand(5,5)
~~~
{: .matlab}

~~~
Y =
    1.1093   -0.0068    1.1174    1.5442    2.3505
   -0.8637    1.5326   -1.0891    0.0859   -0.6156
    0.0774   -0.7697    0.0326   -1.4916    0.7481
   -1.2141    0.3714    0.5525   -0.7423   -0.1924
   -1.1135   -0.2256    1.1006   -1.0616    0.8886
~~~
{: .output}

~~~
Y > 0
~~~
{: .matlab}

~~~
ans =

  5×5 logical array

   1   0   1   1   1
   0   1   0   1   0
   1   0   1   0   1
   0   1   1   0   0
   0   0   1   0   1
~~~
{: .output}

~~~
Y.*(Y>0)
~~~
{: .matlab}

~~~
Y =
    1.1093         0    1.1174    1.5442    2.3505
         0    1.5326         0    0.0859         0
    0.0774         0    0.0326         0    0.7481
         0    0.3714    0.5525         0         0
         0         0    1.1006         0    0.8886
~~~
{: .output}

You can see that the negative elements are filtered out, because they have been multiplied by zero, and the positive elements are preserved, because they have been multiplied by one. One thing that I would like to emphasize is how simple the matrix operations are. So far, we have never had to write a loop. It is possible to write a `for` loop in MATLAB, but it is actually not recommended to use a `for` loop if you can do the same thing without it by using MATLAB's matrix operations. This is particularly true of nested loops: try to avoid them as much as possible (not because they are bad, but because they are slow). Many of matrix operatins are *parallelizable*, that is, to compute the result, you can run several computations in parallel, rather than accessing them sequentially in a `for` loop. If your computer has several cores (CPUs), MATLAB will find a way to best utilize all of them for the purpose of parallelization. And, of course, on Palmetto we have some compute nodes which have as much as 56 cores, so MATLAB takes full advantage of that.



{% include links.md %}
