---
layout: page
title: The Unix Shell
subtitle: Creating Things
minutes: 25-30
---
> ## Learning Objectives {.objectives}
>
> * Explain general syntax of the shell
> * Explain commands options and arguments
> * Just commands

### Shell reads commands. Commands read arguments

The way CLI works is that you tell it what needs to be done i.e here is command execute it. And it will do
exactly that. But command itself demands more information i.e what do you want me to work with ..? 

- some programs can only run by themselvs e.g `date`, `cal` 
- some programs can only run with give arguments e.g `mv`, `cp`
- other programs can run either way, with or without parameters e.g `cd`, `ls`
_what this really means if no arguments give, run with default argument_

__Some common default arguments__

- `cd` by default always changes to `/home/john`
- `ls` by default always list content of the current directory
- `bwa` by default runs a help menue

Just to reiterate something that you have already understand 
- you always start at the prompt
- then you tell the Shell what you want from it i.e which command to run
- then tell command what to wrok with i.e which file or directory

And the syntax always, always going to be command space argument. Doesn't matter what command you are running
there must a separator between command and it argument. Two possible senarios:

- no space between command and its argument - well shell will not recognise the command
- two spaces between command and its argument - shell will recognise the command, but command will see second 
space as its argument and might get confused

Would it be cool to also tell any given command how to run..?

e.g don't just give me the files, but also give me the size and the date and who owns the files

### Actually commands considere given options together with arguments

So happens that the standard for giving options to any commnads is a "dash":

- `-h` dash h  (one dash for short options)
- `--help` dash dash help (two dashed for verbose options)

both have exacttly the same effect. It is not a bad idea to write you options in verbose manner given that
you are going to publish them later or look at yourself and should be very self explanotory.

> ## Possible syntax for commands options {.callout}
> 
> Not always you will both options i.e `-h` and `--help`. It is a good practice to have both and alot of
> tools support that. However sometime you will get one or another. It is possible to get none. e.g STAR
> 
> Another point to note as we will see later some tools are really a collection of tools e.g BWA and SAMtools,
> hence the name. Therefore you call the tool e.g `samtools` then you would call subtool e.g `view` and
> then you would give options to a subtool, in this case `view`, because `view` is a subtool, there is
> no dashes in front. It isn't an option. It is tool !

> ## Take home massage {.callout}
> 
> - You need a separator to separate each thing you type in
> - The separator in the shell is `space` 
> - There will always be a sapce:
>   * between command and its options
>   * between options and arguments
>   * between arguments themselvs

~~~ {.bash}
~$ ls
~~~
~~~ {.output}

~~~
~~~ {.bash}
~$ cd /mnt/shared/RNAseq
~~~
~~~ {.output}
mapping  raw_data  ref_data
~~~
~~~ {.bash}
~$ ls -1
~~~
~~~ {.output}
mapping
raw_data
ref_data
~~~
~~~ {.bash}
/mnt/shared/RNAseq$ ls -r
~~~
~~~ {.output}
ref_data raw_data mapping
~~~
~~~ {.bash}
/mnt/shared/RNAseq$ ls -l
~~~
~~~ {.output}
total 12
drwxrwxr-x 2 roxane roxane 4096 Jun 29 14:49 mapping
drwxrwxr-x 2 roxane roxane 4096 Jun 29 11:44 raw_data
drwxrwxr-x 2 roxane roxane 4096 Jun 29 11:45 ref_data
~~~
~~~ {.bash}
$ ls
~~~
~~~ {.output}
draft.txt
~~~

### BAHS commands

I can't see a point jsut giving you list of commands to use. There are so many different commands and tools out
there and many more comes on the daily basis. Rather start using CLI and every time you want to do something
think of a command and google for it. e.g I want to copy some files. "How to copy files in terminal linux"
The key words are copy, terminal and linux. Always have terminal and/or linux and/or BASH in your search.

> ## Go and find new commands. Assignment-one {.challenge}
>
> I made a file with a lsit of commands. 
> The files are plain text files and you can view them in terminal
> Files under course name under relavant day
> 1. Go to relevant directory
> 2. Google how to view content of the file
> 3. more instructioin inside the file

> ## Go and find more new commands. Assignment-two {.challenge}
>
> There is another file with more commands inside the same directory
> It doesn't look like a file. 
> 1. Go to relevant directory
> 2. Use known commands to try to get content from each object in the directory
> 3. Once you find a relant file copy it to your home directory

The key aspects from the assignment:

- move and copy commands can also rename files. How..?

