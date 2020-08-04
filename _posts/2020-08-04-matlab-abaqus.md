---
layout: post
title: Call ABAQUS in MATLAB
date:   2020-08-04
tags: FEM
---
To establish a set of models in ABAQUS, writing a Python script and a control script in MATLAB or other language like bash to create and submit models automaticly will save lots of labors.
In MATLAB, one can call command line using function `dos()`.
To call ABAQUS and run corresponding Python script without opening its GUI, using following command:
```
mycmd = 'abaqus cae noGUI=myPath\myScript.py --vars';
[status, cmdout] = dos(mycmd);
```
The working directory of ABAQUS will be the current directory of MATLAB.

In `mycmd`, `vars` will be passed into `myScript.py`.
To use vars while running the script, adding following codes into `myScripy.py`
```
import sys
vars = sys.argv[-1]
```
Notice that `sys.argv` is a list that contains all arguments in mycmd, which means, `abaqus`, `cae` and so on are included.
Thus, it would be convenient to count var from the end.
