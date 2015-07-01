---
layout:
page title: The Unix Shell
subtitle: Getting to know a bioinformatic tool
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> * Understand how to structure your processed data
> * Know how to explore a new command line tool
> * Get familiar with the bwa bioinformatics tool
> * Explore the SAMtools bioinformatics suite

### Organise your data

Here's how I lay out my bioinformatics data on the group server:

~~~ {.bash}
$ mkdir projects
$ ls
~~~
~~~ {.output}
projects
~~~ 

~~~ {.bash}
$ cd projects
/projects$ ls
~~~
~~~ {.output}

~~~

~~~ {.bash}
/projects$ mkdir first-bacterial-work
/projects$ ls
~~~~
~~~ {.output}
first-bacterial-work
~~~ 

~~~ {.bash}
/projects$ cd first-bacterial-work
/projects/first-bacterial-work$ ls
~~~
~~~{.output}

~~~

### The steps to follow when exploring new CLI tool

1. What do I need to do..? 
   - I need to map my reads
   - I need tools for that
   - BWA will do that for me 2. How to map reads using BWA..?
   - Google no doubt has it.
_Many tools give you a bit of help text if you run them without any arguments. However this is good practice and not mandatory._
    - Read the manual or scientific literature.

3. Dissect the usage line e.g `bwa mem [options] <idxbase> <in1.fq> [in2.fq]`
   - We understand the `bwa mem` part
   - bwa has a series of options, but lets ignore them for now.
   - identify bits that you don't know. eg. what's <idxbase> ..?
_Mapping tools require an index file. ie. An index of your reference genome. Most often in FASTA format_
   - run `bwa index` to learn what it does and how to use it.

4. Make sure you have all your data ready.
   - source (download or get it otherwise) all the files that you need for the tool to run

### BWA: 'Just do it!'

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

_Time to dissect the usage line. Start by ignoring the (non-mandatory) options_
_From the usage section, it appears as if bwa only requires an index file to run._

~~~ {.bash}
/projects/first-bacterial-work$ cd
~$ ls
~~~
~~~{.output}

~~~

> ## Utilise your skills and make and index file(s) {.challenge}
>
> 1. go to your home directory (~/)
> 2. make a new directory for your data e.g working-dir or test-dir
> 3. copy our reference bacterial genome from the ref-files directory under `/mnt/shared/software-carpentry` (find the file name with `ls`!)
>    to your newly created directory
> 4. run bwa to make the index, ready for alignment

> ## Make index files in its own directory {.challenge}
>
> 1. remove all of the index files you created (try to remove them in one go with the * wildcard, but be careful!)
> 2. create your index files again using bwa, but make sure they go into their own directory e.g make a new one called bwa-index

### SAMtools 

Lets explore SAMtools together..

_First, run the `samtools` command on its own._
