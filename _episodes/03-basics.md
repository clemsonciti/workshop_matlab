---
title: "The basics of Matlab"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
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

Let's increment it by one:


<variable>
x = 5
x = 5;
< no need to declare the variable previously>
x
x+1
x = x+1;
x
<command history>
x^2
sqrt(5)
help sqrt
<function: arguments in parenthesis>
help sqrt

y = 1;
exp(1)
ln (exp (1))
lookfor logarithm
log (exp (1))

<many mathematical functions>
abs(-10)
round (7.5)
<cosh, asin>
pi
i
<e is not defined; try exp(1); precision is much greater than printed on screen>

a = 5
a > 5
<1 for true, 0 for false>
a == 5
a ~= 4
~(a == 5)


{% include links.md %}
