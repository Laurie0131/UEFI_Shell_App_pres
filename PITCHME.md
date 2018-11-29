---?image=assets/images/gitpitch-audience.jpg
@title[Platform Build Lab]
<br><br>
<span style="font-size:0.75em" >This slide deck has moved to:  https://gitpitch.com/tianocore-training/UEFI_Shell_App_Pres/master#/</span>
<br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Shell Application

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Shell Application

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Explain UEFI, the shell, and how they work together </span><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Define the shell components</span><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Use the shell  API  in a UEFI application</span> <br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell command Library</span> <br>
 @fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell scripts</span> 


---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Shell Overview Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Shell Overview</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Components of the UEFI Shell</span>
  

---?image=/assets/images/slides/Slide4.JPG
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell?]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

Where the Shell sits between the Platform H/w and the OS after all 
   console / devices initialized


What is a UEFI Shell?
	UEFI Application	
	Standardized Command Line Interface for pre-OS
	Sits directly on UEFI firmware (CIRCLE)
	Optimized for small footprint
	Supports rich pre-OS applications
	Standard scripting & API

Versus EFI Shell
	UEFI App
	Same characteristics
	No specification


USE THESE AS BULLETS

+++?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 02]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 03]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 04]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:


+++?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 06]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>

@snap[north-east span-40 fragment]
@css[ text-yellow](<br>&nbsp;)
![ItsAn](/assets/images/Its_an.png)
@snapend

@snap[east span-30 fragment]
@css[ text-white](<span style="font-size:01.2em"><br><br>&nbsp;<b>Extensive & Standardize Pre-OS UEFI Application</b></span>)
@snapend

Note:

Where the Shell sits between the Platform H/w and the OS after all 
   console / devices initialized


What is a UEFI Shell?
	UEFI Application	
	Standardized Command Line Interface for pre-OS
	Sits directly on UEFI firmware (CIRCLE)
	Optimized for small footprint
	Supports rich pre-OS applications
	Standard scripting & API

Versus EFI Shell
	UEFI App
	Same characteristics
	No specification


USE THESE AS BULLETS



---?image=/assets/images/slides/Slide11_1.JPG
@title[What is a UEFI Shell?]
### <p align="right"><span class="gold" >UEFI Shell Specification V. 2.2</span></p>
<p align="right"><span style="font-size:0.6em" > <a href="http://www.uefi.org/specsandtesttools"> http://www.uefi.org/specsandtesttools</a></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="font-size:0.7em" >UEFI Shell v2.0 specification first released 2008 – Latest V2.2 Jan 2016 </span>

Note:

---
@title[UEFI Shell Elements]
### <p align="right"><span class="gold" >UEFI Shell Elements</span></p>



@snap[west span-45  fragment]
@box[bg-blue text-white waved ](<span style="font-size:01.5em" ><font face="Arial">Small Size Profiles</font></span> )
@snapend

@snap[east span-45  fragment]
@box[bg-yellow text-blue waved ](<span style="font-size:01.5em" ><font face="Arial">Shell Commands</font> </span> )
@snapend

@snap[south-west span-45  fragment]
@box[bg-purple text-white waved ](<span style="font-size:01.5em" ><font face="Arial">New Shell API<br>&nbsp;</font> </span><br> )
@snapend

@snap[south-east span-45  fragment]
@box[bg-green text-white waved  ](<span style="font-size:01.5em" ><font face="Arial">Enhanced Scripting</font> </span><br>)
@snapend

Note:

1)Small Size Profiles
Took the UEFI Shell that Intel has been working on as a starting point 4 areas for size

Levels of support
Different levels of support for different usage scenarios and space constraints:
Level 0: No Command-line Interface (CLI). No shell commands. Only shell API.
Level 1: Adds basic scripting support
Level 2: Adds basic commands (cd, cp, mv)
Level 3: Adds interactive CLI
Shell support level can be detected using an environment variable.
Beyond level 3, additional command “profiles” are defined for debug, networking and driver support

2) Shell Commands

Standardized existing usage
Updated for UEFI 2.1+
Standardized argument usage and output
Example some of the grep commands are standardized

3) New Shell API
Smaller executable size – put common functionally back into the shell
Expose previously hidden shell
  capabilities – the shell does some really cool things
– Example to change the current directory (CD) it did not exposes this and no one else could take advantage of this unless they were linked right into it

Execution break support – control “C”

