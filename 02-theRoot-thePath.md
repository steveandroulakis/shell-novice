---
layout: page
title: The Unix Shell
subtitle: Files and Directories
minutes: 30
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

_remember our that we need to type commands in, execute them and read the reponce_

~~~ {.bash}
$ cd /
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
$ cd /mnt/shared/
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
$ pwd
~~~
~~~ {.output}
/home/john
~~~
~~~ {.bash}
$ cd /mnt 
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

### Appreciate the dot and dot dot

- `.` is current directory. It means definatelly from this, current directory
e.g vim or ./vim will run two different programs


The special directory `..` doesn't usually show up when we run `ls`.
If we want to display it, we can give `ls` the `-a` flag:

> ## Relative path resolution {.challenge}
>
> If `pwd` displays `/Users/thing`, what will `ls ../backup` display?
>
> 1.  `../backup: No such file or directory`
> 2.  `2012-12-01 2013-01-08 2013-01-27`
> 3.  `2012-12-01/ 2013-01-08/ 2013-01-27/`
> 4.  `original pnas_final pnas_sub`

> ## `ls` reading comprehension {.challenge}
>
> If `pwd` displays `/Users/backup`,
> and `-r` tells `ls` to display things in reverse order,
> what command will display:
>
> ~~~
> pnas-sub/ pnas-final/ original/
> ~~~
>
> 1.  `ls pwd`
> 2.  `ls -r -F`
> 3.  `ls -r -F /Users/backup`
> 4.  Either \#2 or \#3 above, but not \#1.

> ## Default `cd` action {.challenge}
>
> What does the command `cd` without a directory name do?
>
> 1.  It has no effect.
> 2.  It changes the working directory to `/`.
> 3.  It changes the working directory to the user's home directory.
> 4.  It produces an error message.

> ## Exploring more `ls` arguments {.challenge}
>
> What does the command `ls` do when used with the `-s` and `-h`
> arguments
