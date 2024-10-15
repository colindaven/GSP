# GSP
A tool for Genome Specific Primers design in polyploid species

In a polyploid species, genes from the homeologous genomes exhibit a very high sequence similarity, especially in the coding regions. This makes it difficult to design genome-specific primers to amplify specific sequences from the individual genomes in the polyploid genome background. Development of genome-specific primers for important genes in polyploid species is very useful and critical not only for the study of sequence diversity and association mapping of genes in natural populations, but also for the development of gene-based functional markers for marker-assisted breeding. GSP is a powerful tool for designing genome-specific primers that can distinguish the sequences among different genomes in a polyploid species. In additon, GSP also allow users to design specific primers in multiple sequence alignment.

Web server: https://probes.pw.usda.gov/GSP/

# Dependencies
There is number of additional dependencies not provided by GSP authors. Additional programs include:  
1. <b>bedtools:</b> a powerful toolset for genome arithmetic (http://bedtools.readthedocs.org/en/latest/).  
2. <b>Muscle:</b> Multiple sequence alignment program (http://www.drive5.com/muscle/).  
3. <b>Primer3:</b> program for designing PCR primers (http://primer3.sourceforge.net/).  

Blast is also required to generate blast results prior to using GSP.

# Installation
1. Download and unzip.
2. Enter the directory after extracting.
3. type `cmake ./src`
4. type `make`

Note:  
1. If cmake is not installed, please go to https://cmake.org/.  
2. If Boost is not installed, please go to http://www.boost.org/.  

# bin
The project folder contains an `executable file called GSP` and the `bin` folder contains the executable files of the dependencies, which were all tested in Ubuntu 14.04 (64-bit).

# Usage  
Before using GSP, please generate a `blast` result (`tab format`). For example, using query sequences blast polyploid genome.  


<b>Usage:</b> GSP  
<b>-r</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;blast table result path  
<b>-d</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sequence database path (blast database path)  
<b>-a</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fasta file path (for design specefic priemrs in multiple sequences only)  
<b>-b</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bedtools path (default: bedtools)  
<b>-m</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;muscle path (default: muscle)  
<b>-p</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;primer3 path (default: primer3_core)  
<b>-t</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;primer3 parameters file path  
<b>-o</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;output path  
<b>-q</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;number of hit sequences for perimer design of each query (default: 3)  
<b>-f</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;hit sequence flanking length (default: 200)  
<b>-s</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;product min size (default: 200)  
<b>-l</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;product max size (default: 1000)  
<b>-c</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;different site in primer (default: 2)  
<b>-e</b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;different site in 3 end of primer (default: No)  


Note:  
1. Make sure that the dependencies (`bedtools`, `muscle`, `primer3_core`) are in the `$PATH`. If not, they must be specified (-b, -m, -p).  
2. Please use absolute paths  

<b>Example 1:</b>  
Design specific primers in polyploid based on blast result.  

`./GSP -r ./example/example1/blast.tab -d ./example/example1/sequences.fas -b ./bin/bedtools -m ./bin/muscle -p ./bin/primer3_core -o ./example1_result.csv -q 3  `

<b>Example 2:</b>  
Design specific primers of multiple sequences.  

 `./GSP -a ./example/example2/sequences.fas -b ./bin/bedtools -m ./bin/muscle -p ./bin/primer3_core -o ./example2_result.csv`
 
 <b>Example 3:</b>  
Design specific primers in polyploid based on blast result with primer parameters setting. 

`./GSP -r ./example/example3/blast.tab -d ./example/example3/sequences.fas -b ./bin/bedtools -m ./bin/muscle -p ./bin/primer3_core -o ./example3_result.csv -q 3 -t ./example/example3/parameter_for_primer`

