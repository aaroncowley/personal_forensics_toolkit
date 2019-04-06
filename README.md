# Aaron Cowley's Personal Toolkit for Forensics

## Introduction
This toolkit is intended for my personal use and comes with a number of preconfigured tools that I like to have git clone-able for easy use.  Git also provides an easy way for me to ensure tools are updated and provides a reliable "cloud" solution for storing my documentation.

I wanted this toolkit to be:
* something that was easy to follow
* reflective of my personal forensics workflow and preferences
* A brain dump so I don't lose information on forensics tools in the future

## Contents

<!--ts-->
   * [Aaron Cowley's Personal Toolkit for Forensics](#aaron-cowleys-personal-toolkit-for-forensics)
      * [Introduction](#introduction)
      * [Contents](#contents)
      * [Host Analysis](#host-analysis)
         * [<a href="http://marketing.accessdata.com/ftkimager4.2.0" rel="nofollow">Ftk Imager</a>](#ftk-imager)
            * [Description](#description)
            * [Review](#review)
            * [Usage](#usage)
         * [<a href="https://sleuthkit.org/autopsy/docs/user-docs/4.5.0/installation_page.html" rel="nofollow">Autopsy</a>](#autopsy)
            * [Description](#description-1)
            * [Review](#review-1)
            * [Usage](#usage-1)
         * [<a href="https://support.microsoft.com/en-us/help/302542/how-to-diagnose-system-problems-with-event-viewer-in-microsoft-windows" rel="nofollow">Event Viewer</a>](#event-viewer)
            * [Description](#description-2)
            * [Review](#review-2)
            * [Usage](#usage-2)
      * [Network Analysis](#network-analysis)
         * [<a href="https://www.wireshark.org/" rel="nofollow">Wireshark</a>](#wireshark)
            * [Description](#description-3)
            * [Review](#review-3)
            * [Usage](#usage-3)
      * [Memory Analysis](#memory-analysis)
         * [<a href="https://github.com/volatilityfoundation/volatility">Volatility</a>](#volatility)
            * [Description](#description-4)
            * [Review](#review-4)
            * [Usage](#usage-4)
         * [<a href="https://github.com/504ensicsLabs/LiME">LiMe</a>](#lime)
            * [Description](#description-5)
            * [Review](#review-5)
            * [Usage](#usage-5)
      * [Malware Analysis](#malware-analysis)
         * [<a href="https://out7.hex-rays.com/files/idafree70_mac.tgz" rel="nofollow">Ida Pro</a>](#ida-pro)
            * [Description](#description-6)
            * [Review/Rating](#reviewrating)
            * [Usage](#usage-6)
         * [GNU Debugger (GDB)](#gnu-debugger-gdb)
            * [Description](#description-7)
            * [Review](#review-6)
            * [Usage](#usage-7)

<!-- Added by: s33r, at: Fri Apr  5 18:27:06 MDT 2019 -->

<!--te-->


## Host Analysis

### [Ftk Imager](http://marketing.accessdata.com/ftkimager4.2.0)
#### Description
FTK Imager is a part of the FTK Suite of tools and can be used for creating 
#### Review
It gets a 4/5 from me.  It is not the best program looks wise but it definitely does the job and its usage is well documented online.  
#### Usage
You start by adding an evidence item and then selecting the source evidence type.  If this is a hard drive then you select "logical drive". You select which drive you would like to create a dump of and the filename you would like the dump to be saved as.

### [Autopsy](https://sleuthkit.org/autopsy/docs/user-docs/4.5.0/installation_page.html)
#### Description
Autopsy is a fantastic GUI tool for analyzing the image dumps that you generate via FTK imager. 
#### Review
Windows version 4.5/5, Linux version 2/5.  The linux version is not quite as nice out of the box and lacks the ease of use that the windows version provides
#### Usage
You make a new case and when prompted to you simply just open the drive image that you would like to analyze.  It will then populate the sidebar with automatically parsed artifacts that are interesting for analysis such as users and temp folders.  From the sidebar you can also access the entire captured filesystem.

### [Event Viewer](https://support.microsoft.com/en-us/help/302542/how-to-diagnose-system-problems-with-event-viewer-in-microsoft-windows)
#### Description
Event Viewer is built into windows and is a fantastic way to get information a running windows machine.
#### Review
4/5, as with most microsoft products there is a great disparity between its beginner documentation and its advanced usage documentation. Overall its the best windows has for logging and can be leveraged to pinpoint events relevent to a forensics investigation.
#### Usage
The linked article gives an overview of most of the features that this program has and there is a lot of "hacks" you can find for each of these features with google.

## Network Analysis
### [Wireshark](https://www.wireshark.org/)
#### Description
Wireshark is the industry standard for packet capture and analysis in a GUI.  It can also be utilized for application protocol reverse engineering and analysis because of the tools it has for assembling files from pcaps and other awesome functionality.
#### Review
5/5, easy to use and is the best GUI tool for pcap analysis and creation. 
#### Usage
As it is a fully featured network analysis toolkit in its own, its documentation found at the linked source is definitely the best place to go once you have a specific use case in mind for it.

## Memory Analysis
### [Volatility](https://github.com/volatilityfoundation/volatility)
#### Description
Volatility is a memory capture analysis utility and uses "profiles" to target specific OS's during its analysis.  It can pull a lot from the process tree information and can be utilized to 
#### Review
3/5, it is one of the only tools in its class that can do what it does so it definitely deserves some credit.  The fact that it is written in python means that it is easily hackable and extendable for whatever modules you woould like to add to it.
#### Usage
``` bash
volatility --info
```
### [LiMe](https://github.com/504ensicsLabs/LiME)
#### Description
Lime is a loadable kernel module that enables live memory capture of any machine running the linux kernel.  It has support for capturing directly to the host or for sending the capture over the network.  
#### Review
5/5, It was easy to use and has usage information on github
#### Usage
Again I would refer to its github page to see a great example of its usage.  It has examples of using netcat to export the capture to a listening machine.


## Malware Analysis
### [Ida Pro](https://out7.hex-rays.com/files/idafree70_mac.tgz)
#### Description
Ida is hands down the best static analysis tool out there for machine code. It dissassembles raw binary into the instruction set of whatever architecture the binary was compiled for.  It provides this dissassembly to you in a clean "graph view" that uses jmp's to show logical pathways the chain of execution can be directed.  Static analysis can be daunting but the visualization that ida provides is best in class and makes reverse engineering significatnly easier.  If you pay for a full license of IDA you get its best in class decompiler that will attempt to turn the binary into equivalent C code which is much more readable than assembly.
#### Review/Rating
I give this tool a good / yes
#### Usage
Download and install your copy and then either drag binary to its shortcut icon or open it from within its file browser.  It will show some disassembly options to you. Unless you are dealing with a weird format or can see that the wrong option is highlighted in the menu.  You will then be taken to graph mode and can refer to the [ida cheat sheet](https://www.hex-rays.com/products/ida/support/freefiles/IDA_Pro_Shortcuts.pdf) for more specific operational advice relating to your task at hand.

### [GNU Debugger (GDB)](https://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)
#### Description
GNU debugger is one of the best tools for linux dynamic analysis.  It allows for breakpoints to be set and for arbitrary jumps in code to be made.  It can help debug logic of a binary and can be used to see how code runs step by step.
#### Review
By itself it is still very usable but lacks some modern niceties. It can be greatly improved by [gdb dashboard](https://github.com/cyrus-and/gdb-dashboard).  
#### Usage
just type:
``` bash
gdb <binary>
```
and the program will be opened in GDB. Typing "r" will run the program and "b * <memory address>" will set a breakpoint.  Using "disas <function name>" will print out the assembly code for that function.
