---
layout: page
title: The Unix Shell
subtitle: Breaking the ice
minutes: 5-10
---
> ## Learning Objectives {.objectives}
>
> * Introduce common biological files
> * Introduce the overall theme for this two days workshop
> * Focus on an RNA-seq pipeline
> * Present the keyboard as your friend

### Most common biological files:

- FASTQ: "raw data" your sequenced reads with quality information per base
- FASTA: can hold any sequence information where each new sequence is separated by ">" sign
- SAM/BAM: "Sequence Alignment Map" and B for binary (BAMs are compressed versions of SAMs). SAM holds alot of information including
  * mapped reads coordinats
  * also holds quality information per base
  * information about sequence mismatches
  * custom encoded information e.g poly(A) tail length information
- GTF/GFF: annotation files

### Two steps bioinformatics:

1. **Getting the data** and getting the data into the right format (can be troublesome and time
consuming) - we need BASH (CLI) skills to get the data and to do primary filtering on the data

2. **Analysing the data** (obviously can be much more time consuming (don\’t undervalue step one though!) - 
this where we need R language to get the answers from our digital-raw data

For example you can most certainly grab your BAM files from elsewhere and start your analysis from that
point onward.. in most cases this should be fine, particularly when you are doing something fairly standard eg.
RNA-seq on mouse for differential gene expression. However if you are doing something a bit more out of the ordinary
or novel then working with data can be tricky. Running tools with default parameters isn't so good any more.

### The common RNA-seq pipeline workflow (from FASTQ to BAM and beyond)

1. Get your FASTQ files - download ..?
2. Clip your FASTQ files - quality and adapter clipping (sometimes)
3. Get your BAM files - Align your FASTQ files to the reference genome 
4. Get your counts - Count how many reads fallen onto the gene feature

__Common tools:__

- `BWA` set of tools used for FASTQ alignment
  * `bwa index` index your reference genome - (must do!)
  * `bwa mem` running the actual alignment and generating a SAM file
- `SAMtools` set of tools for SAM/BAM files manipulation
  * `samtools view` to view the files with different options:
    + `-h`
    + `-c`
    + `-f 4`
    + `-Sb`
  * `samtools sort` sort the file either by coordinates or by chromosome name
  * `samtools index` 
- `featureCount` tool for counting how many reads have mapped onto the gene
- `nesoni` set of tools (I'll cover this later)
  * `clip` use nesoni clip to clip low quality and adapters. It has support for many common adapters

### A keyboard is intrinsically faster than a mouse

It is given that keyboard is faster at doing common tasks you could do with a mouse e.g:

- In a browser..
  * `ctrl^l` - highlights the URL
  * `ctrl^k` - places cursor in the search bar
  * `alt^` (arrows left or right) - page history back/forward

- Common programs (for Mac, replace `ctrl` with `command`)
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

These commands are second nature to anyone great with computers. _Otherwise_ they are set to become your biggest time saver while working on computer.
_I am not a faster worker. I am an efficient worker. I just know and love my shortcuts_.
Appreciate that the keyboard enables you to operate computer at a different level: one where you instruct the computer using a keyboard rather than point and click and the payoff is __time saved__.

When working, I don't have time to:

1. Reaching for the mouse
2. Finding the mouse on the screen
3. Navigating to the right button or icon to click on it

This brings me to the next point

_Useful resources_

Web browser keyboard shortcuts

- [Firefox keyboard shortcuts](https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly#w_navigation)
- [Chrome keyboard shortcuts](https://support.google.com/chrome/answer/157179?hl=en)