> ## Deleting Is Forever {.callout}
>
> The Unix shell doesn't have a trash bin that we can recover deleted
> files from (though most graphical interfaces to Unix do).  Instead,
> when we delete files, they are unhooked from the file system so that
> their storage space on disk can be recycled. Tools for finding and
> recovering deleted files do exist, but there's no guarantee they'll
> work in any particular situation, since the computer may recycle the
> file's disk space right away.

~~~ {.bash}
~$ ls
~~~
~~~ {.output}
file-one.txt file-two.txt
~~~
~~~ {.bash}
~$ cp /mnt/shared/RNAseq/software-carpentry/day-one/.hidden-list-of-files.txt
$ ls
~~~
~~~ {.output}

~~~
~~~ {.bash}
~$ cp .hidden-list-of-files.txt list-of-files.txt
~~~
~~~ {.bash}
~$ rm list-of-files.txt
~$ ls
~~~
~~~ {.output}

~~~

> ## With Great Power Comes Great Responsibility {.callout}
>
> Removing the files in a directory just so that we can remove the
> directory quickly becomes tedious. Instead, we can use `rm` with the
> `-r` flag (which stands for "recursive"):
>
> ~~~
> $ rm -r thesis
> ~~~
>
> This removes everything in the directory, then the directory itself. If
> the directory contains sub-directories, `rm -r` does the same thing to
> them, and so on. It's very handy, but can do a lot of damage if used
> without care.

Let's create that directory and file one more time.
(Note that this time we're running `nano` with the path `thesis/draft.txt`,
rather than going into the `thesis` directory and running `nano` on `draft.txt` there.)

~~~ {.bash}
~$ ls
~~~
~~~ {.output}

~~~
use arrow up to get previous cp commands
~~~ {.bash}
~$ mkdir first-dir
~~~
~~~ {.bash}
~$ cd first-dir
/first-dir$ ls 
/first-dir$ touch empty-file.txt
/first-dir$ ls
~~~
~~~ {.output}
empty-file.txt
~~~
~~~ {.bash}
/first-dir$ cd ..
~$ ls
~~~
~~~ {.output}
first-dir
~~~
~~~ {.bash}
~$ rm -r first-dir
~$ ls
~~~
~~~ {.output}

> ## Renaming files {.challenge}
>
> Suppose that you created a `.txt` file in your current directory to contain a list of the
> statistical tests you will need to do to analyze your data, and named it: `statstics.txt`
>
> After creating and saving this file you realize you misspelled the filename! You want to
> correct the mistake, which of the following commands could you use to do so?
>
> 1. `cp statstics.txt statistics.txt`
> 2. `mv statstics.txt statistics.txt`
> 3. `mv statstics.txt .`
> 4. `cp statstics.txt .`

> ## Copy with Multiple Filenames {.challenge}
>
> What does `cp` do when given several filenames and a directory name, as in:
>
> ~~~
> $ mkdir backup
> $ cp thesis/citations.txt thesis/quotations.txt backup
> ~~~
>
> What does `cp` do when given three or more filenames, as in:
>
> ~~~
> $ ls -F
> intro.txt    methods.txt    survey.txt
> $ cp intro.txt methods.txt survey.txt
> ~~~

> ## Which Editor? {.callout}
>
> When we say, "`nano` is a text editor," we really do mean "text": it can
> only work with plain character data, not tables, images, or any other
> human-friendly media. We use it in examples because almost anyone can
> drive it anywhere without training, but please use something more
> powerful for real work. On Unix systems (such as Linux and Mac OS X),
> many programmers use [Emacs](http://www.gnu.org/software/emacs/) or
> [Vim](http://www.vim.org/) (both of which are completely unintuitive,
> even by Unix standards), or a graphical editor such as
> [Gedit](http://projects.gnome.org/gedit/). On Windows, you may wish to
> use [Notepad++](http://notepad-plus-plus.org/).
>
> No matter what editor you use, you will need to know where it searches
> for and saves files. If you start it from the shell, it will (probably)
> use your current working directory as its default location. If you use
> your computer's start menu, it may want to save files in your desktop or
> documents directory instead. You can change this by navigating to
> another directory the first time you "Save As..."

Let's type in a few lines of text,
then use Control-O to write our data to disk:

![Nano in action](fig/nano-screenshot.png)

Once our file is saved,
we can use Control-X to quit the editor and return to the shell.
(Unix documentation often uses the shorthand `^A` to mean "control-A".)
`nano` doesn't leave any output on the screen after it exits,
but `ls` now shows that we have created a file called `draft.txt`:


