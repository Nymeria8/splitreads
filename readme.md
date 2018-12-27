
# Split reads identification script

### Script for identification of reads overlapping a rearrangement junction. 


![alt text](https://cld.pt/dl/download/c7750b8f-b6e5-41b5-919f-513a4e416691/split.png "Split reads algorithm")

**This script works in continuation of the pipeline described by [Talkowski et al, 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3071919/)**

**A** Translocation cluster identified by liWGS data analysis.Arrowheads depict reads. Diamonds indicate the  breakpoint regions defined between genomic positions a-b and c-d, respectively.Triangles indicate the narrowest breakpoint-spanning intervals between a’-b’ and c’-d’.

**B** Data selection step. The narrowest breakpoint-spanning FASTA sequences from both chromosomes are selected as weel as the unmapped-mate read-pairs for posterior analysis.

**C** Successive alignment steps of read chunks against the reference FASTA sequences. The chunk alignment stops when no chunks have possible matches or the chunk size is equal to the read size.

**D** At the end, we have two chunks of the same read that perfectly map into two distinct genomic locations, identifying the breakpoint.

**For more details, see [David et al, 2019](https://www.google.com)**

## Instalation:
Clone the repository and use the split_reads_V5_beta.py directly:
<pre><code>git clone https://github.com/Nymeria8/splitreads.git
</code></pre>

## To run this script, you need:
+ An aligment file in SAM format of paired-end, large-insert whole genome sequencing, with a minimum of 25 bp of read size. We sujest [BWA aln](http://bio-bwa.sourceforge.net/) for the alignment, but any read alignment sotware that maintains the unmapped reads n the output file and uses the standard SAM flags should work.
+ A cluster that defines a rearrangement as given by [Talkowski et al, 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3071919/) **OR** A rearrangement with two breakpoint regions and two read spanning reads, as showed in the image above.

## Usage:

In the command line:

<pre><code>python split_reads_V5_beta.py [chr:a-a’-b’-b] [chr:c-c’-d’-d] [SAM file] [reference genome]
</code></pre>


+ [chr:a-a’-b’-b] and [chr:c-c’-d’-d]  - breakpoint regions as showed in the image above. a,b,c,d define the region covered by cluster reads; a',b',c',d' defines the breakpoint region.
+ [SAM file] - SAM output file of the alignment previously made
+ [reference genome] - hg19 or hg38