4) Enhanced Scripting
Compatible with existing scripts
Added input redirection & piping
Enhanced if command
   example added capability to use shell without a HD or RAM Drive present. – may not have a HD for Manufacturing 
May not have a Hard drive input output to environment variables



UEFI Advantages = UEFI Shell Advantages
- Flat memory model
- Robust, extensible architecture
- File system, Network, Keyboard, Mouse

- UEFI Works = UEFI Shell Works
- No additional requirements to run

- Write Once/Run Anywhere For Pre-OS
- With standard API/commands = applications from different ISVs work on any platform (Ex: UEFI SCT)





---
@title[Small Size Profiles]

@snap[midpoint span-65  ]
@box[bg-blue text-white waved ](<span style="font-size:02.5em" ><font face="Arial">Small Size Profiles</font></span> )
@snapend


Note:
## Small Size Profiles

Took the UEFI Shell that Intel has been working on as a starting point 4 areas for size

Levels of support
Different levels of support for different usage scenarios and space constraints:

Level 0: No Command-line Interface (CLI). No shell commands. Only shell API.

Level 1: Adds basic scripting support

Level 2: Adds basic commands (cd, cp, mv)

Level 3: Adds interactive CLI

Shell support level can be detected using an environment variable.

Beyond level 3, additional command “profiles” are defined for debug, networking and driver support

---
@title[Small Size Profiles detail]
### <p align="right"><span class="gold" >Small Size Profiles</span></p>
<table>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:70%"><b>Level&nbsp;/&nbsp;Profile&nbsp;</b></p></td>
		<td bgcolor="#4487f2"><p style="line-height:70%"><b>Commands&nbsp;</b></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2" height=".025"><span style="font-size:0.85em"><b>Level 0&nbsp;</b></span></td>
		<td bgcolor="#D7D7D7" height=".025"><span style="font-size:0.65em"><font color="black">Shell API <b>Only</b> &nbsp; </font></span></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2" height=".025"><p style="line-height:20%"><span style="font-size:0.85em"><b>Level 1&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7" height=".025"><p style="line-height:20%"><span style="font-size:0.65em"><font color="black">Basic scripting support &nbsp;</font></span> </p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>Level 2&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.65em"><font color="black">File Support, cmds(cd, cp, mv) &nbsp; </font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>Level 3&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.65em"><font color="black"> Adds interactive CLI + Profiles&nbsp; </font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>UEFI Debug Profile&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.55em"><font color="#4487f2"> bcfg, comp, dblk, dmem, dmpstore, echo, edit, &nbsp; </font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>UEFI Network Profile&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.55em"><font color="#4487f2">ipconfig, ping &nbsp; </font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>UEFI Driver Profile&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.55em"><font color="#4487f2"> drvdiag, openinfo, reconnect, load, unload&nbsp;</font></span> </p></td>
	</tr>

</table>

@snap[south-west  fragment ]
@box[bg-purple text-white rounded ](<span style="font-size:01.0em" ><font face="Arial"><b>Choose the shell that best matches your product needs </b></font></span> )
@snapend

Note:
## Small Size Profiles

Different levels; defining a platform confined in a space – go with a smaller profile.  

Took the same shell commands that have always been there and standardized them

Some were never used so were deprecated 

Level 0: provide shell API and that is about it

Level 1: Provide basic scripting support – but not any command line interface so if you want any support then you need to provide the disk itself

Level 2: basic file manipulation commands

Level 3:CLI

Grouped the rest into 3 groups
- UEFI Debug
- Network
- Driver
- also install

#### KEY POINT:  Choose the shell that best matches your product needs


---
@title[Shell Commands]


@snap[midpoint span-65  ]
@box[bg-yellow text-blue waved ](<span style="font-size:02.5em" ><font face="Arial">Shell Commands</font></span> )
@snapend

Note:

### Shell Commands


---?image=/assets/images/slides/Slide25.JPG
@title[Shell Commands detail]
### <p align="right"><span class="gold" >Shell Commands</span></p>

Note:
### Shell Commands

List of all shell commands from the shell prompt by doing help -b 

Only the commands built with the currenet shell being executed will also be listed in the Help list



---
@title[New Shell API]

@snap[midpoint span-65  ]
@box[bg-purple text-white waved ](<span style="font-size:02.5em" ><font face="Arial">New Shell API<br>&nbsp;</font></span> )
@snapend

Note:

### New Shell API
- Application interface

