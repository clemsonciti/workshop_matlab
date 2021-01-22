---
title: "The basics of Matlab"
teaching: 0
exercises: 0
questions:
- "how to initialize a variable?"
- "how to do basic arithmetics?"
- "how to get help?"
objectives:
- "MATLAB built-in functions"
- "`help`, `lookfor`"
- "`format`
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Now, let's open the ommand-line window. Here, you can type a command and hit `Enter`, and the command will be executed. If the command has a semi-colon at the end, its output will be suppressed. Let's try this:

~~~
x = 5
~~~
{: .matlab}

You should see the output:

~~~
x =

     5
~~~
{: .output}

What we did, is we initialized a variable `x` by assigning its value to five, and the result of this is displayed on the screen. Note that in MATLAB you don't need to declare the variable in order to assign a value to it. By default, all variables re double-precision floating point numbers (sometimes, to save memory, you need to convert them to single-precision, or to signed/unsigned integers; we will not be discussing it today). Now, let's try to do the same thing, but with a semi-colon: 

~~~
x = 5;
~~~
{: .matlab}

Now, you don't see the result of the command, because semi-colon suppresses the output. However, `x` is still set to five; you can check this by simply typing in the varable name:

~~~
x
~~~
{: .matlab}

~~~
x =

     5
~~~
{: .output}

And if we want to display the value of `x+1`, we just type

~~~
x + 1
~~~
{: .matlab}

~~~
ans =

     6
~~~
{: .output}

So you can use MATLAB as a very sophisticated calculator. To do powers, use the `^` character:

~~~
x^2
~~~
{: .matlab}

~~~
ans =

     25
~~~
{: .output}


To compute a square root, you can raise to the power of 0.5, or you can use a special `sqrt` function. In MATLAB, like in most languages, the arguments of the functions are given in parentheses:

~~~
sqrt(x)
~~~
{: .matlab}

~~~
ans =

     2.2361
~~~
{: .output}

You might think that the precision is not that great -- the answer is rounded to the fourth decimal point. However, the precision of the computations is actually pretty good (by default, the numerical variables use double precision, that is, 8 bytes); it's the precision of the output which is truncated. To change the format of the output, use the `format` function:

~~~
format long
sqrt(x)
~~~
{: .matlab}

~~~
ans =

     2.236067977499790
~~~
{: .output}

As you can see, the precision is pretty good! To change `format` back to the default, type `format short`. For built-in MATLAB functions, like `sqrt` and `format`, you can always bring up the manual and read about all the options and features of a function. This is done with the `help` command:

~~~
help sqrt
help format
~~~
{: .matlab}

The `help` command is a very useful feature and I use it all the time. MATLAB, being a licensed software that you have to pay for, has generlly excellent documentation.

To compute exponentials, you can use the `exp` function:

~~~
y = 1;
exp(y)
~~~
{: .matlab}

~~~
ans =

    2.7183
~~~
{: .output}

Let's say you want to compute a natural logarithm but you don't remember how to do it. First, you try `ln`:

~~~
ln (exp(1))
~~~
{: .matlab}

~~~
Unrecognized function or variable 'ln'.
~~~
{: .output}

So, you know it's not `ln`. But what is it? You can ask MATLAB to look it up for you by using the command `lookfor`:

~~~
lookfor logarithm
~~~
{: .matlab}

The `lookfor` command looks through all the available MATLAB functions and finds the ones that have the word "logarithm" in their description. It can take time; when you see the answer that you think it's the correct one, you can press `Ctrl+X` to stop loking further. As you can see from the output, the natural logarithm is computed with the `log` function. Let's try it:

~~~
log(exp(1))
~~~
{: .matlab}

~~~
ans =

    1
~~~
{: .output}

MATLAB has plenty of other mathematical functions: just to give a few examples, `abs` is the absolute value, `round` is rounding to the nearest integer, `sin` and `asin` are the sine and the arcsine, and `cosh` is a hyperbolic cosine for those so inclined. It also has some costants:

~~~
pi
~~~
{: .matlab}

~~~
ans =

    3.1416
~~~
{: .output}

~~~
i
~~~
{: .matlab}

~~~
ans =

   0.0000 + 1.0000i
~~~
{: .output}

~~~
e
~~~
{: .matlab}

~~~
Unrecognized function or variable 'e'.
~~~
{: .output}

As you can see, `e` is not defined. Instead, you an use `exp(1)`.

In addition to arithmetic computation, you can also do logical (Boolean) computation:

~~~
a = 5;
a > 5
~~~
{: .matlab}

~~~
ans =

  logical

   0
~~~
{: .output}

~~~
a == 5
~~~
{: .matlab}

~~~
ans =

  logical

   1
~~~
{: .output}


"Logical zero" means "false", and "logical one" means "true". Note that `==` is used to test the equality, and `=` is used to assign a value. Never confuse the two! 

You can also use Boolean operators: `&` for "and", `|` for "or", and `~` for "not". `~=` is "not equal": 

~~~
a ~= 5
~~~
{: .matlab}

~~~
ans =

  logical

   0
~~~
{: .output}

{% include links.md %}
