---
title: "Starting Matlab"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

As I have mentioned, the real power of MATLAB is in matrix computations. Matrices are two-dimensional arrays; before we go there, let's talk about one-dimensional arrays, which are also called *vectors*. The elements of a vector go inside square brackets. Let's define a vector:

~~~
x = [1 2 3 4 5]

<no need to declare>
size (x)
<number of rows, number of columns>
y = x’
<there is a difference between horizontal and vertical vectors>
size (y)
length(x)
length(y)

z = [2 3 4 5 6]
x + z
x + y
<a very frequent cause of errors is dimension mismatch>
< size function is the most useful function in matlab>
x*y
<1*1+2*2+3*3...>
x*z
<error because of size mismatch; run size(x), size(y)>
x*z'
x'*z
size(x'*z)
x.*z



1:5
x = 1:5
1:2:5

x(1)
<indexing starts from 1>
x(1:3)
x(1:2:5)
x(1:3 4 5)
x(4) = 0
x




{% include links.md %}
