---
layout: page
title: The Unix Shell
---
The Unix shell has been around longer than most of its users have been alive.
It has survived so long because it's a power tool
that allows people to do complex things with just a few keystrokes.
More importantly,
it helps them combine existing programs in new ways
and automate repetitive tasks
so that they don't have to type the same things over and over again.
Use of the shell is fundamental to using a wide range of other powerful tools 
and computing resources (including "high-performance computing" supercomputers).
These lessons will start you on a path towards using these resources effectively.

> ## Prerequisites {.prereq}
>
> This lesson guides you through the basics of file systems and the
> shell.  If you have stored files on a computer at all and recognize
> the word “file” and either “directory” or “folder” (two common words
> for the same thing), you're ready for this lesson.
>
> If you're already comfortable manipulating files and directories,
> searching for files with `grep` and `find`, and writing simple loops
> and scripts, you probably won't learn much from this lesson.

> ## Getting ready {.getready}
>
> You need to download some files to follow this lesson:
> 
> 1. Make a new folder in your Desktop called `shell-novice`.
> 2. Download [next-gen-data.zip](./next-gen-data.zip) and move the file to this folder.
> 3. If it's not unzipped yet, double-click on it to unzip it. You should end up with a new folder called `data`.
> 4. You can access this folder from the Unix shell with:
>
> ~~~ {.input}
> $ cd && cd Desktop/shell-novice/data
> ~~~

## Topics

1.  [Breaking The Ice](00-breakingTheIce.html)
2.  [CLI inroduction](01-cliIntro.html)
3.  [The root and The path](02-theRoot-thePath.html)
4.  [Create Things](03-create.html)
5.  [Chaining commands together with pipe](04-pipe.html)
6.  [How to get to know a new CLI tool](05-exploreTools.html)
6.  [Automate with loops](06-loop.html)
7.  [Finding Things](07-find.html)

## Other Resources

*   [Motivation](motivation.html)
*   [Reference](reference.html)
*   [Discussion](discussion.html)
*   [Instructor's Guide](instructors.html)
