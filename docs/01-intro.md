# The Alignment Pipeline {#intro}

In this chapter we'll look at an overview standard paired-end read run of `minimap2`, what it outputs and how to manipulate the output with `samtools`.

The overall pipeline is very straightforward...

  1. Align all reads to a reference
  2. Filter badly scoring reads
  3. Sort and compress output
  

## Align all reads to a reference

  This is the main step, and with `minimap2` it can be accomplished with a single command-line. In this step each read is aligned against the reference, and its best aligning position found. That position, along with a metric of the quality of the single alignment is reported in a `SAM` format file.

## Filter out badly scoring reads
  
  This is the quality control step. We remove reads that don't have a good alignment score because in most contexts it means the read is a bad read with bad sequence in it. Of course in some contexts it isn't - it depends what you're aligning to what, but for the RNAseq situation or SNP calling situation where we expect the reads to be very like the reference this is appropriate. This step is done with `samtools`
  
## Sort and compress output
  
  Once filtering is done and we have the set of reads we wish to retain we can take our output file and convert it to a sorted binary format that uses less disk space and is optimised for searching in downstream analysis. This step is a kind of housekeeping step that makes everything later easier. We do it with `samtools`
  
## Further Reading

###  FastQ quality scores
Typically the reads we use will be in the FastQ format, this is a two line format that encodes not only the sequence read, but the 'believability' of each base. You can see more [here](https://en.wikipedia.org/wiki/FASTQ_format)

### Why minimap2 and not bwa|bowtie|other

You may have heard of other aligners and that people in your group are using them. `minimap2` is currently the quickest and most accurate of all the aligners and has general ability with all modern sequence types. Those using others (in particular bwa and bowtie) are pretty out of date. bwa _was_ a favourite for a long time, but has been superceded. The same author created both bwa and minimap2 and minimap2 was written to address issues with bwa. 

