# hadoop
Apache Hadoop: We are providing kick start for Hadoop development platform.


----------------------------------------------------------------------------------

Building apache hadoop3 from source on Windows

----------------------------------------------------------------------------------
Requirements:

STEP 1 : Windows System :~

Determine windows OS platform is of x64 bit or  x86 ie 32 bit
Choose binaries accordingly.

Set Environment Variable :
Platform = x64 (when building on a 64-bit system)
Platform = Win32 (when building on a 32-bit system)


STEP 2 : Install JDK 1.8+ :~

Oracle JDK 8 [CLICK HERE]
Download and install Oracle jdk 8


STEP 3 : set JAVA_HOME :~

Now set JAVA_HOME to "C:\PROGRA~1\Java\JDK18~1.0_1" it is written correctly. you can run cd C:\PROGRA~1\Java\JDK18~1.0_1 if it works you can go to step 4.

What If not in that case you have to figure out your jdk path try to locate your jdk open  in explorer[WIN+E]  then  C:\program files** \** \java (Do not copy paste visit the folder)

Press [WIN+R] type cmd press enter command prompt will appear.

Change dir to c:\> by typing cd \

type dir /x press enter you will get extra column Like  PROGRA~1 PROGRA~2
select appropriate one then type cd  PROGRA~1 again type dir /x  you will not have any value in front of java so you can use cd java again run dir /x choose appropriate jdk folder then cd JDK18~1.0_1 now see your prompt will show you something like this  C:\PROGRA~1\Java\JDK18~1.0_1> copy only part without greater than sign  C:\PROGRA~1\Java\JDK18~1.0_1  now you can set your JAVA_HOME variable verify it by running on cmd %JAVA_HOME%\bin\java  -version press enter.

STEP 4 : Maven 3.0 or later :~

Apache Maven [CLICK HERE]

Extract zip folder to C:\apache-maven append path variable by C:\apache-maven\bin
or check your installation path

set Environment varible as follows :
M2_HOME = C:\apache-maven
M2 = %M2_HOME%\bin

STEP 5 : ProtocolBuffer 2.5.0 :~

Protocol Buffer [CLICK HERE]

Extract zip folder to C:\protoc-2.5.0-win32 append path variable by C:\protoc-2.5.0-win32
or check your installation path

Run on cmd
protoc -help

To find ProtocolBuffer 2.5.0 is installed correctly or not.

STEP 6 : Windows SDK 7.1 or Visual Studio 2010 Professional :~

Microsoft Windows SDK for Windows 7 and .NET Framework 4 (ISO) [CLICK HERE]
OR
Microsoft Windows SDK for Windows 7 and .NET Framework 4(Web Installer) [CLICK HERE]

Try to run msbuild on cmd see if it is working. append to Path variable C:\Windows\Microsoft.NET\Framework\v4.0.30319
or check your installation path

Need to set path for msbuild.exe

* Windows SDK 8.1 (if building CPU rate control for the container executor)

If using Visual Studio, it must be Visual Studio 2010 Professional (not 2012).Do not use Visual Studio Express.  It does not support compiling for 64-bit,
which is problematic if running a 64-bit system.  The Windows SDK 7.1 is free

For window 10 only you will face installation  problem Windows SDK 7.1 or Visual Studio 2010 Professional for that  you need to trick your computer by registry editing : I have prepared a script to do that you can use it
To run this script you have to use one administrative tool SubInACL 
SubInACL [CLICK HERE]


Append path variable by C:\Program Files (x86)\Windows Resource Kits\Tools
or check your installation path verify by run command on cmd SubInACL 

for /f "tokens=2*" %%a in ('reg query "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Client" /v Version /reg:32') do set "CurrentNDPv4ClientVersion=%%~b"
for /f "tokens=2*" %%a in ('reg query "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full" /v Version /reg:32') do set "CurrentNDPv4FullVersion=%%~b"

subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4" /setowner="%username%"
subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4" /grant="%username%"=f
reg ADD "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full" /v Version /t REG_SZ /d 4.0.30319 /reg:32 /f
reg ADD "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Client" /v Version /t REG_SZ /d 4.0.30319 /reg:32 /f

echo start your installer now
pause

reg ADD "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Client" /v Version /t REG_SZ /d %CurrentNDPv4ClientVersion% /reg:32 /f
reg ADD "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full" /v Version /t REG_SZ /d %CurrentNDPv4FullVersion% /reg:32 /f

subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4" /revoke="%username%"
subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4" /setowner="NT SERVICE\TrustedInstaller"

copy this script and save it in a text file with [DOT]bat extension like  I use "ms10_vs_help.bat"  and run it with administrator privileges. This script will take pause do not close the script just install while it take pause and run it again.

STEP 7 : CMake 2.6 or newer :~

CMake[CLICK HERE]

Download stable version cmake-3.6.2-win32-x86.msi because I faced issues while building with rc version so it is advisable and check add check the check box add to path for all users .Try to run cmake on cmd see if it is working.
or check your installation path and append to PATH  variable
Note: If you install cmake before step 6 may be your cmake not able to detect your compiler in that case you have to configure it accordingly or reinstall.

STEP 8 : zlib headers :~

zlib [CLICK HERE]

Download source & Download binaries

You have to do both the steps it is not optional

