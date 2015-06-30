---
layout: page
title: The Unix Shell
subtitle: Breaking the ice
minutes: 5
---
> ## Learning Objectives {.objectives}
>
> * Introduce common biological files
> * Introduce overall theme for this two days workshop
> * Focus on RNA-seq pipeline
> * Present keyboard as your friend

### Most common biological files:

- FASTQ "raw data" your sequenced reads with quality information per base
- FASTA can hold any sequence information where each new sequence seprated by ">" sign
- SAM/BAM "Sequence Alignment Map" and B for binary. SAM holds alot of information including
  * mapped reads coordinats
  * also holds quality information per base
  * information about sequence mismatch
  * custom encoded information e.g poly(A) tail length information
- GTF/GFF annotation files

### Two steps bioinformatics:

1. **Getting the data** and getting the data into the right format (can be troublesome and time
consuming) - we need BASH (CLI) skills to get the data and to do primary filtering on the data

2. **Analyse the data** (obviously can be much more time consuming (don\’t undervalue step one though!) - 
this where we need R language to get the answers from our digital-raw data

For example you most certainly can grab your BAM files from else where and start you anaylisis from that
point onward and in most cases this should be fine, particular when you are doing some what standard
RNA-seq on mouse for differentical gene expression. However if you are doing some a bit more out of ordinary
or novel than getting the data can be tricky to get. Running default parametrs isn't good any more.

### Common RNA-seq pipeline workflow (from FASTQ to BAM and beyond)

1. Get your FASTQ files - download ..?
-  Clip your FASTQ files - quality and adapter clipping (sometimes)
2. Get your BAM files - Align your FASTQ files to the reference genome 
3. Get your count - Count how many reads fallen onto the gene feature

__Associate tools:__

- `BWA` set of tools used for FASTQ alignment
  * `bwa index` index your reference genome - must do !
  * `bwa mem` running actuall alignment and generating SAM file
- `SAMtools` set of tools for SAM/BAM files manipulation
  * `samtools view` to view the files different options below
    + `-h`
    + `-c`
    + `-f 4`
    + `-Sb`
  * `samtools sort` sort the file either by coordinats or by chromosome name
  * `samtools index` 
- `featureCount` tool for counting how many reads have mapped onto the gene
- `nesoni` set of tools used that I want go into
  * `clip` use nesoni clip to clip low quality and adapters. It has a list of many common adapters

### Keyboard is intrinsicly faster than a mouse

It is given that keyboard is faster at doing the same thing you would with a mouse e.g:

- searching for a browser and launching it
  * ctrl^l - highlights URL
  * ctrl^k - places cursor in the search bar
  * alt^ (arros left of right) - to move to the previous or next pages

- copy and paste
  * `ctrl^c` copy
  * `ctrl^v` paste
  * `ctrl^s` save
  * `ctrl^o` open
  * `ctrl^a` highlight all text
  * `ctrl^p` print
  * `ctrl^z` undo
  * `ctrl^b` make bold
  * `ctrl^i` make italic
  * `ctrl^u` make underline
  * `ctrl^n` open new window
  * `ctrl^f` find

These commands are inbuild in us. `if not` they are your biggest time saver while working on computer.
_I am not a faster worker. I am efficient worker. I just know and love my shortcuts_.
All I want from you is to appreciate that keyboard enables you to operate computer at the different level,
level where you instruct computer using keyboard rather than point and click and the pay off is __time__.

I don't have time to:

1. rich across to a mouse
2. jerk a mouse a bit and simultaneously find search for a pointer on the screen
3. navigate to firefox icon and double click on it

This is too long...

This brings me to the next point

_Useful resources_

Web browser keyboard shortcuts

- [Firefox keyboard shortcuts](https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly#w_navigation)
- [Chrome keyboard shortcuts](https://support.google.com/chrome/answer/157179?hl=en)
