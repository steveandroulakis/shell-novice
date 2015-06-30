---
layout: page
title: The Unix Shell
subtitle: Creating Things
minutes: 25-30
---
> ## Learning Objectives {.objectives}
>
> * Explain the general syntax of the shell
> * Explain command options and arguments
> * Run commands!

### Shell reads commands. Commands read arguments

The way the CLI works is that you tell it what needs to be done i.e "here is command, now execute it". It will do
exactly that. However, sometimes you need to tell it extra information such as the data you want it to operate on. These are _arguments_, also known as _parameters_. There are also _options_.

- some programs can only run by themselves e.g `date`, `cal` 
- some programs can only run with given arguments e.g `mv`, `cp`
- other programs can run either way, with or without parameters e.g `cd`, `ls`
_if you give no arguments, commands assume certain defaults_

__Some common default arguments__

- `cd` by default always changes to your home directory eg. `/home/john`
- `ls` by default always lists the contents of the current directory
- `bwa` by default runs a help menue

The syntax is always the same. `command and arguments`. eg `tail -f /my/file`.

- Always remember to put spaces between your commands and each argument.
- More than one space is often okay, though not always!

### Commands and options

There are also _options_. These always start with a dash and can have their own arguments. Above I typed `tail -f /my/file` which means "show me the bottom lines of a file (tail) with the file (-f) /my/file (the argument)".

Why might I do this?

A very common option for many programs..
- `-h` dash h  (one dash for short options)
- `--help` dash dash help (two dashed for verbose options)

Both have exacttly the same effect. It is not a bad idea to write your options in verbose manner given that
you are going to publish them later or look at it again yourself. You don't want to be guessing what -x or -o means in a particular program, for example.

> ## More about options {.callout}
> 
> It's important to note that some programs don't give you a single dash and double dash option like `-h` and `--help`. It's good practice to, but bioinformatic tools (and scientific software in general) is famed for not conforming to rules!
> Another point to note: Some tools are really a collection of tools e.g BWA and SAMtools, hence the name. Therefore you call the tool e.g `samtools` then you would call subtool e.g `view` and
> then you would give options to a subtool, in this case `view`, because `view` is a subtool, there is
> no dashes in front. It isn't an option. It is tool!

> ## Notes about spaces {.callout}
> 
> - Separate your arguments from each other
> - The separator in the shell is `space` 
> - There will always be a space:
>
>   * between commands and their options
>   * between options and arguments
>   * between arguments themselves
>
>   * you'll also learn quickly that spaces in file names are problematic on the shell. Something to learn about (!!).

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

### BASH commands

There are hundreds of thousands, if not millions of commands available. So many tools out there with more and more on a daily basis. Rather than learning specific commands one by one, it's important to have the fundamentals of the command line. Once you know this and are comfortable then you can always Google for how to use a specific tool. For example: "How to copy files in terminal linux". Always put `terminal` or `bash` in your searches for basic operations such as this.

> ## Go and find new commands. Assignment-one {.challenge}
>
> I've made a file with a list of commands. 
> The files are plain text files and you can view them in your terminal. I'll show you where to find them on the server..
> 
> From there..
> 1. Go to the directory with the files
> 2. Google how to view content of a file
> 3. More instructions will be found in each file

> ## Go and find more new commands. Assignment-two {.challenge}
>
> There is another file with more commands inside the same directory but it doesn't look like a file. 
> 1. Go to the directory
> 2. Use known commands to try to get content from each object in the directory
> 3. Once you find the file, copy it to your home directory

The move and copy commands can also rename files in a directory. How?

> ## Deleting Is Forever {.callout}
>
> The Unix shell doesn't have a recycle or trash bin that we can recover deleted
> files from (though most graphical interfaces to Unix do).  Instead,
> when we delete files, they are unhooked from the file system so that
> their storage space on disk can be recycled automatically. Tools for finding and
> recovering deleted files do exist, but there's no guarantee they'll
> work in any particular situation, since the computer may recycle the
> file's disk space right away. Be careful!

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


