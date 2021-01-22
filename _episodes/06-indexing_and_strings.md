---
title: "More indexing; Strings"
teaching: 0
exercises: 0
questions:
- "how to find things in a vector or a matrix"
- "how to work with strings"
objectives:
- "`find`"
- "string operations"
keypoints:
- "use `ind2sub` to convert indices to (row, column) format"
- "strings are vectors of characters"
- "use `strcmp` to compare strings"
---

Let's talk a little bit about finding things in a vector or a matrix. For this purpose, we can use the `find` command. Let's bring up our old vector `z` and find the elements in a vector that are equal to three: 

~~~
z
~~~
{: .matlab}

~~~
z =

     2     3     4     5     6
~~~
{: .output}

~~~
find (z == 3)
~~~
{: .matlab}

~~~
ans =

     2
~~~
{: .output}

The output means that the second element of `z` is three. Let's find the indices of the elements that are greater than three:

~~~
find (z > 3)
~~~
{: .matlab}

~~~
ans =

      3     4     5
~~~
{: .output}

Which is, the third, fourth, and fifth elements of `z` are greater than three. To get the values of these elements, we can use the `find` function to index the vector:

~~~
z (find (z > 3))
~~~
{: .matlab}

~~~
ans =

      4     5     6
~~~
{: .output}

To use `find` on a matrix could be a little bit trickier than on a vector. Let's create a random Gaussian matrix and find all the positive elements:

~~~
X = randn (3, 4)
~~~
{: .matlab}

~~~
X = 
   -0.7648    0.4882    1.4193    1.5877
   -1.4023   -0.1774    0.2916   -0.8045
   -1.4224   -0.1961    0.1978    0.6966
~~~
{: .output}

~~~
find (X > 0)
~~~
{: .matlab}

~~~
ans =
     4
     7
     8
     9
    10
    12
~~~
{: .output}

Huh? This looks puzzling. When you apply `find` to a matrix, it first converts it to a vector. So, in our example, the fourth element is the first element in the second row; the seventh element is the first element in the third row, etc. To convert the output of `find` into more intuitive row and column indices, let's use the `ind2sub` function:   

~~~
[row, col] = ind2sub(size(X), find (X>0))
~~~
{: .matlab}

~~~
row =

     1
     1
     2
     3
     1
     3


col =

     2
     3
     3
     3
     4
     4
~~~
{: .output}

Now, that's easier to interpret. The first positive element of X comes from row 1 and column 2, the second comes from row 1 and column 3, etc.

So far, we have been dealing with numbers. Now, let me show you how to deal with strings. In MATLAB, a string is a vector containing charaters. Strings are enclosed within single quotation marks:

~~~
str = 'Hello World!'
~~~
{: .matlab}

~~~
str =
    'Hello World!'
~~~
{: .output}

~~~
str(2)
~~~
{: .matlab}

~~~
ans =
    'e'
~~~
{: .output}

`str(2)` is the second character in `str`, which is `e`. Length of a string can be computed using the `length` function.

The tricky part about working with strings is comparing one string to another. Remember, strings are vectors of characters.


~~~
name = 'John';
name == 'John'
~~~
{: .matlab}

~~~
ans =

  1×4 logical array

   1   1   1   1
~~~
{: .output}

We initialize the variable `name` to a string "John". Then, if we naively want to compare it to "John", we would expect the answer `true`, but what we get instead is four ones. To understand better what's going on, let's compare it to "Jack":

~~~
name == 'Jack'
~~~
{: .matlab}

~~~
ans =

  1×4 logical array

   1   0   0   0
~~~
{: .output}

When you do `name == 'Jack'`, it compares the two vectors ("John" and "Jack") element-by-element. The first element is the same, therefore you get a one; the remaining elements are different, therefore you get three zeros. The moral is not to use `==` to compare strings! Instead, use a special function called `strcmp`:

~~~
strcmp (name, 'John')
~~~
{: .matlab}

~~~
ans =

  logical

   1
~~~   
{: .output}

~~~
strcmp (name, 'Jack')
~~~
{: .matlab}

~~~
ans =

  logical

   0
~~~
{: .output}

Now, this makes so much more sense! The variable `name` is equal to the string "John" (logical one), and not equal to the string "Jack" (logical zero).

{% include links.md %}
