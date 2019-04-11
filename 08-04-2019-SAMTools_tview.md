### SAMTools tview

------

​                                                                                             **PSSUN**

#### Samtools introduction

**SAM** (Sequence Alignment/Map) format is a generic format for storing large nucleotide sequence alignments. **SAMTools** provide various utilities for manipulating alignments in the SAM format, including sorting, merging, indexing and generating alignments in a per-position format.

#### Required file

- Software: samtools
- File: bamfile.bam & referfasta.fa

#### Usage

- Step 1 : Installation (on ubuntu):

```shell
sudo apt-get install samtools
```

- Step 2: Sort bam file:

```shell
samtools sort bamfile.bam > sorted.bam
```

- Step 3: Make index for sorted bam file:

```
samtools index sorted.bam
```

- Step 4: View the result

```shell
samtools tview sorted.bam                # not to show the refer sequence
```

```shell
samtools tview sorted.bam referfasta.fa  # show the refer sequence
```

**NOTE:** Press **'g'** to go to the position you want to view, example: 'chr1:10000'

​           Press **'&larr;'** or **'&rarr;'** to move the window for 1 bp

​	   Press **'ctrl'+'H'** or **'ctrl'+'L'** to move the window for 1000bp

​           Use **'?'** to check more information when using tview.

Please refer to http://samtools.sourceforge.net/ for more information 
