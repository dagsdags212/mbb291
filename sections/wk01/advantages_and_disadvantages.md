---
kernelspec:
  name: python3
  display_name: 'Python 3'
---
# Advantages and Limitations of Long-read Sequencing

## Short-read sequencing

- most commonly used form of next-generation sequencing
- genome is broken into _small fragments_ (typically 50 to 300 bases) before being sequenced
- carry out sequencing by synthesis or ligation
- nucleotides can either be probided one at a time, or they can be modified with identifying tags
- can be single molecule-based (sequencing of a single molecule)
- can be ensemble-based (sequencing of multiple identical copies of a DNA molecule)

### Effective for applications aimed at:

- counting abundance of specific sequences
- identifying variants within well-conserved sequences
    + Single nucleotide variations (SNPs), short indels
- profiling of expression of particular transcripts

### Workhose in NGS labs:

- obtain _high depth_ and _high quality_ data for the _lowest cost per base_
- higher coverage of targets
- high confidence SNP and mutation calling

### Common limitations:

- inability to sequence long stretches of DNA
  + preparations require _fragmentation_ and _amplification_
  + amplification steps can introduce biases
  + can fail to generate sufficient overlap between DNA fragments
    + assemblies may be fragments and may contain hundreds or even thousands of contigs
- challenging to sequence (_and assemble_) highly complex and repetitive genoes (or targets)
  + structural variants and repeats that are longer than the short reads
- library preparations can be laborious and may have long turnaround time
- methylation changes are not detected

## Long-read sequencing

- capable of reading longer lengths (kb to mb lengths)
  + 4 mb as maximum reported read length
- generate reasonable length to _overlap_ a sequence for better sequence assembly
  + reads can be longer than (or span) structural variants, complex regions (repeats and rearrangements), and highly polymorphic regions
- _Single_ molecular sequencing
  + native molecules (DNA/RNA) are processed
    + no need for fragmentation
    + eliminates amplification bias
  + directly detects presence of modified bases
- sequencing in real-time (or near real-time)
  + adaptive sampling (nanopore): enrichment or depletion

### Analogy: Building Puzzles

:::{image} https://media.licdn.com/dms/image/v2/D4D12AQEviW_k5TFy_Q/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1658514975459?e=1746057600&v=beta&t=1z4dcqpN18gGLJ1CiWIAw3l0B7Il4yivtVN4Lo15Zcs
:label: read-analogy
:align: center
:::

> Short-read sequencing produces fragments that are much smaller (~150 bp), making it much more difficult to piece them together to form a larger segment (or contig).

:::{note}
The process of generating longer, contiguous sequences from a set of overlapping reads is called {sc}`sequence assembly`.
:::

### Assembly graphs

:::{image} ./images/short_vs_long_read_assembly.png
:label: long-vs-short-read-assembly
:align: center
:::


:::{aside} Advantages of long read assembly
Show here is a genome sequence with 3 unique segments A, B, and C in blue, yellow, and green, and 3 copies of a repeat R in red.

If the repeat length is shorter than the repeat region (left), the corresponding assembly graph will contain 4 contigs, with edges connecting them but in an ambiguous order.
If the reads span the repeat segments (right), the the corresponding assembly graph will not be branching, and a single long contig spanning the entire genome will be created.

{cite}`10.1101/006395`
:::

:::{image} ./images/salmonella_assembly.png
:label: salmonella-assembly
:align: center
:::

### Downside of long-read sequencing

- **accuracy**: accuracy per read may be lower than that of short-read
  + high raw error rates - random errors during detection step
  + see comparison of short-read sequences vs. long-read sequencers (buyer's guide)
- **cost**: more expensive per Gb output that short-read sequencing technologies
- **throughput**: lower output than short-read sequencing

## Then and Now of long-read sequencers

:::{table} Progress of ONT and PacBio from start to date. {cite}`10.1016/j.tig.2023.04.006`
:label: progress-long-read-sequencers
:align: center

<table>
   <tr>
      <th rowspan="1"></th>
      <th colspan="2" align="center">ONT</th>
      <th colspan="2" align="center">PacBio</th>
   </tr>
   <tr>
      <th align="center"></th>
      <th align="center">Then</th>
      <th align="center">Now</th>
      <th align="center">Then</th>
      <th align="center">Now</th>
      <th>
   </tr>
   <tr>
      <td>Accuracy</td>
      <td align="center">60-70%</td>
      <td align="center">99.6% (simplex) <br> 99.92% (duplex)</td>
      <td align="center">~85%<td>
      <td align="center">99.9% (HiFi)<td>
   </tr>
   <tr>
      <td>Read length</td>
      <td colspan="2" align="center">Unlimited <br> (in principle)</td>
      <td align="center">~1.5 kb<td>
      <td align="center">>200 kb<td>
   </tr>
   <tr>
      <td>Short reads</td>
      <td colspan="2" align="center">minimum length 200 nt</td>
      <td align="center">not available<td>
      <td align="center">SBB short read sequencing <br> (100-220 nt)<td>
   </tr>
   <tr>
      <td>Maximum throughput per run</td>
      <td align="center">~0.5 Gb</td>
      <td align="center">14 Tb (PromethION 48)</td>
      <td align="center">~100 Mb<td>
      <td align="center">360 Gb (HiFi)<td>
   </tr>
</table>
:::

