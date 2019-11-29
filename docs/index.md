--- 
title: "Basic Read Alignment"
author: "Dan MacLean"
date: "2019-11-29"
site: bookdown::bookdown_site
output: bookdown::gitbook
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
github-repo: TeamMacLean/basic_alignment
description: "A minimal guide to performing read alignment against a reference"
---

# About this course

In this short course we'll look at a method for running an alignment of sequence reads against a reference genome. The course is very brief and will show you how to use a program called `minimap2` and `samtools` to create a binary alignment file that you can use in further work. 

I acknowledge that there are lots of other programs and methods - this course is _not_ meant to be comprehensive, it is meant to get you being productive. Seek out further advice if you need to run other programs. Do be encouraged though, 99 % of what you learn here will be applicable to other tools for the same job (they all run in a _very_ similar manner) so this is a good place to start. 

The course has two main parts - first we'll learn to do this 'locally', that is to say on the computer that you are actually physically sitting at and have direct control over. Once we've done that and know how to run the actual programs then we shall switch to running the programs 'remotely' on a HPC environment using a submission system that you have to log in to.

## Prerequisites

This course assumes that you are familiar with the basics of running stuff from a command-line. You'll need to have some experience not lots. If you've done the TSL command-line course you'll know plenty

For the first 'local' part of this you'll need some software on your machines. Most bioinformatics software has to run on Unix style computers, which for most of us means Macs. The installation instructions below only apply to Macs.

For the second part you'll need an HPC account. See the Bioinformatics Team to get one of these.


### Local Software Installation

We need to install `minimap2` and `samtools`. Installing bioinformatics software is often _not_ straightforward so we'll take a path of least resistance and install some tools that manage software for us. This is a roundabout way of doing things, but it greatly simplifies the hard parts and means that we can isolate our installations from the rest of our computer and not mess up anything already installed.


  1. **Get `conda`**
    `conda` is an environment and package manager for software projects (initially Python - hence the name). Its purpose is to create a sandbox area on your computer where you can safely install software without it interfering or overwriting any of the existing software already on there. This safe space is called a conda 'environment'. To install `conda`:
      1. Click this link [https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg) and wait for the package to download. When it has double-click it and go through the installation process.
  2. **Get `bioconda`**
    `bioconda` is plugin that makes `conda` aware of the bioinformatics software we will need. To make `conda` aware of `bioconda` 
      1. Open `Terminal` and type the following:
     
```
      conda config --add channels defaults
      conda config --add channels bioconda
      conda config --add channels conda-forge
```
  3. **Create a new environment**
  We can now create our new safe space environment. Type in the following.

```
      conda create --name alignment_env
```
  This step can take a moment or two and nothing seems to happen for a while - be patient. Accept the defaults (answer `y` when questioned).
  
  4. **Activate the environment**
  Everytime we want to use the new environment, including to install something into it, we have to activate it. That means each time we leave or start a new Terminal we need to type this into it
  
```
  conda activate alignment_env
```
  You should see the name at the `$` prompt change, telling you that this Terminal is in the `alignment_env` environment. If you ever can't find programs that you're sure you installed, it means that you probably didn't activate the right environment.
  
  5. **Install the alignment software `minimap2` and `samtools`**
  All the steps up to now have been so we can do this one! Install each of the pieces of software in turn by using `conda` with:
```
      conda install minimap2
      conda install samtools
```
These steps can also take a while. Again accept the defaults (answer `y`).

Now you are done! Everything is installed ready for you to work with. Next we need to get the sample data

### Sample reference genome and reads

You'll need this [E.coli reference genome](sample_data/ecoli_genome.fa) file and this set of [paired end reads](sample_data/ecoli_pe.fq). Download them and put them into a folder on your machine. I suggest `Desktop/align_tut`. I'll assume that is the directory you will work from.


That's all you need to do the lesson. If you have any problems getting this going, then ask someone in the Bioinformatics Team and we'll help.





