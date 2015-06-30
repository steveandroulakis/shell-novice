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
> * Introduction to full path
> * Explaining relative path and solidifying path concept
> * How to navigate in shell

Once you log in to your remote machine. The first time is always unfamiliar and confusing. I remember my first
logins to new account on a new server I run `ls` and said 'There are no files here` that becaue this is YOUR
new accoutn.. In this situation you really want to behave like a cat, who has been put in a new house.
That is it will walk around sniffing everywhere, going to every conner with a grumpy face, hatting you
and everyone around him. And so I want you to behave in exactly the same way. Look around the server explore
every conner so to speak and find your place. Once you've become familiar with your new environment you will
naturally start having dog like behaviour. That is open the door and straight to the couch! 

### Change Directory and List content

Lets start exploring from the start, from the ground floor up, from the roots of the tree from the __root__

_remember our  that we need to type commands in, execute them and read the reponce_

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

Here is the visual how it looks (upside down root tree, that's because we down under !)

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

### Bourne Again SHell or BASH for short

As at was mentioned previously `shell` is an intepreter. It is going to interpreate what we type for computer.
However we do need to type in specific language and it will be `BASH`, because it sound rought. 

- Havea you tried BASHing it..?
- Just give it a good BASH
- BASH quick anad dirty solution to everything

BASH as one specific language all Unix computers understand.

First two important aspects about CLI and BASH

1. Tab expand - have your little finger on the tab key all the time sorf of thing
  * one tab autocompletes
  * two tabs gives you ambigious options
2. Arrows key up - all commands stored in history. You can access them by scrolling through them one at a time

_Continue exploring but this time use tab expand_

### Introduce full path

When you hike you park your car and hike up. It is imposibble for you to go pass a place and not to
have in you path right..? This is fundamental idea about path. You don't have to stop and rest at every break
point, but if you have passed on your way up it was in your path. This is very simple.

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
I start at the root, nextt stop `mnt`, I don't want to stop at `mnt`, next stop at `shared`
~~~ {.bash}
/mnt/shared$ ls
~~~
~~~ {.output}
data RNAseq
~~~

It doesn't matter where you are as long as you follow __full path__ you are not going to get lost

### Why can I not start from where I left of..?

Exactly ! You don't always have to start at the root and traverse down. You can start __path__ from where you
are at.

- `pwd` print working directory, which just tells you where you are at 

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

- `~ == /home/john` tilda is a convinient short cut 
- `.`  is current directory 
- `..` is parent directory relative to where you are
- `cd ..` is to go up a directory

> ## Tilda {.callout}
> The reason you never see `/home/john/` behiind your prompt, is because it is replaced by tilda.
> Can you see the tilda behind your prompt now ..?

> ## Dot and Dot Dot {.callout}
> 
> `.` is current directory. It means definatelly from this, current directory
> e.g vim or ./vim will run two different programs

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

> ## Get grasp of path {.challenge}
>
> 1. get current directory 
> 2. go to the root
> 3. go to the `/mnt/shared/`
> 4. have a looks what there
> 5. visualy locate this course directory
> 6. go into the course directory 
> 7. go into relevant day
> 8. get your current directory
> 9. Green sticky up if you got there safely
>
> ## Get grasp of full and relative paths {.challenge}
>
> 1.  start from where you ended up from previous exercese
> 2.  go `/mnt/shared/` using full path
> 3.  look at the contetn
> 4.  get you current working directory
> 5.  go back to where you where using relative path
>
> ## Apreciate the dot and dot dot {.challenge}
>
> 1. stat from where you eneded up from precious exersice
> 2. go up one directory 
> 3. go up one more directory
> 4. get your current directory
> 5. go back, two directories deep
> 6. go back, two directories up, in one go, using dots only 
