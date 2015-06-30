---
layout: page
title: The Unix Shell
subtitle: CLI First type
minutes: 15-20
---
> ## Learning Objectives {.objectives}
>
> *   Introduce Command-line Interface
> *   Introduce the lingo
> *   Execute first command `ssh`
> *   Present CLI as an alternative to GUI

### Command-line interface or CLI for short

We saw in previous section that you can operate an application such as web browser or MS office suites through 
simply pressing combination of keyboard keys. This is cool and great time saver.

Let me solidify why we want to use keyboard keys instead of mouse:

1. Speed and therefore time

   * hands always on the __keyboard__
   * no need to look __just do it__

Now lets utilise keyboard system wide. 

CLI is this interactive and responsive thing, where you will need to type things in and you will get
your response printed on the screen. The technical term for this is **read-evaluate-print loop**, where user
needs:

1. __type a command__
2. then press enter (return) key
3. computer will read the command
4. __execute the command__
5. show the __output on the screen__

The key to the Command-Line Interface:

- you will have to type
- in specific language - BASH
- read your answers of the screen

### CLI is full of lingo, just learn it

- folder == __directory__ AND directory == folder
- __CLI__ == terminal == SHELL (not exactly, but for us it is)
  * It is a generic name describing an interface
  * Terminal comes from old days when the only way to access computer was through physical terminal.
    Actually correct language is terminal emulator, but gets shorten to terminal!
  * SHELL is an interpreter that conveys specific language that you type (BASH) to something that computer
    can understand.
- can't click on anything in the terminal. Forget about mouse, can only navigate using __keyboard__
- `$` this sign means __prompt__ - "a message or symbol on a screen to show that the system is waiting
user's input"
- __Execute__ == pressing Enter on the keyboard
- all commands are __executed at the prompt__
- launch == open == __start__ == double click
- server == just another computer much like you laptop, which can also server some files or other content

### Let us execute our first command `ssh`

Execute `ssh john@crunch.erc.monash.edu` insert your login name

_In this case `Serverauditor` is our terminal emulator and this will be our CLI_

To explain what just happened. `crunch.erc.monash.edu` is computer with fancy name. The name could have been
anything. You don't even need to have a name. The name is an abstraction for an numeric IP address.
In plain English command means log john to crunch machine, very simple. Three parts to it: 

- log me in `ssh`
- who you are `john`
- where you want to be `crunch.erc.monash.edu`

And now we are on the remote machine else where and who really know where...
You can `ssh` to any computer you want (provided some settings) 

I'm not clear why should I use `ssh` ..?

- to log in to another computer
- because it has many more CPU's and RAM (memory)
- because you can leave it running over night, days, weeks, you don't ever shut it down
- because it has all the tools installed 
- because your data might comes straight to that server

But really you can run your tools on your local machine a.k.a your laptop if you want.

This brings me back to this same, important point why CLI and so I would like to re-solidify it again

> ## How to copy and paste - terminal {.callout}
> - `shift+ctrl^c` copy from terminal
> - `shift+ctrl^v` paste to terminal

### CLI is just an interface to operate a hardware bunch a.k.a computer

This isn't much different from GUI where you don't have to type anything in as such, but you still need to
read off the screen, accept it is more appealing visually or some might thing so. To me it's just an extra
layer of distraction.

GUI may appear intuitive to some or most of users, however I would argue the opposite CLI is much
easier and much more intuitive once one has developed appreciation for CLI. Of course these days it is
rather hard to avoid GUI. Drawing and graphical editing is certainly best done with the mouse, but we are
not in that kind of industry. I believe majority of bio-analysis is done using keyboard rather than mouse. 
More importantly majority of bio-analysis should be done using keyboard rather than mouse.

Why CLI..?

__convincing__

- faster to type then point and click
- easy to write and publish your methods sections
- reproducible, commands either work or don't - no two ways about it
- easy to communicate commands appose to explaining which drop down menu

__no so much__

- can automate and run multiple jobs at once  _I don't care_
- access to high performance computers and clusters _I still don't care_
- a lot of tools don't have graphical interface _Well too bad, they should !_

Speaking frankly nothing is stopping you from using GUI and please do, because that will make me always look
much more efficient just because I am too lazy not to be lazy and press keyboard keys.

Lets leap into CLI..