---
@title[New Shell API detail]
### <p align="right"><span class="gold" >New Shell API</span></p>
<p align="center"><span style="font-size:01.1em; background-color:#643885">&nbsp;&nbsp;&nbsp;<span style="font-size:0.85em">`EFI_SHELL_PROTOCOL`</span>&nbsp;&nbsp;&nbsp;</span></p>

<table>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:70%"><b>Group&nbsp;</b></p></td>
		<td bgcolor="#4487f2"><p style="line-height:70%"><b>Functions&nbsp;</b></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2" height=".025"><span style="font-size:0.85em"><b>File Manipulation &nbsp;</b></span></td>
		<td bgcolor="#D7D7D7" height=".025"><span style="font-size:0.5em"><font color="black">`OpenFileByName(), WriteFile(),` etc. . . &nbsp; </font></span></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2" height=".025"><p style="line-height:80%"><span style="font-size:0.85em"><b>Mapping, Alias & Environmental Variables&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7" height=".025"><p style="line-height:50%"><span style="font-size:0.5em"><font color="black">`GetMapFromDevicePath(), GetFilePathFromDevicePath()`, etc . . .&nbsp;</font></span> </p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:80%"><span style="font-size:0.85em"><b>Launch Application or Script&nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:50%"><span style="font-size:0.5em"><font color="black">`Execute(), BatchIsActive(), IsRootShell()`,etc . . . &nbsp; </font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#4487f2"><p style="line-height:20%"><span style="font-size:0.85em"><b>Miscellaneous &nbsp;</b></span></p></td>
		<td bgcolor="#D7D7D7"><p style="line-height:20%"><span style="font-size:0.5em"><font color="black">`GetPageBreak(), EnablePageBreak()` ,etc . . . &nbsp; </font></span></p></td>
	</tr>

</table>

@snap[south-west  fragment ]
@box[bg-purple text-white rounded ](<span style="font-size:01.0em" ><font face="Arial"><b>`EFI_SHELL_PROTOCOL` is installed on each application image handle </b></font></span> )
@snapend


Note:
### New Shell API

This just to give an idea of the over all groups

#### KEY POINT: EFI_SHELL_PROTOCOL is installed on each application image handle

CreateFile, DeleteFile, ReadFile, WriteFile, DeleteFileByName, CloseFile, FindFiles, FindFilesInDir, GetFilePosition, SetFilePosition, GetFileInfo, SetFileInfo, FreeFileList, OpenFileByName, OpenFileList, OpenRoot, OpenRootByHandle, GetFileSize, RemoveDupInFileList


GetMapFromDevicePath, GetFilePathFromDevicePath, GetDevicePathFromFilePath, GetDevicePathFromMap, SetMap, SetAlias, GetEnv, SetEnv, GetCurDir, SetCurDir


Execute, BatchIsActive, IsRootShell


GetPageBreak, EnablePageBreak, DisablePageBreak, GetHelpText, GetDeviceName


Mapping – FS0 instead of full 

---?image=/assets/images/slides/Slide31.JPG
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries]
<p align="right"><span style="font-size:01.1em"><font color="#e49436">ShellPkg Main Libraries</font></span></p>


Note:

There are three main libraries used by almost all shell commands 


- ShellLib 
  -  Used by both commands and applications. Provides easy access to Shell Protocols, File I/O, and printing to the user. 



- HandleParsingLib
   - Used by both commands and applications. Provides easy access for manipulating handles. This means things like 
conversion the handle to and from the handle index; the index is the 2 digit hex identifier of the handle seen by the user 
sorting of handles to determine parent controllers, child controllers, or which driver controls a given controller 

- ShellCommandLib 
  - fully usable only when linked within the shell binary and therefore only by internal shell commands. This provides extra features for internal commands.





+++?image=/assets/images/slides/Slide32.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries 02]
<p align="right"><span style="font-size:01.1em"><font color="#e49436">ShellPkg Main Libraries</font></span></p>

Note: 

+++?image=/assets/images/slides/Slide33.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries 03]
<p align="right"><span style="font-size:01.1em"><font color="#e49436">ShellPkg Main Libraries</font></span></p>

Note: 


There are three main libraries used by almost all shell commands 


- ShellLib 
  -  Used by both commands and applications. Provides easy access to Shell Protocols, File I/O, and printing to the user. 



- HandleParsingLib
   - Used by both commands and applications. Provides easy access for manipulating handles. This means things like 
conversion the handle to and from the handle index; the index is the 2 digit hex identifier of the handle seen by the user 
sorting of handles to determine parent controllers, child controllers, or which driver controls a given controller 

