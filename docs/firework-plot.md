# Genome Firework Plot

A tutorial by David Eccles about representing a genome in a visually-interesting form.

<img src="pics/genome_firework_Nb_small.png" alt="Genome firework plot for Nippostrongylus brasiliensis" title="Genome firework plot for Nippostrongylus brasiliensis" width="512"/>

## Preparation

This tutorial uses the GFA file produced by [Canu](https://github.com/marbl/canu/releases). Specifically, the GFA file produced from our attempt at a _Nippostrongylus brasiliensis_ (_Nippo_) genome assembly:

* [GFA file](data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa.gz)
* [Genome assembly](https://www.ebi.ac.uk/ena/data/view/GCA_900200055) (for reference, not used in this tutorial)

The final image also includes length data from the existing NCBI [_Nippo_ genome assembly](http://parasite.wormbase.org/Nippostrongylus_brasiliensis_prjeb511/Info/Index/) that was assembled by the [Wellcome Trust Sanger Institute](http://www.sanger.ac.uk/):

* [PRJEB511 length data](data/lengths_Nb_WTSI.txt.gz)

This length data was generated from the *Nippo* assembly by using the `fastx-length.pl` script from my [bioinf-scripts](https://github.com/gringer/bioinfscripts) repository:

    /bioinf/scripts/fastx-length.pl PRJEB511.WBPS9.genomic.fa | \
      gzip > data/lengths_Nb_WTSI.txt.gz
    
_Note: when the location `/bioinf/scripts/` is used in subsequent steps, it refers to the above repository_

The contig length information was extracted from the GFA plot and converted into the same space-separated `<length> <id>` format:

    gunzip data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa.gz
    grep '^S' data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa | \
      awk '{sub("LN:i:","",$4); print $4,$2}' | \
      gzip > data/lengths_ONTCFED.txt.gz

This tutorial also uses [R](https://www.r-project.org), [Bandage](https://rrwick.github.io/Bandage/), and [Inkscape](https://inkscape.org):

 * https://www.rstudio.com/products/RStudio/ -- RStudio, an R user interface
 * https://rrwick.github.io/Bandage/ -- Bandage homepage
 * https://inkscape.org/release/ -- Inkscape download page

## Initial Concept Image

Most of the preparatory work required to make one of these plots from an arbitrary assembly is already available in my own length histogram R script and in Bandage:

    /bioinf/scripts/length_plot.r -h lengths_ONTCFED.txt.gz

Here is what the resulting `MinION_Reads_SequenceHist_ONTCFED.png` looks like:

<img src="pics/MinION_Reads_SequenceHist_ONTCFED.png" alt="Vertical length histogram for Nippo assembly" title="Vertical length histogram for Nippo assembly" width="512"/>

Bandage will produce, by default, an image of *all* contigs:

    ~/install/bandage/Bandage load Nb_ONTCFED_65bpTrim_t1.contigs.gfa
    

Click on the 'Draw Graph' button at the left to display the contigs:

<img src="pics/bandage_drawGraph.png" alt="Bandage plot of contigs"  title="Bandage plot of contigs" width="512"/>

To save as an SVG image, use `File -> Save image (entire scene)`, choose 'SVG' as the file type, and change the extension in the _Name_ box to `.svg`:

<img src="pics/bandage_saveAs_SVG.png" alt="Saving as SVG with Bandage"  title="Saving as SVG with Bandage" width="512"/>

This SVG image can then be loaded up in Inkscape and the *Page* exported as a PNG file via `File -> Export PNG image...`. Here the width of the exported image has been set to 1024 pixels:

<img src="pics/inkscape_export_PNG.png" alt="Exporting as PNG with Inkscape"  title="Exporting as PNG with Inkscape" width="512"/>

Resulting in the following image:

<img src="pics/genome_contigs_all.png" alt="Image of all contigs with random colours" title="Image of all contigs with random colours" width="512"/>

_Note: The intermediate Inkscape step is used (rather than exporting directly to PNG from Bandage) because subsequent steps will use Inkscape to modify the image._