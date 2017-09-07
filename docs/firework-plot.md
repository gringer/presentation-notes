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

## Counting Links

The GFA file needs to be processed to work out the number of contigs in linked subgraphs of the assembled genome. The `igraph` package is very useful for this. The only thing needed is the linking between one contig and the next, so some initial processing with `awk` is done to make the loading easier. Link lines (beginning with `L`) are extracted, and the second and fourth fields are extracted (containing contig names). Some links appear more than once in the Canu GFA output, so an additional pass through `uniq` is carried out:

    grep '^L' data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa | \
      awk '{print $2,$4}' | sort | \
      uniq > data/Nb_ONTCFED_65bpTrim_t1_contigLinks.txt

This can then be loaded into R and converted into an undirected graph. The links are filtered to remove contigs that link to themselves:

    > library(igraph);
    > links.df <- 
    +   read.table("data/Nb_ONTCFED_65bpTrim_t1_contigLinks.txt",
    +     col.names=c("from","to"), stringsAsFactors=FALSE);
    > links.df <- subset(links.df, !(from == to));
    > links.graph <- graph.data.frame(links.df, directed=FALSE);

The clusters containing subgraphs are identified. The `table` function is used to identify where to put the breaks for the histogram, and shows that beyond 11, the number of links in a graph is very large and might as well just be "lots":

    > links.clusters <- clusters(links.graph);
    > table(links.clusters$csize);
    
R Output:

      2   3   4   5   6   7   8   9  10  11  26  27  34  38  41 
    149  55  22  14   6   3   2   4   2   1   1   1   1   1   1 
     57  76 106 
      1   1   1 

The association between contig names and subgraph cardinality is stored in a new data frame:

    > contig.links.df <- 
    +    data.frame(contig=names(links.clusters$membership),
    +               linkID=links.clusters$membership);
    > contig.links.df$card <- 
    +    links.clusters$csize[contig.links.df$linkID];

The comma-separated list of contigs can be stored in a file for filtering with Bandage. Bandage removes the initial `tig` and leading zeroes, so these are removed as well for the output file using `sub`:

    > cat(sub("^tig0*","",contig.links.df$contig), sep=",",
    +     file="data/linked_contigs.txt");

However, on loading these into Bandage via `Graph drawing -> Scope: Around nodes`, it is apparent that there are still too many "boring" subgraphs, where the contigs are linked in an unambiguous fashion:

<img src="pics/bandage_linear_links.png" alt="Linear links in Bandage"  title="Linear links in bandage" width="512"/>

Fixing this requires paying a bit more attention to the link structure of the GFA plot. It will be assumed that any contigs involved in these links will be treated as "linear / unlinked".

## Counting Non-trivial Links

In this case, the direction of the link is preserved, so that the associated contig end can be identified. A subgraph is considered "complex" if it contains at least one non-trivial link, i.e. if the same contig end is linked to more than one contig. Again, the link lines in the GFA graph are filtered, but this time showing direction:

    grep '^L' data/Nb_ONTCFED_65bpTrim_t1.contigs.gfa | \
      awk '{print $2,$3,$4,$5}' | sort | \
      uniq > data/Nb_ONTCFED_65bpTrim_t1_contigLinksDir.txt

A bit of preprocessing is needed in R. The contig names will be appended with `_S` or `_E`, depending on which end of the contig is linked, which changes depending on whether it is a `+` or `-` connection, and whether the contig appears on the left-hand side or the right-hand side. Complex contig joins are identified by looking for duplicates. Finally, start and end contig fragments are linked to ensure that they appear in the same contig cluster.

    library(igraph);
    links.df <- 
    read.table("data/Nb_ONTCFED_65bpTrim_t1_contigLinksDir.txt",
      col.names=c("from", "fromDir", "to", "toDir"), 
      stringsAsFactors=FALSE);
    links.df$fromSig <- paste0(links.df$from,
      ifelse(links.df$fromDir == "+", "_E", "_S"));
    links.df$toSig <- paste0(links.df$to,
      ifelse(links.df$toDir == "+", "_S", "_E"));
    newLinks.df <- unique(data.frame(from=links.df$fromSig,
      to=links.df$toSig, stringsAsFactors=FALSE));
    complex.contigs <- 
      names(which(table(c(newLinks.df$from, newLinks.df$to)) > 1));
    contigNames <- unique(c(links.df$from, links.df$to));
    newLinks.df <- 
      unique(rbind(newLinks.df, 
        data.frame(from=paste0(contigNames, "_S"), 
        to=paste0(contigNames, "_E"))));
    links.graph <- graph.data.frame(newLinks.df, directed=FALSE);

Again the `clusters` function is used, but the `csize` value can no longer be used because of both sides of contigs appearing in the same cluster:

    links.clusters <- clusters(links.graph);
    names(links.clusters$membership) <-
      sub("_[SE]$","",names(links.clusters$membership));
    links.subgraphs <- tapply(names(links.clusters$membership),
      links.clusters$membership, function(x){
        unique(sub("_[SE]$","",x));
      });
    table(sapply(links.subgraphs,length));

R output:

      1   2   3   4   5   6   7   8   9  10  11  26  27  34  38 
      4 149  55  22  14   6   3   2   4   2   1   1   1   1   1 
     41  57  76 106 
      1   1   1   1 

