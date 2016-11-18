<div dir="ltr" style="text-align: left;" trbidi="on">
----------------------------------------------------------------------------------<br />
<br />
Building apache hadoop3 from source on Windows<br />
<br />
----------------------------------------------------------------------------------<br />
Requirements:<br />
<br />
<b>STEP 1 :&nbsp;Windows System&nbsp;:~</b><br />
<br />
Determine windows OS platform is of x64 bit or &nbsp;x86 ie 32 bit<br />
Choose binaries accordingly.<br />
<br />
Set Environment Variable :<br />
Platform = x64 (when building on a 64-bit system)<br />
Platform = Win32 (when building on a 32-bit system)<br />
<div>
<br /></div>
<br />
<b>STEP 2 :&nbsp;Install JDK 1.8+&nbsp;:~</b><br />
<br />
<a href="http://www.oracle.com/technetwork/java/javase/downloads/index.html">Oracle JDK 8 [CLICK HERE]</a><br />
Download and install Oracle jdk 8<br />
<br />
<br />
<b>STEP 3 :&nbsp;set JAVA_HOME&nbsp;:~</b><br />
<br />
Now set JAVA_HOME to "<b>C:\PROGRA~1\Java\JDK18~1.0_1</b>" it is written correctly. you can run <b>cd C:\PROGRA~1\Java\JDK18~1.0_1</b> if it works you can go to step 4.<br />
<br />
What If not in that case you have to figure out your jdk path try to locate your jdk open &nbsp;in explorer[WIN+E] &nbsp;then &nbsp;C:\program files** \** \java (Do not copy paste visit the folder)<br />
<br />
Press [WIN+R] type cmd press enter command prompt will appear.<br />
<br />
Change dir to c:\&gt; by typing cd \<br />
<br />
type dir /x press enter you will get extra column Like &nbsp;PROGRA~1 PROGRA~2<br />
select appropriate one then type <b>cd &nbsp;PROGRA~1</b> again type dir /x &nbsp;you will not have any value in front of java so you can use <b>cd java</b> again run dir /x choose appropriate jdk folder then cd JDK18~1.0_1 now see your prompt will show you something like this <b>&nbsp;C:\PROGRA~1\Java\JDK18~1.0_1&gt;</b> copy only part without greater than sign <b>&nbsp;C:\PROGRA~1\Java\JDK18~1.0_1</b> &nbsp;now you can set your JAVA_HOME variable verify it by running on cmd&nbsp;<b>%JAVA_HOME%\bin\java &nbsp;-version</b> press enter.<br />
<br />
<b>STEP 4 :&nbsp;Maven 3.0 or later&nbsp;:~</b><br />
<br />
<a href="http://maven.apache.org/download.cgi">Apache Maven [CLICK HERE]</a><br />
<br />
Extract zip folder to&nbsp;<b>C:\apache-maven</b> append path variable by <b>C:\apache-maven\bin</b><br />
or check your installation path<br />
<br />
<div style="background-color: white; box-sizing: border-box; font-family: Verdana, Geneva, Tahoma, Arial, Helvetica, sans-serif; font-size: 15px !important; line-height: 24px; margin: 0em 0.2em 1em; padding: 0px; text-align: justify; word-wrap: break-word;">
<i style="box-sizing: border-box;">set Environment varible as follows :</i><br />
<i style="box-sizing: border-box;">M2_HOME =&nbsp;</i><span style="background-color: transparent; text-align: left;">C:\apache-maven</span></div>
<div style="background-color: white; box-sizing: border-box; font-family: Verdana, Geneva, Tahoma, Arial, Helvetica, sans-serif; font-size: 15px !important; line-height: 24px; margin: 0em 0.2em 1em; padding: 0px; text-align: justify; word-wrap: break-word;">
<i style="box-sizing: border-box;">M2 = %M2_HOME%\bin</i><br />
<br /></div>
<b>STEP 5 :&nbsp;ProtocolBuffer 2.5.0&nbsp;:~</b><br />
<br />
<a href="https://github.com/google/protobuf/releases?after=v2.6.1">Protocol Buffer [CLICK HERE]</a><br />
<br />
Extract zip folder to&nbsp;C:\protoc-2.5.0-win32 append path variable by C:\protoc-2.5.0-win32<br />
or check your installation path<br />
<br />
Run on cmd<br />
protoc -help<br />
<br />
To find ProtocolBuffer 2.5.0 is installed correctly or not.<br />
<br />
<b>STEP 6 :&nbsp;Windows SDK 7.1 or Visual Studio 2010 Professional&nbsp;:~</b><br />
<br />
<a href="https://www.microsoft.com/en-in/download/details.aspx?id=8442">Microsoft Windows SDK for Windows 7 and .NET Framework 4 (ISO) [CLICK HERE]</a><br />
OR<br />
<a href="http://www.microsoft.com/en-us/download/details.aspx?id=8279">Microsoft Windows SDK for Windows 7 and .NET Framework 4(Web Installer) [CLICK HERE]</a><br />
<br />
Try to run msbuild on cmd see if it is working. append to Path variable&nbsp;C:\Windows\Microsoft.NET\Framework\v4.0.30319<br />
<div>
or check your installation path<br />
<br /></div>
Need to set path for msbuild.exe<br />
<br />
* Windows SDK 8.1 (if building CPU rate control for the container executor)<br />
<br />
If using Visual Studio, it must be Visual Studio 2010 Professional (not 2012).Do not use Visual Studio Express. &nbsp;It does not support compiling for 64-bit,<br />
which is problematic if running a 64-bit system. &nbsp;The Windows SDK 7.1 is free<br />
<br />
For window 10 only you will face installation &nbsp;problem&nbsp;Windows SDK 7.1 or Visual Studio 2010 Professional for that &nbsp;you need to trick your computer by registry editing : I have prepared a script to do that you can use it<br />
To run this script you have to use one administrative tool&nbsp;<span style="background-color: white; color: #2f2f2f; font-family: , , &quot;tahoma&quot; , &quot;verdana&quot; , &quot;arial&quot; , sans-serif;">SubInACL</span><span style="background-color: white; color: #2f2f2f; font-family: , , &quot;tahoma&quot; , &quot;verdana&quot; , &quot;arial&quot; , sans-serif; font-size: 30px;">&nbsp;</span><br />
<a href="https://www.microsoft.com/en-in/download/details.aspx?id=23510">SubInACL [CLICK HERE]</a><br />
<br />
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: black; font-family: verdana, geneva, tahoma, arial, helvetica, sans-serif; font-size: 15px; font-style: normal; font-variant-caps: normal; font-variant-ligatures: normal; font-weight: normal; letter-spacing: normal; line-height: 24px; margin: 0em 0.2em 1em; orphans: 2; padding: 0px; text-align: justify; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; word-wrap: break-word;">
</div>
<br />
<div style="margin: 0px; orphans: 2; text-align: left; text-indent: 0px; widows: 2;">
<span style="color: black; font-family: &quot;times new roman&quot;; font-size: small; font-style: normal; font-weight: normal; letter-spacing: normal; text-transform: none; white-space: normal; word-spacing: 0px;">Append path variable by </span><b>C:\Program Files (x86)\Windows Resource Kits\Tools</b></div>
or check your installation path verify by run command on cmd&nbsp;SubInACL <br />
<br />
<pre class="lang-java prettyprint prettyprinted" style="background-color: #eff0f1; border: 0px; margin-bottom: 1em; max-height: 600px; overflow: auto; padding: 5px; width: auto; word-wrap: normal;"><span style="color: #303336; font-family: &quot;consolas&quot; , &quot;menlo&quot; , &quot;monaco&quot; , &quot;lucida console&quot; , &quot;liberation mono&quot; , &quot;dejavu sans mono&quot; , &quot;bitstream vera sans mono&quot; , &quot;courier new&quot; , monospace , sans-serif;">for /f "tokens=2*" %%a in ('reg query "HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Client" /v Version /reg:32') do set "CurrentNDPv4ClientVersion=%%~b"
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
subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4" /setowner="NT SERVICE\TrustedInstaller"</span></pre>
<div>
<br /></div>
copy this script and save it in a text file with [DOT]bat extension like &nbsp;I use "ms10_vs_help.bat" &nbsp;and run it with administrator privileges. This script will take pause do not close the script just install while it take pause and run it again.<br />
<br />
<b>STEP 7 :&nbsp;CMake 2.6 or newer&nbsp;:~</b><br />
<br />
<a href="https://cmake.org/download/">CMake[CLICK HERE]</a><br />
<br />
Download stable version&nbsp;<a href="https://cmake.org/files/v3.6/cmake-3.6.2-win32-x86.msi" style="background: rgb(240, 240, 240); border: 0px; box-sizing: border-box; color: #2763bc; font-family: &quot;Open Sans&quot;, Arial, sans-serif; font-size: 14px; margin: 0px; outline: 0px; padding: 0px; text-decoration: none; vertical-align: baseline;">cmake-3.6.2-win32-x86.msi</a>&nbsp;because I faced issues while building with rc version so it is advisable and check add check the check box add to path for all users .Try to run cmake on cmd see if it is working.<br />
or check your installation path and append to PATH &nbsp;variable<br />
Note: If you install cmake before step 6 may be your cmake not able to detect your compiler in that case you have to configure it accordingly or reinstall.<br />
<br />
<b>STEP 8 :&nbsp;zlib headers :~</b><br />
<br />
<a href="http://www.zlib.net/">zlib [CLICK HERE]</a><br />
<br />
Download source &amp; Download binaries<br />
<br />
You have to do both the steps it is not optional<br />
<br />
For binaries :~<br />
Extract zip folder to C:\zlib128-dll&nbsp;append path variable by C:\zlib128-dll<br />
<div>
<br /></div>
<div>
For Source :~</div>
<div>
Extract zip folder to C:\zlib-1.2.8&nbsp;add Environment varible&nbsp;ZLIB_HOME = C:\zlib-1.2.8</div>
<div>
<br />
<b>STEP 9 :&nbsp;Unix command-line tools from GnuWin32&nbsp;:~</b></div>
<br />
<a href="http://gnuwin32.sourceforge.net/">Gnuwin32 [CLICK HERE]</a><br />
<br />
<br />
Unix command-line tools from GnuWin32: sh, mkdir, rm, cp, tar, gzip. These<br />
tools must be present on your PATH.<br />
<br />
It is a exe which is compressed you are extracting it don't get confused with install button. now click on install on its default setting don't make any changes.<br />
a folder will be created in same directory<br />
<span style="color: #413f36; font-family: monospace;"><span style="background-color: #f4efd6; font-size: 12px;"><br /></span></span>
<br />
now open cmd go to directory&nbsp;type this command<br />
c:\Downloads\GetGnuWin32\&gt; install c:\gnuwin32<br />
Cygwin is neither required nor supported.<br />
<div>
<br /></div>
<b>STEP 10 :&nbsp;Python ( for generation of docs using 'mvn site')&nbsp;:~</b><br />
<br />
<a href="https://www.python.org/downloads/">Python [CLICK HERE]</a><br />
<br />
<b>STEP 11 :&nbsp;Git (for sh and bash )&nbsp;:~</b><br />
<br />
<a href="https://git-scm.com/downloads">Git [CLICK HERE]</a><br />
<br />
Unix command-line tools are also included with the Windows Git package<br />
<br />
need to set path to git bin bash.exe and sh.exe<br />
Install Git by default settings and &nbsp;append path variable by C:\Program Files\Git\bin<br />
<br />
Try to run bash &amp; sh on cmd(two different consoles) see if it is working.<br />
<br />
<b>STEP 12 :&nbsp;Hadoop Source&nbsp;:~</b><br />
<br />
<a href="http://hadoop.apache.org/">Hadoop Source [CLICK HERE]</a><br />
<br />
Keep the source code tree in a short path to avoid running into problems related<br />
to Windows maximum path length limitation (for example, C:\hdc).<br />
<div>
<br /></div>
<b>STEP 13 :&nbsp;Run builds&nbsp;:~</b><br />
<br />
Run builds from a Windows SDK Command Prompt. (Start, All Programs,<br />
Microsoft Windows SDK v7.1, Windows SDK 7.1 Command Prompt).<br />
<div>
<br /></div>
Click on start &gt; All Programs &gt;&nbsp;Microsoft Windows SDK v7.1 &gt;&nbsp;Windows SDK 7.1 Command Prompt now change Directory to hadoop source folder then run the following command<br />
<br />
<pre class="lang-java prettyprint prettyprinted" style="background-color: #eff0f1; border: 0px; font-family: consolas, menlo, monaco, &quot;lucida console&quot;, &quot;liberation mono&quot;, &quot;dejavu sans mono&quot;, &quot;bitstream vera sans mono&quot;, &quot;courier new&quot;, monospace, sans-serif; font-size: 13px; margin-bottom: 1em; max-height: 600px; overflow: auto; padding: 5px; width: auto; word-wrap: normal;"><code style="border: 0px; font-family: Consolas, Menlo, Monaco, &quot;Lucida Console&quot;, &quot;Liberation Mono&quot;, &quot;DejaVu Sans Mono&quot;, &quot;Bitstream Vera Sans Mono&quot;, &quot;Courier New&quot;, monospace, sans-serif; margin: 0px; padding: 0px; white-space: inherit;"><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">mvn -e -X </span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">-</span><span class="typ" style="border: 0px; color: #2b91af; margin: 0px; padding: 0px;">Dmaven</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">.</span><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">compiler</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">.</span><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">fork</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">=</span><span class="kwd" style="border: 0px; color: #101094; margin: 0px; padding: 0px;">true</span><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;"> </span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">-</span><span class="typ" style="border: 0px; color: #2b91af; margin: 0px; padding: 0px;">Dmaven</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">.</span><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">compiler</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">.</span><span class="pln" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">executables</span><span class="pun" style="border: 0px; color: #303336; margin: 0px; padding: 0px;">=</span><span class="pun" style="border: 0px; margin: 0px; padding: 0px;"><span style="color: #7d2727;">%JAVA_HOME%\bin </span></span></code><span style="background-color: #f3f5f7; font-family: &quot;courier&quot; , monospace; font-size: 16px; white-space: pre-wrap;">package -Pdist,native-win -DskipTests -Dtar</span></pre>
<div>
<br />
If you face ant run plugin exception try&nbsp;<span style="font-family: &quot;courier&quot; , monospace;"><span style="background-color: #f3f5f7; white-space: pre-wrap;"><br /></span></span>
<span style="font-family: &quot;courier&quot; , monospace;"><span style="background-color: #f3f5f7; white-space: pre-wrap;">mvn antrun:run </span></span><br />
<span style="font-family: &quot;courier&quot; , monospace;"><span style="background-color: #f3f5f7; white-space: pre-wrap;"><br /></span></span>
<span style="font-family: &quot;courier&quot; , monospace;"><span style="background-color: #f3f5f7; white-space: pre-wrap;"><br /></span></span>
then run </div>
<div>
<br /></div>
<div>
<pre style="background-color: #f3f5f7; border: 1pt solid rgb(174, 189, 204); font-family: courier, monospace; font-size: 16px; padding: 5pt; white-space: pre-wrap; word-wrap: break-word;">mvn package -Pdist,native-win -DskipTests -Dtar</pre>
<span class="anchor" id="line-42"></span><span class="anchor" id="line-43"></span><br />
<b>STEP 14 : Extract Builds :~</b><br />
<span style="background-color: white; font-family: sans-serif; font-size: 16px;"><br /></span>
<span style="background-color: white; font-family: sans-serif; font-size: 16px;">A successful build generates a binary hadoop</span><em style="background-color: white; font-family: sans-serif; font-size: 16px;">.tar.gz</em><span style="background-color: white; font-family: sans-serif; font-size: 16px;">&nbsp;package in&nbsp; [source Root Directory]&nbsp;</span><em style="background-color: white; font-family: sans-serif; font-size: 16px;">hadoop-dist\target\</em><span style="background-color: white; font-family: sans-serif; font-size: 16px;">.&nbsp;</span><br />
<br />
<b>STEP 15 : Required&nbsp;</b><b style="background-color: white; font-family: Verdana, Arial, Helvetica; font-size: 12.8px;">7-Zip&nbsp;</b><b>&nbsp;to Extract Builds :~</b><br />
<b><br /></b>
<b><a href="http://www.7-zip.org/download.html">7-Zip [CLICK HERE]</a></b><br />
<br />
Install 7-Zip software in your system by default settings.</div>
<div>
<br /></div>
<div>
<b>STEP 16 : Extract Builds :~</b></div>
<div>
<br /></div>
<div>
<span style="background-color: white; font-family: sans-serif; font-size: 16px;">Extract the tar.gz file (e.g.</span><em style="background-color: white; font-family: sans-serif; font-size: 16px;">hadoop-x.x.x.tar.gz</em><span style="background-color: white; font-family: sans-serif; font-size: 16px;">) under&nbsp;</span><b><em style="background-color: white; font-family: sans-serif; font-size: 16px;">c:\deploy&nbsp;</em></b></div>
<div>
<b><span style="font-family: sans-serif;"><span style="background-color: white;"><i><br /></i></span></span></b></div>
<div>
<br /></div>
<div>
<div>
<br />
<b>STEP 17 : Class Not Found Issue :~</b><br />
<b><br /></b>
It may happen you have user name with white spaces so in that scenario I would suggest just create another user without any space.<br />
<br /></div>
<br />
<b>STEP 18 : Configure Command Prompt :~</b><br />
<br />
Now we have build hadoop from source but to run on IDE for debugging &amp; development we need our command prompt to be conigured with equivalent configuration of Windows SDK 7.1 Command Prompt so how can we do that.</div>
<div>
<br /></div>
<div>
Press Win+R type cmd on command prompt type <b>set &gt; command.txt</b></div>
<div>
Now open Windows SDK 7.1 Command Prompt and type <b>set &gt; wcommand.txt</b></div>
<div>
<br /></div>
<div>
Note:Check the files will be generated in current directory so please note down the directory location and collect those files.</div>
<div>
<br /></div>
<div>
<br /></div>
<div>
Then open this site&nbsp;<a href="https://www.diffchecker.com/">diffchecker.</a>&nbsp;diff tool to compare text differences between two text files.Or use any difference checker tool.</div>
<div>
<br /></div>
<div>
compare those file and set all the variable which is not available in <b>command.txt</b>&nbsp; Including path variable please set path variable with care if you made a mistake it may result on your OS. Better approach just copy paste.<br />
<br />
<div>
then run</div>
<div>
<br /></div>
<div>
<pre style="background-color: #f3f5f7; border: 1pt solid rgb(174, 189, 204); font-family: courier, monospace; font-size: 16px; padding: 5pt; white-space: pre-wrap; word-wrap: break-word;">mvn package -Pdist,native-win -DskipTests -Dtar</pre>
</div>
</div>
<div>
<br />
Hopefully you will compile successfully this time also as you did in Step 13.<br />
<br />
<b>STEP 19 : Configure Hadoop For Intellij :~</b><br />
<b><br /></b>
<br />
cd into your hadoop directory.<br />
Type the following command to create the Hadoop IntelliJ projects.<br />
<br />
<div>
<pre style="background-color: #f3f5f7; border: 1pt solid rgb(174, 189, 204); font-family: courier, monospace; font-size: 16px; padding: 5pt; white-space: pre-wrap; word-wrap: break-word;">mvn idea:idea</pre>
</div>
<div>
<br /></div>
Open IntelliJ.<br />
Select Open… from the top menu bar.<br />
Browse to the hadoop-main.ipr file in your hadoop directory.<br />
Open hadoop-main-ipr.</div>
<div>
<br /></div>
<div>
compile project again by this command may be you will face administrative privileges issue so while running your intellij instance just right click and run as administrator better approach use administrator account for development&nbsp;</div>
<div>
<br />
<pre style="background-color: #f3f5f7; border: 1pt solid rgb(174, 189, 204); font-family: courier, monospace; font-size: 16px; padding: 5pt; white-space: pre-wrap; word-wrap: break-word;">mvn package -Pdist,native-win -DskipTests -Dtar</pre>
<br />
Hopefully you will compile successfully this time also as you did in Step 19.<br />
<br />
<b>STEP 20 : Run Hadoop Examples :~</b><br />
<b><br /></b>
<br />
Select Run &gt; Edit Configurations…  from the top menu bar.<br />
Click on the ‘+‘ symbol in the upper left hand corner of the Run/Debug Configurations screen.<br />
Enter <b>org.apache.hadoop.util.Runjar</b> the main class.</div>
<div>
Enter<b>&nbsp;</b>path&nbsp;</div>
<div>
<pre style="background-color: #f3f5f7; border: 1pt solid rgb(174, 189, 204); font-family: courier, monospace; font-size: 16px; padding: 5pt; text-align: justify; white-space: pre-wrap; word-wrap: break-word;"><span style="background-color: #f2f2f2; font-family: &quot;monaco&quot; , &quot;consolas&quot; , &quot;bitstream vera sans mono&quot; , &quot;courier new&quot; , &quot;courier&quot; , monospace; font-size: 14px; white-space: pre;">(your hadoop foder)/hadoop-dist/target/hadoop-X.X.X-XXXXXX/share/</span><span style="background-color: #f2f2f2; font-family: &quot;monaco&quot; , &quot;consolas&quot; , &quot;bitstream vera sans mono&quot; , &quot;courier new&quot; , &quot;courier&quot; , monospace; font-size: 14px; white-space: pre;">hadoop/mapreduce/hadoop-mapreduce-examples-</span>-X.X.X-XXXXXX.jar <span style="color: red;"><b>pi 10 10</b></span></pre>
</div>
<div>
of the Hadoop examples jar the&nbsp;program arguments.</div>
<div>
<br /></div>
better approach search for hadoop-mapreduce-examples--X.X.X-XXXXXX.jar then right click open file location copy the path in explorer and append the jar file name accordingly then place the path with the text in red it is nothing but arguments pi is a class name.<br />
<br />
Class Path of module select hadoop-minicluster because it has<b> org.apache.hadoop.util.Runjar</b><br />
<br />
Click on the OK button. then Run/Debug Configurations screen.<br />
<div>
Hopefully you will compile successfully this time also with result 3.2<br />
<br />
<br />
<b>STEP 20 : We will develop word count project and have fun :~</b><br />
<b><span style="color: lime;">updates will be publish at next weekends, demands and questions are welocome.</span></b><br />
<b><br /></b>
Hopefully you will not face any issues while compiling the project &amp; configuring development environment If you still face some issue feel free to comments I have tried my best to describe all the steps.<br />
<br />
To Configure Hadoop you can follow&nbsp;<a href="https://wiki.apache.org/hadoop/Hadoop2OnWindows">Hadoop2OnWindows</a><br />
<br />
If you still face any issue feel free to connect with me Email: <a href="mailto:jaypatil.sonu@gmail.com">jaypatil.sonu@gmail.com</a></div>
<br />
For Regular updates follow up my blog <a href="https://apachehadoop3.blogspot.in"> apachehadoop3.blogspot.in</a><br />
</div>
