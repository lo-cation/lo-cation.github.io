---
layout: post
title: Debug user subroutines of ABAQUS
date:   2020-04-12 22:00:00 +0800
tags: FEM
---
ABAQUS provides powerful interfaces to users to customize their own materials or elements. While it is hard to debug the user subroutines line by line under environment of ABAQUS and make the coding experience unpleasant. Here is a tutorial to how to debug the subroutines.

## Environment
Since running a program in debug mode usually costs more time than just running, ABAQUS disables the debug function by default.
We need to enable the debug function from environment file first.

For the old version of ABAQUS, the environment settings are contained in _abaqus_v6.env_ and we can modify it directly.
While for the recent version, ABAQUS 2019 for example, _abaqus_v6.env_ is a main environment file which calls several sub files the build up environment.
The file needed modification is 
{% highlight bash %}
X:XXX\Dassault Systemes\SimulationServices\V6R2019x\win_b64\SMA\site\win86_64.env
{% endhighlight %}
where _X:\XXX_ is the installation path of ABAQUS.
The file is named according to the operation systems which means it could be slightly different on different machine.

_win86_64.env_ is written in Python mode and inside the file one can observe that there are lots of lines are commented out.
It is easy to locate the lines related debug function since ABAQUS writes indicative comments in the file.
We just need to uncomment those lines to enable debug mode.
Remeber to keep a backup of the original file in case you made any mistake and ensure you can switch back to default.

## Subroutine
To debug a subroutine under ABAQUS environment, we need to pause the program somehow.
A input function could be a good choice:
{% highlight fortran %}
logical :: firstrun = .true.
integer tempvar
if (firstrun) then
  write(*,*)"please input an integer:"
  read(*,*)tempvar
  firstrun = .false.
end if
{% endhighlight %}
By adding above piece of code into the beginning of the subroutine, it will pause when the subroutine is called.
A pause function could be another choice the do the same thing.

## ABAQUS Command
Since we need to pause the program, that means we should submit the job through an interactive console instead of using GUI.
One can use system command line and locate to the working directory of ABAQUS or just open ABAQUS command which will direct to working directory automaticlly.
{% highlight bash %}
abaqus job=<inp file name> user=<subroutine file name>.for int
{% endhighlight %}
Notice that job name is without .inp and one can also include the path of files relative to working directory if they are not in the same folder.
Remeber to include _int_ which means interactive in the command line or the job will be executed in backstage.
For more command, please check abaqus commands.

## Micorsoft Visual Studio
We are going to utilize the "attach to process" function of Microsoft Visual Studio (VS) to realize line by line debugging of subroutine.
Theoratically, any program can be debugged using the same way if the source code is available.

After the ABAQUS job is paused, open the subroutine in VS.
Usually, the subroutine will be called in the _standard.exe_ process of ABAQUS, but it could be different according the type of subroutine.
One can check the current process on the command line portal as shown following:
![Screenshot of Command Line](/images/posts/abaqus/20200412-Debug-1.png)

In VS, find the process in _Debugging->Attach to process ( 调试->附加到进程 )_ and set break points after pausing lines.
Then resume the job in command line, the job will be paused at the break point just setted and the subroutine can be debugged line by line.
Click stop debugging button, the ABAQUS job will be terminated as well.
