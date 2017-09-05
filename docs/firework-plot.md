# Genome Firework Plot

A tutorial by David Eccles about representing a genome in a visually-interesting form.

<img src="pics/genome_firework_Nb_small.png" alt="Genome firework plot for Nippostrongylus brasiliensis" title="Genome firework plot for Nippostrongylus brasiliensis" width="512"/>

## Preparation

This tutorial uses the GFA file produced by [Canu](https://github.com/marbl/canu/releases). Specifically, the GFA file produced from our attempt at a _Nippostrongylus brasiliensis_ genome assembly:

* [GFA file](data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa.gz)
* [Genome assembly](https://www.ebi.ac.uk/ena/data/view/GCA_900200055) (for reference, not used in this tutorial)

The final image also includes length data from the existing [_Nippostrongylus brasiliensis_ genome assembly](http://parasite.wormbase.org/Nippostrongylus_brasiliensis_prjeb511/Info/Index/) that was assembled by the [Wellcome Trust Sanger Institute](http://www.sanger.ac.uk/):

* [PRJEB511 length data](data/lengths_Nb_WTSI.txt.gz)

This length data was generated from the *Nippo* assembly by using the `fastx-length.pl` script from my [bioinf-scripts](https://github.com/gringer/bioinfscripts) repository:

    /bioinf/scripts/fastx-length.pl nippostrongylus_brasiliensis.PRJEB511.WBPS9.genomic.fa | gzip > lengths_Nb_WTSI.txt.gz
    
_Note: when the location `/bioinf/scripts/` is used in subsequent steps, it refers to the above repository_
