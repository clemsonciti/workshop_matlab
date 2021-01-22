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
So far, we have used the command-line interface to MATLAB. Oftentimes, you need to write a program and save it so you can rerun it later. A MATLAB program is called a *script*, and it is a file with the `.m` extension. 

I have prepared an example for you. If you are using Palmetto to run MATLAB, type this in terminal (not in MATLAB window):

~~~
git clone https://github.com/clemsonciti/matlab_workshop_examples.git
~~~
{: .bash}

This should create a folder called matlab_workshop_examples with a couple of examples. Let's look at the script called `blood_pressure.m`.

The first line, `clear all`, lears all previous variables from the workspace. It's good practice to have `clear all` at the beginning of your script (unless your script specifically relies on other scripts to create some variables in the workspace). 

The second line loads the Excel spreadsheet called `matlab_workshop_dataset.xls`. In MATLAB, reading the Excel spreadsheets is very easy, which is quite handy if you store your data in Excel. Writing into an Excel spreadsheet could be tricky, however (it works fine on Windows but is buggy on Mac OS). Here, we load the numerical values from the spreadsheet and save them into a matrix called `num`: `num = xlsread ('matlab_workshop_dataset.xls');`. There is a lot more to the `xlsread` function; please read `help xlsread` if you plan to work with Excel spreadsheets.

The spredsheet contains (fake) medical data for ten people: their patient IDs, systolic and diastolic pressure, pulse, and history of stroke (1 == had a stroke before, 0 == never had a stroke). Our MATLAB script saves different columns of the `num` matrix as separate vectors (`id`, `sys`, `dias`, `pulse`, `cvd`; CVD stands for "cardiovascular disease", like stroke). Then, we 


{% include links.md %}
