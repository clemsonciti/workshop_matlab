---
title: "Starting Matlab"
teaching: 0
exercises: 0
questions:
- "how to run MATLAB on Palmetto"
objectives:
- "qsub"
- "module load"
keypoints:
- "to start MATLAB, connect to a compute node and load the MATLAB module"
---
If you don't have MATLAB installed on your local computer, you can use MATLAB which is installed on Palmetto. 

PC users should use MobaXTerm to log into Palmetto as described [here](https://clemsonciti.github.io/workshop-palmetto/02-accessing-palmetto/index.html). Once you get on the login node, you should request a compute node with a `-X` option (otherwise, you will not be able to run MATLAB's graphical interface). Make sure you request at least 10 Gb of RAM, MATLAB is fairly memory-hungry program:

~~~
qsub -I -X -l select=1:ncpus=4:mem=10gb:interconnect=1g,walltime=2:00:00
~~~
{: .bash}

Once you get on a compute node, load the MATLAB module:

~~~
module load matlab/2020a
~~~
{: .bash}

Then, you can start MATLAB by typing

~~~
matlab
~~~
{: .bash}

Mac users can start the graphical interface to Matlab using the [VNC protocol](https://www.palmetto.clemson.edu/palmetto/basic/vnc/#running-vnc-on-a-mac-platform). 

{% include links.md %}