- ShellCommandLib 
  - fully usable only when linked within the shell binary and therefore only by internal shell commands. This provides extra features for internal commands.



---
@title[EDK II ShellPkg]
<p align="right"><span style="font-size:01.1em"><font color="#e49436"><b>EDK II ShellPkg</b></font></span></p>


@snap[north-west span-45  fragment]
@css[text-yellow](<br> <br>&nbsp;)
@box[bg-blue text-white rounded ](<span style="font-size:01.5em" ><font face="Arial">Support binary portability</font></span> )
@snapend

@snap[north-east span-45  fragment]
@css[text-yellow](<br> <br>&nbsp;)
@box[bg-green text-white rounded ](<span style="font-size:01.5em" ><font face="Arial">Shell protocols<br>&nbsp;</font> </span> )
@snapend

@snap[south span-55  fragment]
@box[bg-purple text-white rounded ](<span style="font-size:01.5em" ><font face="Arial">Shell parameters&nbsp;</font> </span><span style="font-size:0.65em" ><br>&num;`include` &lt;`Library/ShellLib.h`&gt;<br>`gEfiShellParametersProtocol`<br>`gEfiShellProtocol` </span> )

@snapend


Note: 


- EDK II native library for shell applications 
  - ShellPkg on Open Source, Repository: https://github.com/tianocore/edk2/tree/master/ShellPkg
- Supports binary portability between EFI Shell 1.0 and UEFI 2.0 shell
- Shell protocols: Calls into UEFI (default) or EFI for functionality
- Shell parameters
  - Handles parameter parsing for flag, value, and position command-line parameters
  - EDK II UEFI Shell 2.0 Library globals in Shell applications
    - #Include <Library/ShellLib.h>
    - gEfiShellParametersProtocol  
    - gEfiShellProtocol


---
@title[Shell Call example]
<p align="right"><span style="font-size:01.1em"><font color="#e49436"><b>Shell Call Example</b></font></span></p>

```C++
// use UEFI shell 2.x interface
//
 if (gEfiShellParametersProtocol != NULL) {
        Argc = gEfiShellParametersProtocol->Argc;
        Argv = gEfiShellParametersProtocol->Argv;
//Create the file with Argv[1] with 
//                 read/write/create
       Status = gEfiShellProtocol->OpenFileByName
          (Argv[1], &Handle, 
           EFI_FILE_MODE_READ | 
           EFI_FILE_MODE_WRITE | 
           EFI_FILE_MODE_CREATE);

// . . .
// Write the buffer data to the file
	Status = gEfiShellProtocol->WriteFile( Handle,     
           (UINTN *)&BufferSize, (void *)Buffer);
```

