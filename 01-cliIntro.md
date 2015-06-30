---
layout: page
title: The Unix Shell
subtitle: CLI First type
minutes: 15-20
---
> ## Learning Objectives {.objectives}
>
> *   Introduce the Command-line Interface
> *   Introduce some lingo
> *   Execute our first command `ssh`
> *   Present the CLI as an alternative to GUI

### Command-line interface (or CLI for short)

We saw in the previous section that you can operate an application such as web browser or MS office suites through 
simply pressing a combination of keyboard keys. This is cool and a great time saver.

Let me solidify why we want to use keyboard keys instead of mouse:

1. Speed and therefore time

   * hands always on the __keyboard__
   * no need to look __just do it__

Now lets utilise our keyboard system wide. 

The Command Line Interface (CLI) is an interactive and responsive thing. You will need to type words in and you will get
your response printed on the screen in response. The technical term for this is the **read-evaluate-print loop**, wherein a user:

1. __types a command__
2. presses enter (return) key
3. computer will read the command
4. __computer executes the command__
5. __output is shown on-screen__

The key to the Command-Line Interface:

- you will have to type
- the command line comes in different languages. ours is: `BASH`
- carefully read the output on the screen

### CLI is full of lingo.. learn it!

- folder == __directory__ AND directory == folder

- __CLI__ == terminal == SHELL (not exactly, but for us it is)
  - Terminal is a generic name describing an interface
  - Terminal comes from the old days when the only way to access a computer was through physical terminal.
    _Actually.. the correct language is terminal emulator, but it gets shortened to terminal!_
  - SHELL is an interpreter that conveys specific language that you type (eg. BASH language) to something that your computer
    can understand.
- You can't click on anything in the terminal. Forget about the mouse, you can only navigate using your __keyboard__
- `$`. This sign means __prompt__ - "a message or symbol on a screen to show that the system is awaiting user's input"
- __Execute__ == pressing Enter on the keyboard
- all commands are __executed at the prompt__
- launch == open == __start__ == double click
- server == just another computer much like your laptop. Others can access it remotely, sometimes through the __CLI__, often through a web browser.

### Let us execute our first command: `ssh`

Execute `ssh john@crunch.erc.monash.edu` replace john with your login name. _See an instructor for your details_.

_In this case `Serverauditor` is our terminal emulator and this will be our CLI_

To explain what just happened. `crunch.erc.monash.edu` is computer on the internet with a fancy name. The name could have been
anything. You don't even need to have a name. The name is an abstraction for an numeric IP address eg. 192.168.1.11.

In plain English, this `ssh` command means "log john in to the crunch machine". Very simple. Three parts to it: 

- log me in `ssh`
- who you are `john`
- where you want to be `crunch.erc.monash.edu` (this server happens to run in one of Monash's data centres)

Now we are on the remote machine..

### Why use ssh?
You can `ssh` to most computers in the world (provided they're not Windows!). For example, the vast majority of web sites in the world run the Linux operating system and therefore have ssh support.. not that Google.com want you to try and remotely control their servers and delete all their files :)

You use `ssh` because the computer you're connected to has advantages..

- it often has many more CPU's and RAM (memory)
- you can often leave it running over night, days, weeks, you don't ever shut it down.. it just sits there processing
- it has all the tools you need installed, saving you doing it yourself
- because your data might live right next to the server, so you don't need to download it on your terrible home connection
- because it might be networked on the web, meaning you can run web sites and host downloadable files off it for others (eg. host results of your experiments!)

You can still run these tools on your local machine, within reason, but it's often much easier to work elsewhere.

> ## How to copy and paste - terminal {.callout}
> - `shift+ctrl^c` copy from terminal
> - `shift+ctrl^v` paste to terminal

Mac users using the in-built Terminal app use `command^c` and `command^v` instead.

### CLI is just a very powerful interface for operating your computer

This isn't much different from GUI where you don't have to type anything in as such, but you still need to
read your results off the screen.

A GUI may appear intuitive on the surface, but pretty quickly a CLI starts to feel familiar. It has all the advantages of providing you with far more control than a GUI and no need to learn a new interface. Of course these days it is rather hard to avoid GUI. Drawing and graphical editing is certainly best done with the mouse, but we are
not in that kind of industry. I believe majority of bio-analysis is done using keyboard rather than mouse. 
More importantly majority of bio-analysis could and perhaps should be done using keyboard rather than mouse.

Why CLI..?

__convincing__

- faster to type than point and click
- easy to write and publish your methods sections
- reproducible, commands either work or don't - no two ways about it
- easy to communicate commands as opposed to explaining which drop down menu to find the specific function

__'why not' the command line?__

- can automate and run multiple jobs at once  _I don't care_
- access to high performance computers and clusters _I still don't care_
- a lot of tools don't have graphical interface _Well too bad, they should !_

Nothing can stop you from using a Graphical User Interface, but once you learn the Command Line, you will have an indispensible tool and power at your disposal for decades to come.

Lets leap into it..!
