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

Now, let's open the ommand-line window. Here, you can type a command and hit `Enter`, and the command will be executed. If the command has a semi-column at the end, its output will be suppressed. Let's try this:

~~~
x = 5
~~~
{: .bash}

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