For binaries :~
Extract zip folder to C:\zlib128-dll append path variable by C:\zlib128-dll

For Source :~
Extract zip folder to C:\zlib-1.2.8 add Environment varible ZLIB_HOME = C:\zlib-1.2.8

STEP 9 : Unix command-line tools from GnuWin32 :~

Gnuwin32 [CLICK HERE]


Unix command-line tools from GnuWin32: sh, mkdir, rm, cp, tar, gzip. These
tools must be present on your PATH.

It is a exe which is compressed you are extracting it don't get confused with install button. now click on install on its default setting don't make any changes.
a folder will be created in same directory


now open cmd go to directory type this command
c:\Downloads\GetGnuWin32\> install c:\gnuwin32
Cygwin is neither required nor supported.

STEP 10 : Python ( for generation of docs using 'mvn site') :~

Python [CLICK HERE]

STEP 11 : Git (for sh and bash ) :~

Git [CLICK HERE]

Unix command-line tools are also included with the Windows Git package

need to set path to git bin bash.exe and sh.exe
Install Git by default settings and  append path variable by C:\Program Files\Git\bin

Try to run bash & sh on cmd(two different consoles) see if it is working.

STEP 12 : Hadoop Source :~

Hadoop Source [CLICK HERE]

Keep the source code tree in a short path to avoid running into problems related
to Windows maximum path length limitation (for example, C:\hdc).

STEP 13 : Run builds :~

Run builds from a Windows SDK Command Prompt. (Start, All Programs,
Microsoft Windows SDK v7.1, Windows SDK 7.1 Command Prompt).

Click on start > All Programs > Microsoft Windows SDK v7.1 > Windows SDK 7.1 Command Prompt now change Directory to hadoop source folder then run the following command

mvn -e -X -Dmaven.compiler.fork=true -Dmaven.compiler.executables=%JAVA_HOME%\bin package -Pdist,native-win -DskipTests -Dtar

If you face ant run plugin exception try 
 mvn antrun:run 


then run

mvn package -Pdist,native-win -DskipTests -Dtar

STEP 14 : Extract Builds :~

A successful build generates a binary hadoop.tar.gz package in  [source Root Directory] hadoop-dist\target\. 

STEP 15 : Required 7-Zip  to Extract Builds :~

7-Zip [CLICK HERE]

Install 7-Zip software in your system by default settings.

STEP 16 : Extract Builds :~

Extract the tar.gz file (e.g.hadoop-x.x.x.tar.gz) under c:\deploy 



STEP 17 : Class Not Found Issue :~

It may happen you have user name with white spaces so in that scenario I would suggest just create another user without any space.


STEP 18 : Configure Command Prompt :~

Now we have build hadoop from source but to run on IDE for debugging & development we need our command prompt to be conigured with equivalent configuration of Windows SDK 7.1 Command Prompt so how can we do that.

Press Win+R type cmd on command prompt type set > command.txt
Now open Windows SDK 7.1 Command Prompt and type set > wcommand.txt

Note:Check the files will be generated in current directory so please note down the directory location and collect those files.


Then open this site diffchecker. diff tool to compare text differences between two text files.Or use any difference checker tool.

compare those file and set all the variable which is not available in command.txt  Including path variable please set path variable with care if you made a mistake it may result on your OS. Better approach just copy paste.

then run

mvn package -Pdist,native-win -DskipTests -Dtar

Hopefully you will compile successfully this time also as you did in Step 13.

STEP 19 : Configure Hadoop For Intellij :~


cd into your hadoop directory.
Type the following command to create the Hadoop IntelliJ projects.

mvn idea:idea

Open IntelliJ.
Select Open… from the top menu bar.
Browse to the hadoop-main.ipr file in your hadoop directory.
Open hadoop-main-ipr.

compile project again by this command may be you will face administrative privileges issue so while running your intellij instance just right click and run as administrator better approach use administrator account for development 

mvn package -Pdist,native-win -DskipTests -Dtar

Hopefully you will compile successfully this time also as you did in Step 19.

STEP 20 : Run Hadoop Examples :~


Select Run > Edit Configurations… from the top menu bar.
Click on the ‘+‘ symbol in the upper left hand corner of the Run/Debug Configurations screen.
Enter org.apache.hadoop.util.Runjar the main class.
Enter path 
(your hadoop foder)/hadoop-dist/target/hadoop-X.X.X-XXXXXX/share/hadoop/mapreduce/hadoop-mapreduce-examples--X.X.X-XXXXXX.jar pi 10 10
of the Hadoop examples jar the program arguments.

better approach search for hadoop-mapreduce-examples--X.X.X-XXXXXX.jar then right click open file location copy the path in explorer and append the jar file name accordingly then place the path with the text in red it is nothing but arguments pi is a class name.

Class Path of module select hadoop-minicluster because it has org.apache.hadoop.util.Runjar

Click on the OK button. then Run/Debug Configurations screen.
Hopefully you will compile successfully this time also with result 3.2


STEP 20 : We will develop word count project and have fun :~
updates will be publish at next weekends, demands and questions are welocome.

Hopefully you will not face any issues while compiling the project & configuring development environment If you still face some issue feel free to comments I have tried my best to describe all the steps.

To Configure Hadoop you can follow Hadoop2OnWindows

If you still face any issue feel free to connect with me Email: jaypatil.sonu@gmail.com