@[4-5](Parameters Argc and Argv from the command line passed to YOUR shell application)
@[6-8](Create the file with Argv string using the Shell <i>Open File by name</i> function)
@[15-17](After your application is finished with it's task, write the contains using the Shell handle)



Note:

---
@title[Enhanced Scripting]


@snap[midpoint span-65  ]
@box[bg-green text-white waved ](<span style="font-size:02.5em" ><font face="Arial">Enhanced Scripting</font></span> )
@snapend


Note: 


---
@title[Enhanced Scripting details]
<br>
<p align="center"><span style="font-size:01.1em"><font color="#e49436"><b>Shell Enhanced Scripting</b></font></span></p>
<br>
 @fa[circle gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Contains <b>.nsh</b> extention</span> <br>
 @fa[circle gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;"`Startup.nsh`" runs first</span> <br>
 @fa[circle gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Supports:</span><br>
 <span style="font-size:0.8em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Command-line arguments</span><br>
 <span style="font-size:0.8em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Standard script commands</span> <br>
 <span style="font-size:0.8em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Input & output redirection & pipes</span><br>
 

Note: 
- Text files with .nsh extension are shell scripts
- Supports command-line arguments using positional parameters %0 - %9 and shift.
- Supports standard script commands 
  - if/else/endif
  - goto
  - for/endfor
  - echo
  - exit
- Supports input & output redirection & pipes.
- Can also redirect to/from environment variables!


- Startup.nsh – First Shell script can be on any FS system. the first script run by the UEFI Shell and it can be run from any removable device


---?image=/assets/images/slides/Slide43.JPG
@title[Shell Scripts (Benefits)]
<br>
<p align="center"><span style="font-size:01.1em"><font color="#e49436"><b>Shell Scripts (Benefits)</b></font></span></p>

Note: 

The UEFI Shell can execute commands from a file, which is called a batch script file (.nsh files). 


### Benefits: These files allow users to simplify routine or repetitive tasks. 
- Perform basic flow control. 
- Allow branching and looping in a script. 
- Allow users to control input and output and call other batch programs (known as script nesting). 



---
@title[Script Detects Shell Capabilities]
<br>
<p align="center"><span style="font-size:01.1em"><font color="#e49436">Script that Detects Shell Capabilities</font></span></p>
<br>
```shell
# check if Shell supports level 3 commands
 # Exit on error
 if %uefishellsupport% ult 3 then
   echo Must support UEFI Shell, Level 3
   exit /b 2
 endif

 # check that Shell supports Debug1 profile.
 if profiles(Debug1)then
   echo UEFI Shell supports Debug1 profile
 endif
```

@[2-4](Check if Shell supports level 3 commands - That means a Command Line Interface (CLI)
@[9-10](Check that Shell supports Debug1 profile.)



Note:

Walk through the code
- "ult" is <u>u</u>nsigned <u>l</u>ess <u>t</u>han)

---
@title[UEFI Shell Script Example]
<br>
<p align="center"><span class="gold" >UEFI Shell Script Example</span></p>
<br>
<span style="font-size:0.7em"><font color="yellow">Script1.nsh</font></span>
```shell
# Simple UEFI Shell script file
echo  -off
script2.nsh
if exist %cwd%Mytime.log then
     type Mytime.log
endif
echo "%HThank you.” “%VByeBye:) %N"
```
<br>
<span style="font-size:0.7em"><font color="yellow">Script2.nsh</font></span>
```shell
# Show nested scripts
time > Mytime.log
for %a run (3 1 -1)
    echo %a counting down
endfor
```

Note:
walk through the script calling the second script
- if
- for loop
  - %a counting down...

---?image=/assets/images/slides/Slide47.JPG
@title[Documentation for EDK II ShellPkg]
<p align="center"><span style="font-size:01.1em"><font color="#e49436">Documentation for EDK II ShellPkg</font></span></p>
<br>
<br>
<br>
 @fa[book gp-bullet-ltgreen]<span style="font-size:0.8em">&nbsp;&nbsp;Documenation Link:<br> &nbsp;&nbsp;&nbsp;&nbsp;<a href="https://github.com/tianocore/tianocore.github.io/wiki/ShellPkg">wiki Shell Package</a></span>


Note:

UEFI Shell Documentation updated in the Engineering Resources section


---
@title[UEFI Shell 2.2 Vs. EFI Shell 1.0]
<br>
<p align="center"><span style="font-size:01.1em"><font color="#e49436">UEFI Shell 2.2   &nbsp;&nbsp;Vs.   &nbsp;&nbsp;EFI Shell 1.0</font></span></p>
<br>
@fa[circle gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell 2.x&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- EFI_SHELL_PARAMETERS_PROTOCOL</span><br>
@fa[circle gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;EFI Shell 1.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- EFI_SHELL_INTERFACE</span>             
<br>
```C
//
#include <Protocol/EfiShellInterface.h> //GUID protocol for EFI Shell 1.0
#include <Protocol/ShellParameters.h>   //GUID protocol for UEFI Shell 2.x

// . . .

 EFI_SHELL_PARAMETERS_PROTOCOL    *mEfiShellParametersProtocol;
 EFI_SHELL_INTERFACE              *mEfiShellInterface;
//
```

<span style="font-size:0.6em">&nbsp;&nbsp;See example C file: <a href="https://github.com/tianocore-training/UEFI_Shell_App_pres/tree/master/Sample/MyShellApp/MyShellApp.c">MyShellApp.c </a></span>

Note:

Protocol GUID will be for either Shell 1.0 or Shell 2.0

This slide shows how to access UEFI Shell 2.0 Versus EFI Shell 1.0
There are 2 different GUIDs 

Simply try to open one GUID verse the other to see which Shell is currently in use.

Notice the lower case "g" is for global - this notation is used throughout EDK II code

Lower case "m" means global for "my" Application, driver, etc


+++?code=Sample/MyShellApp/MyShellApp.c&lang=c++&title=UEFI Shell 2.2 Vs. EFI Shell 1.0

@[69-79](Check input parameters from command line using UEFI Shell 2.2 - notice <b>gEfiShellParametersProtocolGuid</b>)
@[81-82](Protocol GUID was found, so assign Argc & Argv from Shell 2.2 protocol)
@[85-92](Else, check if EFI Shell 1.0 - notice <b>gEfiShellInterfaceGuid</b> , Lower case "g")
@[96-97](Protocol GUID was found, so assign Argc & Argv from Shell 1.0 protocol)
@[99-100](Else, Error out of application  )

Note:

This slide shows how to access UEFI Shell 2.0 Versus EFI Shell 1.0
There are 2 different GUIDs 
Simply try to open one GUID verse the other to see which Shell is currently in use.

Notice the lower case "g" is for global - this notation is used throughout EDK II code

Lower case "m" means global for "my" Application, driver, etc





---?image=/assets/images/slides/Slide52.JPG
@title[Legacy vs. UEFI ]

### <p align="right"><span class="gold" >Legacy vs. UEFI</span></p>

Note:
The UEFI SHELL is an UEFI application that allows you to interface with the UEFI environment prior to the time the OS is loaded. Once the OS starts loading, the UEFI environment is no longer accessible through the Shell. 
The UEFI Shell supports a command line interface similar to DOS or Unix.  In fact a lot of the same commands exist in the UEFI shell that are in DOS and forms of Linux.



---?image=/assets/images/slides/Slide54.JPG
@title[Shell Usage ]
### <p align="right"><span class="gold" >Shell Usage</span></p>

Note:
The shell is where preboot programs  will execute.  For example, manufacturing test applications with the rich pre boot environment there is no need to run / execute an operating system
Typical environment that an EFI application might need to execute pre-operating system functions:

- Execute preboot programs
- update programs
- disk utilities
- tests(hwd and soft)
- operating system installation – Configuration utility of a Driver
- Diagnostics
- Platform Testing & Driver Diagnostics

- Move files around between different devices (hard disk, CD/DVD, USB flash drives, …)
- The shell is where files can be moved around just as in DOS or Unix.

- Load a preboot UEFI driver in the system (.efi)
- The shell is where preboot EFI drivers are loaded in the system such as a lan stack tcpip drivers, update old drivers in flash, new drivers for plugin cards etc.
 

- LAN stack & TCP/IP drivers
- Update old drivers in flash
- New drivers for plug-in cards

---?image=/assets/images/slides/Slide56.JPG
@title[Accessing the Shell]
### <p align="right"><span class="gold" >Accessing the Shell</span></p>

Note:
Boot UEFI Shell from FAT/FAT32 partition:
1.  Special boot file located under /EFI/boot/ directory:
    - BOOTia32.efi (IA32) or BOOTx64.efi (x64) or other NON IA



---?image=/assets/images/slides/Slide58.JPG
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>


Note:
Can manipulate only UEFI system partitions (FAT/FAT32) where boot loader and UEFI applications are located:

An example of the EFI File system is best seen using the MAP Command that will display the mappings in nvram between block devices .  
The EFI shell is replacing what is to the left of the “:” with the device path to the right of the “:”


- Blkxx designates a raw block device 
- Such as a disk controller, floppy controller etc.
- FSy designates that a block device has a fat file system on that device.
- The Map command displays all the raw block devices in the system and the FAT file systems mounted and usable.
- After the colon is the device path or physical location of where that device or file system is located.


- Lets try the Map Command on your classroom systems.


+++?image=/assets/images/slides/Slide60.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 02]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:


+++?image=/assets/images/slides/Slide61.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 03]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide62.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 04]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide63.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 05]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide64.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 06]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide65.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 07]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:


+++?image=/assets/images/slides/Slide66.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 08]
<br>
<p align="right"><span class="gold" >UEFI File System & Device Path</span></p>

Note:
Can manipulate only UEFI system partitions (FAT/FAT32) where boot loader and UEFI applications are located:

An example of the EFI File system is best seen using the MAP Command that will display the mappings in nvram between block devices .  
The EFI shell is replacing what is to the left of the “:” with the device path to the right of the “:”


- Blkxx designates a raw block device 
- Such as a disk controller, floppy controller etc.
- FSy designates that a block device has a fat file system on that device.
- The Map command displays all the raw block devices in the system and the FAT file systems mounted and usable.
- After the colon is the device path or physical location of where that device or file system is located.


- Lets try the Map Command on your classroom systems.


---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>
<br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Explain UEFI, the shell, and how they work together </span><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Define the shell components</span><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Use the shell  API  in a UEFI application</span> <br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell command Library</span> <br>
 @fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell scripts</span> 

 

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG =10x) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2018, Intel Corporation. All rights reserved.
**/

```
