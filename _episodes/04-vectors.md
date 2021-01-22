---
title: "Working with vectors"
teaching: 0
exercises: 0
questions:
- "how to initialize vectors"
- "how to do basic operations (addition, multiplication) with vectors"
objectives:
- "row and column vectors; transposing"
- "range"
- "indexing"
keypoints:
- "for basic arithmetics, vectors must match in size and orientation (row, column)"
- "two types of multiplication: vector multiplication, and element-by-element"
---

As I have mentioned, the real power of MATLAB is in matrix computations. Matrices are two-dimensional arrays; before we go there, let's talk about one-dimensional arrays, which are also called *vectors*. The elements of a vector go inside square brackets. Let's define a vector:

~~~
x = [1 2 3 4 5]
~~~
{: .matlab}

~~~
x =

     1     2     3     4     5

~~~
{: .output}

We have defined a vector with five elements, the first being one, he second being two, et cetera. Vectors come in two flavours: row vectors and column vectors. The vector that we have defined is a row vector. To convert it into a column vector, we need to *transpose* it, which is done with an apostrophe:

~~~
y = x'
~~~
{: .matlab}

~~~
y =

     1
     2
     3
     4
     5

~~~
{: .output}

You can get the dimensions of a vector with an extremely useful command called `size`:

~~~
size (x)
~~~
{: .matlab}

~~~
ans =

     1     5
~~~
{: .output}

~~~
size (y)
~~~
{: .matlab}

~~~
ans =

     5     1
~~~
{: .output}

You can see that `x`, which is a row vector, is of size 1x5, and `y`, which is a column vector, is of size 5x1. Let's define another row vector with fve elements, and try to add it to `x`:

~~~
z = [2 3 4 5 6];
x + z
~~~
{: .matlab}

~~~
ans =

     3     5     7     9    11

~~~
{: .output}

You see that vector addition is done using exactly the same syntax as scalar addition. MATLAB knows that `x` and `z` are vectors, so it does vector addition. The first element of the sum is the sum of the first elements of the two vectors (1+2), the second element of the sum is the sum of the second elements, and so on. Now, let's try to add `z` to `y`:

~~~
y + z
~~~
{: .matlab}

In older versions of MATLAB, that will give you an error, because `y` is a column vector and `z` is a row vector, so their dimensions don't match. In MATLAB 2020, they have decided to change this, and the result looks like that:

~~~
ans =

     3     4     5     6     7
     4     5     6     7     8
     5     6     7     8     9
     6     7     8     9    10
     7     8     9    10    11

~~~
{: .output}

Now, let's try some vector multiplication:

~~~
x*y
~~~
{: .matlab}

~~~
ans =

     55

~~~
{: .output}

This is the product of a row vector and a column vector: the product of the first two elements plus the product of the second two elements etc., that is, `1*1 + 2*2 + 3*3 + 4*4 + 5*5`, which is 55. 

~~~
x*z
~~~
{: .matlab}

~~~
Error using  * 
Incorrect dimensions for matrix multiplication. Check that the number of columns in the first matrix
matches the number of rows in the second matrix. To perform elementwise multiplication, use '.*'.
~~~
{: .error}

You can't compute the product of the two row vectors, therefore, you get an error. However, if you transpose `z`, you will get a five-element column vector, so you *can* compute the product of `x` and the transpose of `z`:

~~~
x*z'
~~~
{: .matlab}

~~~
ans =

     70
~~~
{: .output}

Likewise, if you transpose `z`, you will be able to multiply it by `z`:

~~~
x'*z
~~~
{: .matlab}

~~~
ans =

     2     3     4     5     6
     4     6     8    10    12
     6     9    12    15    18
     8    12    16    20    24
    10    15    20    25    30
~~~
{: .output}

Remember that `z` is 1x5, and so is `x`, so `x'` is 5x1. If you multiply a 5x1 vector and a 1x5 vector, you will get a 5x5 matrix. The (i,j) element of this matrix is the product of (i)th element of of `x'` and (j)th element of `z`.

Another, totall different, kind of multiplication is element-by-element multiplication, done by `.*`. Remember that we got an error when we tried `x*z`. However, `x.*z` will work:

~~~
x.*z
~~~
{: .matlab}

~~~
ans =

     2     6    12    20    30
~~~
{: .output}

Here, the first element of the result is the product of the first element of `x` and the first element of `z`; the second element of the result is the product of the second element of `x` and the second element of `z`, and so on. You can do element-by-element multiplication of any vectors that have the same number of elements, and it doesn't matter whether they are row or column vectors. 

Now, let's talk about *ranges*. LEt's say you want a vector which elements are the numbers of 1 through 5. You can just type them one by one as we did before, but you can also specify the range:

~~~
x = 1:5
~~~
{: .matlab}

~~~
ans =

     1  2  3  4  5
~~~
{: .output}

You can aso specify the increment, e.g. a range of numbers from 1 to 5 in steps of 2:

~~~
x = 1:2:5
~~~
{: .matlab}

~~~
ans =

     1  3  5
~~~
{: .output}

OK, we have talked quite a bit about working with a vector as a whole, so let's talk about how to work with its parts, that is, how to access elements of a vector. The (i)th element of a vector `x` can be accessed as `x(i)`. In MATLAB (unlike C and Python), indexing starts from 1. Let's access some elements of `z`:

~~~
z
~~~
{: .matlab}

~~~
ans =

     2  3  4  5  6
~~~
{: .output}

~~~
z(1)
~~~
{: .matlab}

~~~
ans =

     2
~~~
{: .output}

~~~
z(4)
~~~
{: .matlab}

~~~
ans =

     5
~~~
{: .output}

~~~
z(1:3)
~~~
{: .matlab}

~~~
ans =

     2  3  4
~~~
{: .output}

The last example is interesting: you can use one vector to index another vector. Here, we use a vector `[1:3]` to index another vector `z`. 

Now that we know how to access elements of a vector, let's try to change them:

~~~
z(4) = 0;
z
~~~
{: .matlab}

~~~
ans =

     2  3  4  0  6
~~~
{: .output}

{% include links.md %}
