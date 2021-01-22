---
title: "Visualization"
teaching: 0
exercises: 0
questions:
- "How to plot data?"
objectives:
- "`plot`"
- "line plots and scatter plots"
keypoints:
- "use `figure` to plot the data on a new figure, and use `hold on` to superimpose plots on the same figure"
---

MATLAB is pretty great for visualizing your results. The main function for visualization is `plot`; it's an incredibly powerful function with many options. In our tutorial, I will show you just the basic use; if you are curious, you can read more about it on the excellent [MATLAB website](https://www.mathworks.com/help/matlab/ref/plot.html). 

To see a simple example of how it works, let's plot the square root function. Let's create a vector `x` of numbers from 1 to 100, and another vector `y` of their square roots, and then plot `y` against `x`:

~~~
x = 1:100;
y = sqrt (x);
plot (x, y);
~~~
{: .matlab}

A new window will pop up with a beautiful plot of a square root function:

<img src="../fig/sqrt_line.png" style="height:450px">

If you want, you can save it as a picture (JPEG, TIGG, PNG, etc.) by clicking `File` -> `Save as`. If you are familiar with vector graphics software like Corel Draw or Adobe Illustrator, you can save it as extended postscript (EPS) and then edit it in Corel Draw or Illustrator; with practice, you can create very high-quality graphics.

The plot that we created is called a *line plot*, where the data points are conneted with lines. Sometimes we want to create a scatter plot, where each data point is shown with a marker. Let's do it:

~~~
plot (x, y, 'o')
~~~
{: .matlab}

We will see that our line plot will be replaced with a scatter plot:

<img src="../fig/sqrt_scatter.png" style="height:450px">

Here, each of the 100 datapoints is represented with a circle. You can also use other markers (dots, crosses, triangles, etc.); refer to the `plot` manual on the MATLAB website. 

Notice that our old line plot was replaced with a scatter plot. If you want to plot the scatter plot on a different figure, use the `figure` command before `plot`. On the other hand, if you want the scatter plot to be plotted on top of the line plot, use the `hold on` command; this way, all plots within one figure will be overlaying on top of each other.
{% include links.md %}
