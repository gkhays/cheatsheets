# Windows Batch Cheat Sheet

Prefer `REM` over `::` for comments (`::` is an empty label and may cause problems).<br/>
`^` is the line continuation character.<br/>
`%*` contains all the arguments.<br/>
`%~nx0` is the name of the batch file whereas `%0` is the command used to call the batch file<br/>
`%~d0` gives the current drive, e.g. `F:\`<br/>
`%~p0` gives the current path

`IF "%~1"==""` checks if a parameter was passed. The `~` removes any surrounding quotes

`SHIFT` changes the parameter position, e.g. `shift-test.bat 1 2 3 4 5 6 7 8 9 10`

```bat
set LAST=%9%
shift
set AFTER_LAST=%9% <--- Gets the 10th argument
echo %LAST%
echo %AFTER_LAST%
```
**Output**:
```
9
10
```

Count the number of arguments and print a message if there are too few.

```bat
@echo off
setlocal EnableExtensions EnableDelayedExpansion

set n=0
for %%i in (%*) do (
    set /A n+=1
    set "args[!n!]=%%~i"
)

echo # of parameters: %n%
if /I "%n%" LSS "4" goto error
echo The first parameter is: "!args[1]!"
echo The fourth parameter is: "!args[4]!"
if /I "%args[5]%" == "" echo no 5th argument

:error
set USAGE="Usage: %~nx0 [one] [two] [three] [four]"
echo %USAGE%

endlocal
```

### SETX is Persistent

```bat
setx /m JAVA_HOME=C:\Program Files\Zulu\zulu-8\
```

Where the `/m` switch sets the variable system wide, e.g. `HKEY_LOCAL_MACHINE` instead of the deafulat `HKEY_CURRENT_USER`.

[What is the difference between SETX and SET in environment variables in Windows](https://superuser.com/a/916652/1100004)

### Retrieve IP Address into Variable

```bat
for /f "delims=[] tokens=2" %%a in ('ping %computername% -4 -n 1 ^| findstr "["') do (set ip=%%a)
```
[How do I get the IP address into a batch-file variable?](http://stackoverflow.com/questions/5898763/how-do-i-get-the-ip-address-into-a-batch-file-variable)

### Ant and Maven Build Shell on Portable Drive

Directory structure.

```bat
F:\
+--.m2
+--src
|  +--project1
|  +--project2
|  +--project3
+--tools
|  +--ant
|  +--maven
|  +--jdk
\--build.bat
\--mvn_ant_env.bat
```

Set up the tools.

```bat
@echo Setting Maven Environment...

set MAVEN_OPTS=-Xms256M -Xmx764M
set JAVA_HOME=%~d0\tools\jdk1.8.0_131
set M2_HOME=%~d0\tools\apache-maven-3.2.3
set ANT_HOME=%~d0\tools\apache-ant-1.9.4
PATH=%PATH%;%JAVA_HOME%\bin;%M2_HOME%\bin;%ANT_HOME%\bin
title Maven and Ant Enabled Shell
cmd
```

Now build some projects.

```bat
set HOME=%~d0

cd src\ism_version_0.2\base
call mvn -s %HOME%\.m2\settings.xml -Dmaven.repo.local=%HOME%\.m2\repository clean install
pushd %~dp0

cd src\daas_ags_conn
call mvn -s %HOME%\.m2\settings.xml -Dmaven.repo.local=%HOME%\.m2\repository clean install
pushd %~dp0

cd src\ags6
call ant all

pushd %~dp0
```

### References
1. [Which comment style should I use in batch files?](http://stackoverflow.com/a/12407934/6146580)
2. [Batch-Script - Iterate through arguments](http://stackoverflow.com/a/19837690/6146580)
3. [How do you utilize more than 9 arguments when calling a label in a CMD batch-script?](http://stackoverflow.com/a/29886675/6146580)
4. **Arrays**: [Create list or arrays in Windows Batch](http://stackoverflow.com/a/17606350/6146580) and [Arrays, linked lists and other data structures in cmd.exe (batch) script](http://stackoverflow.com/a/10167990/6146580)
5. [Get list of passed arguments in Windows batch script (.bat)](http://stackoverflow.com/a/382312/6146580)
6. [Using parameters in batch files at DOS command line](http://stackoverflow.com/a/14298769/6146580)
7. [Using batch parameters](https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/percent.mspx?mfr=true)
8. [What does d0 mean](https://stackoverflow.com/questions/112055/what-does-d0-mean-in-a-windows-batch-file)
9. [What does dp0 mean](https://stackoverflow.com/questions/5034076/what-does-dp0-mean-and-how-does-it-work)
10. [%~dp0 vs %cd%](http://www.computerhope.com/forum/index.php?topic=54333.0)
11. [Windows Batch Scripting: Advanced Tricks](https://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html)
