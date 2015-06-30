---
layout: page
title: The Unix Shell
subtitle: The root and The path
minutes: 25-30
---
> ## Learning Objectives {.objectives}
>
> * First two commands and cat-dog behaviour
> * Introduction to BASH
> * Introduction to the full path
> * Explaining relative path and solidifying the path concept
> * How to navigate in shell

Once you log in to your remote machine. The first time is always unfamiliar and confusing. I remember my first
logins to new account on a new server. I ran `ls` and said 'There are no files here` that because this is YOUR fresh and new account.. In this situation you really want to behave like a cat, who has been put in a new house.
That is it will likely walk around sniffing everywhere, exploring every corner with a grumpy face. And so I want you to behave in exactly the same way. Look around the server. Explore
every corner, so to speak, and learn what places are yours. Once you've become familiar with your new environment you will
naturally start having dog like behaviour. That is open the door and straight to the couch! 

### Change Directory and List content

Lets start exploring from the start, from the ground floor up, from the roots of the tree... __root__

_remember that we need to type commands in, execute them and read the response_

~~~ {.bash}
~$ cd /
~~~
~~~ {.output}
/$
~~~
~~~ {.bash}
/$ ls
~~~
~~~ {.output}
bin  boot  dev  etc  home  initrd.img  initrd.img.old  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin
srv  sys  tmp  usr  var  vmlinuz  vmlinuz.old
~~~

Here is the visually how it looks (an upside down root tree, because we're down under :) !)

![The File System](fig/filesystem.svg)

Inside root all other directories with several other directories:
- `bin` (which is where some built-in programs are stored),
- `data` (for miscellaneous data files),
- `Users` (where users' personal directories are located),
- `tmp` (for temporary files that don't need to be stored long-term),
and so on:

_Keep exploring_

~~~ {.bash}
/$ cd /mnt/
~~~
~~~ {.bash}
/mnt$ ls
~~~
~~~ {.output}
lost+found shared
~~~
~~~ {.bash}
/mnt$ cd /shared/
~~~
~~~ {.bash}
/mnt/shared$ ls
~~~
~~~ {.output}
data RNAseq
~~~

Note two things here:

1. how text increases and decreases on the left hand side as you move around
   _Reflects the path_
2. that no matter how deep in the directories you are, you can always type `cd /` and get to the root

### Bourne Again Shell or BASH for short

As at was mentioned previously `shell` is an intepreter. It is going to interpreate what we type for computer.
However we do need to type in specific language and it will be `BASH`.. 

- Havea you tried BASHing it..?
- Just give it a good BASH
- BASH quick and dirty solution to everything

BASH is one specific language almost all Unix computers understand.

The first two important aspects to know about the CLI and BASH

1. Tab expand - pretty soon you'll have your little finger on the tab key all the time..
  * one tab autocompletes
  * two tabs gives you ambigious options
2. Arrow keys up - all commands stored in history. You can access them by scrolling through them one at a time

_Continue exploring but this time use tab expand_

### Introducing the 'full' path

The path is like hiking. You park your car, that's the `root` or top of your path. As you keep going down various connected paths, you can always reverse your actions and change course. The full path describes the steps you need to get from your car to the particular place you're standing. eg. `/carpark/naturetrail/waterfall`

> ## Path {.callout}
>
> Notice that there are two meanings for the `/` character.
> When it appears at the front of a file or directory name,
> it refers to the root directory. When it appears *inside* a name,
> it's just a separator.

The leading `/` tells the computer to follow the path from the root of the file system,
so it always refers to exactly one directory, no matter where we are when we run the command.

~~~ {.bash}
~$ cd /mnt/shared/
~~~
I start at the root, next stop `mnt`, I don't want to stop at `mnt`, next stop at `shared`
~~~ {.bash}
/mnt/shared$ ls
~~~
~~~ {.output}
data RNAseq
~~~

It doesn't matter where you are as long as you follow __full path__ you are not going to get lost

### Why can I not start from where I left off..?

Exactly ! You don't always have to start at the root and traverse down. You can refer to other paths from where you
are currently at.

- `pwd` print working directory, which just tells you where you are on the file system

~~~ {.bash}
~$ pwd
~~~
~~~ {.output}
/home/john
~~~
~~~ {.bash}
~$ cd /mnt 
~~~
~~~ {.output}
lost+found shared
~~~
~~~ {.bash}
/mnt$ cd shared/RNAseq
~~~
~~~ {.bash}
/mnt/shared/RNAseq$ pwd
~~~
~~~ {.output}
mapping  raw_data  ref_data
~~~

### Shell navigation in general

- `~ == /home/john` tilde is a convinient short cut to your home directory (see below)
- `.`  is your current directory 
- `..` is parent directory relative to where you are
- eg. `cd ..` is to go up a directory (to its parent)

### Your 'home' directory.

While you may be able to look around the root (eg. '/') path on a system, you probably won't be able to modify any information at that level.

This is because:
 * The root contains many important parts that make your computer run properly
 * These parts affect every user account on the computer and so its important to have them reliable for all
 * If everyone could modify files from the root downwards, it would be relatively easy to accidentally break the system for all users, including yourself.

Think of the system root as containing a car's engine area (under the bonnet, or hood). You should know what you're doing if you're messing about there, and what you do will affect all passengers of the car.

Because of this, users on systems have _home directories_.  This may look like `/home/john` (eg. by default on many Linux systems) or `/Users/john` on Macs. The home directory is like a passenger seat of a car. You can put your seatbelt on. You can make your window go up or down. You can help yourself, but without adversely affecting anybody else.

When you log into a system (by `ssh` or just opening a terminal on your computer, you start by default in your home directory).

Home directories are parts of a system that only you should be able to create and modify data within. Your tools should output information into there, with the peace of mind that you have full control. You can even install tools here, just for yourself to use.

A shortcut for _my home directory_ is the tilde character: `~`. For example, in the shell: `cd ~/` means 'take me to my home directory'. This becomes really useful as we go along.

> ## Tilde {.callout}
> The reason you never see `/home/john/` behiind your prompt, is because it is replaced by tilde.
> Can you see the tilde behind your prompt now ..?

> ## Dot and Dot Dot {.callout}
> 
> `.` is your current directory. It means 'from this, current directory'
> e.g cat would run the program `cat` that reads the contents of your files, but `./cat` would try and run a program called `cat` living in the current directory you're in.

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/home/john
~~~
~~~ {.bash}
/home/john$ cd ..
~~~
~~~ {.output}
/home/
~~~

> ## Get grasp of the path {.challenge}
>
> 1. show your current directory name on-screen
> 2. go to the root
> 3. go to the `/mnt/shared/` directory
> 4. have a look what's in there
> 5. visually locate this course directory
> 6. try and find the RNA Seq course's mapping directory
> 7. Green sticky up if you got there safely


> ## Get a grasp of full and relative paths {.challenge}
>
> 1.  start from any path
> 2.  go to `/mnt/shared/` using its full path name
> 3.  look at the contents
> 4.  show your current working directory (path)
> 5.  go back to your home directory


> ## Appreciate the dot and dot dot {.challenge}
>
> 1. start in your home directory
> 2. go up one directory 
> 3. go up one more directory
> 4. show your current working directory
> 5. go back to your home directory
> 6. go back two directories up, in one command.. using dots only 
