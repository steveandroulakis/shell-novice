---
layout:
page title: The Unix Shell
subtitle: How to get to know a new CLI tool
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> * Suggest to lay out directories
> * Suggest an approach to explore CLI tool for the first time
> * Explore bwa tool
> * Explore SAMtools

Command-Line interface is super, super easy. I personally find CLI to be much more intuitive then
GUI, not because I have experience in it, rather because I understand how to find help. I always
find help in either of these three places: 

The thing about CLI that scares people the most, I believe, isn't the fact that it is black screen
or unfamiliar environment rather lack of drop downs, buttons and tick boxes. However CLI has all of
those options in one format and in one place and the way you access it is by type it in

GUI in its nature is very redundant. It will always have more than one way of doing the same thing
e.g "toolbar" is just a set of shortcuts, but there is a tools bar at the top, left right and
bottom, plus the right click all leading you to the same, one place.

### Lay out your directories

Very, very important is to lay out your directories, exactly as you would on your laptop. And don't
be afraid of the path ! It is nothing more than pointer to files location.

~~~ {.bash}
~$ mkdir projects
~$ ls
~~~ {.output}
projects
~~~ 
~~~ {.bash}
~$ cd projects
/projects$ ls
~~~ {.output}
~~~
~~~ {.bash}
/projects$ mkdir first-bacterial-work
/projects$ ls
~~~ {.output}
first-bacterial-work
~~~ 
~~~ {.bash}
/projects$ cd first-bacterial-work
/projects/first-bacterial-work$ ls
~~~
~~~ {.output}

~~~

### The steps to follow when exploring new CLI tool

1. What do I need to do..? 
   - I need to map my reads
   - I need tools for that
   - BWA will do that for me

2. How to map reads using BWA..?
   - the best way to know is google
_Even though majority of tools follow this convention where you can run the tool by itself and it will give
you help menu with usage at the very top. This is mandatory rather a good practice._
    - read the menu (manual) 

3. Dissect the usage line e.g `bwa mem [options] <idxbase> <in1.fq> [in2.fq]`
   - we understand the `bwa mem` part
   - almost always ignore the optional options to start with, because they are optional !
   - identify bits that you don't know and get to know them e.g what is this <idxbase> ..?
_All mapping tools that I know of, require an index file. That is an index of your reference sequence
in FASTA format_
   - run `bwa index` to get usage on that

4. Have we got all the files we need..?
   - source (download or get it otherwise) all the files that you need for the tool to run

### Just get Nike and Just do it ! BWA

Almost always you want to run the tool by itself first. If that fails try with `-h` and/or `--help`.

~~~ {.bash}
/projects/first-bacterial-work$ bwa
~~~
~~~ {.output}
Program: bwa (alignment via Burrows-Wheeler transformation)
Version: 0.7.5a-r405
Contact: Heng Li <lh3@sanger.ac.uk>

Usage:   bwa <command> [options]

Command: index         index sequences in the FASTA format
         mem           BWA-MEM algorithm
         fastmap       identify super-maximal exact matches
         pemerge       merge overlapping paired ends (EXPERIMENTAL)
         aln           gapped/ungapped alignment
         samse         generate alignment (single ended)
         sampe         generate alignment (paired ended)
         bwasw         BWA-SW for long queries

         fa2pac        convert FASTA to PAC format
         pac2bwt       generate BWT from PAC
         pac2bwtgen    alternative algorithm for generating BWT
         bwtupdate     update .bwt to the new format
         bwt2sa        generate SA from BWT and Occ

Note: To use BWA, you need to first index the genome with `bwa index'. There are
      three alignment algorithms in BWA: `mem', `bwasw' and `aln/samse/sampe'. If)      you are not
sure which to use, try `bwa mem' first. Please `man ./bwa.1' for)      for the manual.
~~~
~~~ {.bash}
/projects/first-bacterial-work$ bwa mem
~~~
~~~ {.output}
Usage: bwa mem [options] <idxbase> <in1.fq> [in2.fq]

Algorithm options:

       -t INT     number of threads [1]
       -k INT     minimum seed length [19]
       -w INT     band width for banded alignment [100]
       -d INT     off-diagonal X-dropoff [100]
       -r FLOAT   look for internal seeds inside a seed longer than {-k} * FLOAT [1.5]
       -c INT     skip seeds with more than INT occurrences [10000]
       -S         skip mate rescue
       -P         skip pairing; mate rescue performed unless -S also in use
       -A INT     score for a sequence match [1]
       -B INT     penalty for a mismatch [4]
       -O INT     gap open penalty [6]
       -E INT     gap extension penalty; a gap of size k cost {-O} + {-E}*k [1]
       -L INT     penalty for clipping [5]
       -U INT     penalty for an unpaired read pair [17]

Input/output options:

       -p         first query file consists of interleaved paired-end sequences
       -R STR     read group header line such as '@RG\tID:foo\tSM:bar' [null]]]       -v INT
verbose level: 1=error, 2=warning, 3=message, 4+=debugging [3]]       -T INT     minimum score to
output [30]]       -a         output all alignments for SE or unpaired PE]       -C         append
FASTA/FASTQ comment to SAM output]       -M         mark shorter split hits as secondary (for Picard/GATK compatibility))Note: Please read the man page for detailed description of the command line and options.
~~~

_run bwa again look for answers in the help menu_

~~~ {.bash}
/projects/first-bacterial-work$ bwa index
~~~
~~~ {.output}
Usage:   bwa index [-a bwtsw|is] [-c] <in.fasta>

Options: -a STR    BWT construction algorithm: bwtsw or is [auto]
         -p STR    prefix of the index [same as fasta name]
         -6        index files named as <in.fasta>.64.* instead of <in.fasta>.* 

Warning: `-a bwtsw' does not work for short genomes, while `-a is' and
         `-a div' do not work not for long genomes. Please choose `-a'
         according to the length of the genome.
~~~

_back to the point number 3 dissect the usage line. Start by ignoring optional options_
_It looks like for bwa all you need to do is to give a reference file_

~~~ {.bash}
/projects/first-bacterial-work$ cd
~$ ls
~~~
~~~{.output}

~~~

> ## Utilise your skills and make and index file(s) {.challenge}
>
> 1. go to your home directory
> 2. make new directory e.g working-dir or test-dir
> 3. copy reference bacterial genome from ref-files directory somewhere under `/mnt/shared/software-carpentry`
>    to you newly created directory
> 4. make bwa index

> ## Make index files in its own directory {.challenge}
>
> 1. remove all files in one go
> 2. create index files again, but make sure they go into its own directory e.g bwa-index

> ## Make reference directory {.challenge}
>
> 1. under your home directory make reference directory 
> 2. all your reference files and directories will go into that directory e.g bwa-index and fasta files
> 3. copy reference genome file to reference directory
> 4. make bwa index inside your reference directory

Different ways of redirection stuff to new directory

- some tools will a separate option e.g -o output directory
  * some tools will create your directory
  * others will not
_you really don't know. I always assume that they do and it error out obvioiusly they don't then_
- others will assume the path prefix (bwa assumes the path prefix)
_I understand that if you specify the out directory in the path prefix than it must be created before hand_

### SAMtools 

For me Bioinformatics and CLI in general isn't about remebering all the tools and commands and they options,
but about understanding how to ask the question and how quickly filter through the answers.

_run samtools and expore options that might need. Follow the general protocol_
