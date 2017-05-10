# London Calling 2017

Presentation notes on London Calling, written by David Eccles.

## Day 1 (May the Fourth be with You)

### Lightning Talk -- David Eccles

#### Sequencing a parasite genome

 * A long history of sequencing, started doing his own prep with R9 kit
 * Runs in October / November last year were bad
   * ONT offered to do the sequencing for them
 * Five sequencing runs, all better than 20 previous runs at institute
 * One run amplified from a single worm
   * Metagenomic profile from a 35,000-read subset
 * One run had a very long read length "hump"
   * Sonication + Tip20 extraction
   * Run N50 was better than current reference genome
 * Poster talks about assembly discoveries

### Philipp Euskirchen

[DE: starting to feel jet lag problems]

#### [History of brain tumour diagnosis]

#### Diagnosis
 * Tumours can have very different morphologies but be molecularly similar
 * Diagnosis is preferred if it leads to a prognosis
   * e.g. identification of an H1 mutation; a 1p or 19q codeletion strongly correlated with prognosis
   * For subgroups of medulloblastoma, prognosis depends on the subtype
 * How can diagnosis be implemented?
   * There are four subtypes of medulloblastoma based on their transcriptomic and methylation classification
   * A lot of different machines and protocols
 * Two paradigms
   * Low-pass whole-genome sequencing, producing results within a day
   * Deep amplicon sequencing for point mutations and GC-rich regions

#### Copy-number profiling
 * DNA with rapid kit and sequencing
 * Used out-of-the-box tools from the supermarket
 * Read numbers are not gigantic, but could still generate decent profiles within a day
 * Visually explored the EGFR region on chromosome 7
   * Saw focal amplication
   * Was able to identify split reads at both ends
   * Remapped to a synthetic sequence for collapsed reads
   * Confirmed by sanger sequencing

#### Methylation sequencing
 * Can use the same reads as used for copy-number profiling
 * Compared with Illumina 450k chip
 * Wanted to know if this could possibly work for nanopore
   * Classifier error changes things; don't know in advance what CpG sites will be seen
   * Compared with Illumina, methylation profile has a nice correlation

#### Pan-cancer classification
 * Classification from a while different method
x * Works for IDH mutant and medulloblastoma
 * What works in brain tumours should have benefit for other cancers

#### Real-time read depth monitoring
 * 10-20 minutes until a region is 1000X-covered, including a GC-rich region
 * Results mostly in line with Illumina data

## Breakout 3 Discussion
 * Nanopolish doesn't work so well with the new version of albacore
 * ONT wants to work to produce a better base caller, want to avoid needing nanopolish
   * Don't want a base caller that introduces systematic error
 * Damien has tried tracking virus with mouse samples, seen different diversity in different tissues
   * With direct RNA sequencing, even with 10^6 to 10^7 copies per ml, sill gets swamped out by the host
 * What is the optimum depth?
   * Read length matters
   * With good long reads, 20-30X is good enough
 * For clinical use, need to be very sure about accuracy
   * There are applications where read-until will be useful

### Clive Brown

#### Novel statements selected by David Eccles
 * Thinking of making a GridION version that has PromethION flow cells
 * PromethION Will also do a 4-way MUX (max 10,400 wells)
 * New chemistry coming which will increase MinION yield by 20-30%
 * Accuracy should get to 99.9% [q30] by the end of this year (possibly this summer)
 * Updated pore [technology development] has two times read-ahead, and should be able to model up to 30bp homopolymers
 * A reasonable user will be able to knit their own clothes using nanopore packaging
 * Have been able to get a metal-metal interface working on the Flongle
 * A sequencer that doesn't do base calling -- Clive's pet project for the rest of the year
 
[evening for Clive brown is after 6pm]

#### Goal of ONT: Anyone sequencing anything anywhere

* Most products are targeted at this gooal
* Sequencing is becoming more ubiquitous
* When things get out of the lab, people find out more uses
* People have gone out and found real applications
* Can go back and mark Clive's homewark as a permanent record

#### Clive explaining nanopore sequencing

* Protein pore at the moment
* Pore will scan the entire sequence length
* Other technologies are typically limited by photo damage
* Sequencing is fast: per-molecule cycle time is milliseconds
 * Should have significant implications in the future
* Fragment length is effectively read length
* No reason why full-length chromosomes can't be done
 * Histones shouldn't hinder sequencing
 * *What if we could do whole chromosomes?*

#### MinION

* Probably all people at the conference are MinION users Have always
* Felt MiNION would be good enough; it is the democratising feature of ONT
* Sits in no-mans-land because a lot of electronics are in the flow cells
* There are now about 4,500 users, ideally want 10,000-15,000
* Workflow is never linear with the MinION
 * Can analyse data in an hour, some people are beginning to do this by not just firing and forgetting it

#### Lab Work

* Clive is not good at lab work, but has had a go anyway
* Clive has run what ONT has to see how hard it was
* In half an hour got 140µg DNA using a Qiagen kit
* Could load flow cells (got one bubble once, but easily fixed by other ONT staff)
* First attempt used 30 flow cells
* Subsequent run on GridION, 5 flow cells at 14-15 gigabases
 * Some users have got 16 gigabases
 * Some have trouble with getting anything
 * Clive used reagents that we have now, demonstrating that the GridION can be used now
 * Another run used newer chemistry (not available yet in the community), and achieved 24 gigabases per flow cell
 * Now has over 200 gigabases, people can do with that whatever is ethically reasonable
 * Probably some protocol issues; some samples don't yield much DNA
 * People are now using VolTRAX to give consistent yield; flow cell is now tip top

#### GridION

 * Started as a modular rack-mounted system with reagents, dynamically forming membranes and sequencing
 * Abandoned this approach, but left it parked on the website
 * New GridION is modular
 * **Thinking of making a version that has PromethION flow cells**
 * Will have Run Until and Read Until
 * People are licensed to use the GridION for commercial use
 * Can alternatively use five MinIONs, with laptops, software, etc.
   * Process is all automated on the GridION
 * Box can do real-time online basecalling

##### FPGAs

 * Internal effort to map data processing into FPGAs
 * Can call 1 million bases per second at the moment
 * Not as much success with GPU / CPU
 * Gives very fast feedback, even with a high number of pores

##### Funding model

 * ONT doesn't like the idea of how people pay for things
 * Preferred model is consumable only; almost Pay-As-You-Go, with contracted minimum
   * This has been the most popular model

##### Manufacturing

 * Box is very highly manufacturable
 * After June, should be able to make 3 per day
 * Shipping in about 48 hours
 * Flow cells have about a 48 hour delivery
 * First GridION out on the 15th May, might be the same GridION used for the Cliveome, but maybe not

#### PromethION

 * Designed 3 years ago, everything is completely new
 * Was designed to take on Illumina
 * In principle, will generate more data than a NovaSeq
   * Head room is so much that even if NovaSeq is brought forward, will still be competitive
 * Have 12-14 boxes out now, produces a ton of data
   * **Bulk purchase cost of flow cells is about $600**
   * Just sit tight
 * Can de-batch the entire workflow
   * e.g. 50 samples on a Wednesday, one sample the next day; more real time and less batched
 * PromethION is licensed as fee-for-service
 * Flow cell has a different layout
   * A few issues remain, but nothing that hasn't been seen before with the MinION
   * Even with issues, getting 22 Gb in 22 hours [DE: I recall there was a '23' somewhere]
    * Active unblock is not yet fixed on the PromethION
    * Flow cell run time has been increased to 4 days
    * **Will also do a 4-way MUX (max 10,400 wells)**
 * Even if just using similar output to a MinION, is still better than NovaSeq

#### PromethION Processing

 * Increased speed of sequencing
   * Internally have a run at 1,000 bases per second
 * Couldn't fit processing into the original design
 * Solution is to make as separate computer
   * Will eventually shrink by about 1/3
 * Composed mostly of FPGAs, will allow complete base call in real time
 * Lower module will be a network switch
 * Inside is a server with a skin
 * FPGAs with neural networks
   * Loads of them out and configured
 * Steady incremental improvement

#### PromethION evolution
 * Firmware tweaks are increasing processing to 4.8 Tb
 * Ultimately will retransfer computing, end up with a single server
 * People should sit tight for this one; this is the box that will turn the supertanker market around

#### MinION yields
 * Customers are getting pretty good yields
 * Should be able to get 20 gigabases per day, but more realistically 6 or 7
 * Someone got 16 gigabases [one run], Clive wishes they would tweet that run
   * 16 gigabases is a realistic expectation
   * **New chemistry coming which will increase that yield by 20-30%**

#### MinKNOW
 * Improving rapidly
 * Should be able to wash out flow cell sample, fix sample prep, and move on
 * Want to get rid of the priming step
   * Just load the flow cell without priming
   * This flow cell should be ready [DE: i.e. almost shippable]
 * Working on recommendation list
 * Radically simplifying the software
   * A team is working on redesigning the user experience
   * People should just know how to run MinKNOW
   * After a time, all base calling improvements will be in MinKNOW
   * Process should be very straightforward

#### VolTRAX
 * Moving along pretty well
 * After a time all protocols will be moded onto VolTRAX
 * By the end of the year, should be using lyophilised reagents
 * Multi-sample flow cells
 * Quantification + possibly amplification
 * Available at the end of the year (VolTRAX mk 1)

#### Raw signal
 * Another slide Clive hates
 * Clive doesn't like the evnets
 * Breaks down at fast speed
 * Event data bloats the files

#### Algorithm updates
 * 1D will improve
 * 2D idea: template + hairpin + complement
   * need to replace with something new
 * 1D²; make the second strand hang around for longer so second strand follows through
 * 96% modal accuracy, limited by how data is combined
 * Should get to 1% error
 * 1D² will be implemented next week

#### R9.5
 * New pore
 * Backwardly compatible
 * Coming 8th May
 * All ready to rock
 * 2D can now go into the dustbin of history
   * Nanopore killed 2D today (please tweet)
 * Very little is different between R9.4 and R9.5
   * What is different should be fixable in software

#### Homopolymers
 * If taken out, now getting pretty good numbers
 * Can do quite well, pretty much all homopolymer calls are out by 1
 * Homopolymers will go out as systematic errors

#### Basecalling
 * Still an enormous amount of headroom
 * End up with detritus of error
 * **Should get to 99.9% by the end of this year (possibly this summer)**
 * Still lots of unmodelled signals
   * e.g. there is a fungus that puts sugars on DNA
   * People here have shown that things are visible in the signal

#### New pores
 * Also working on new pores; patent has just been published on this
   * In the future, will now never replace pores, just migrate pores
 * **Updated pore has two times read-ahead**
   * should be able to span 30bp homopolymers
   * may have new pore by the end of summer

#### Raw Calling
 * A lot of work done on this
 * Captured on FPGA
 * Pretty close now to comparable performance to what is done now
 * Making available raw data base caller now
 * Any useful software will migrate to MinKNOW
 * Want to just output FASTQ

#### Removing cold-chain system
 * Can now store and ship new packaging in wool
   * Creating jobs for sheep
   * **A reasonable user will be able to knit their own clothes using nanopore packaging**
 * A lot of work being done to make a lyophilised reagent system
 * Performance is comparable to conventional wet reagents
 * 1D² version will be available shortly

#### Pipettes
 * That leaves pipettes; pipettes have to go
 * Need to encapsulate prep into a dry / warm container
 * Reagents put into prototype tube
 * There will come a point when you can put a swab in, and 15-20mins later start looking at reads
 * Not quite there to show with date or product yet

#### Increasing sensitivity
 * Can currently do well down to about 1ng
 * can go even lower (with reduced yield)

#### Additional device with new name needed
 * Dongle with FPGA and firmware
 * Can basecall MinION sequences
 * Encapsulated supercomputer
 * Computer can be cheap and small
 * Device will eventually be able to work on its own (with connected power supply)
 * Should be out by the end of summer
 * FPGA currently Intel Arria 10, runs at 10Mb per second
   * Next version will be 7Mb per second
 * Theme is portability: want to make things as easy as possible

#### Flongle
 * Electronics moved onto dongle
 * One-off buy, can be thought of as a mkII MinION
 * Cheaper flow cell snaps into adapter
 * Fewer channels, higher volume [DE: presumably production volume], cheaper price
 * The substrate device... the MinION they should have made
   * Very significant for ONT
   * Should be out by the end of the year
 * Previously had gel-gel interface
   * **Can now get metal/metal interface**
   * have prototype chips and membranes at the other end of the scale
   * was actually a prototype used for the SmidgION

#### SmidgION
 * Won't be around this year, but it will come
 * Chris has been able to run a MinION on a mobile phone

#### Hypothesis-driven sequencing
 * Looking to develop this
 * There are a lot of things that can be done with nanopores
 * Blob counting: sequencing of site-specific things
   * Let sequences whizz through the pore
   * Blob does the counting
   * Very rapid yes/no sequencing
   * Getting to very rapid MinION sequencing

#### Solid-state nanopores
 * Will be solid-state Flongle; will definitely [DE: also] be a blob counter

#### Cas9
 * Can be programmed: a programmable blob
 * Target certain fragments
 * Use chemistry to select out molecules for sequencing
 * Can use the same trick for detection as well
 * Have pretty good working implementation of Cas9 target selection
 * Multiplexing
   * Very cost-effective for small region for thousands of samples
   * "Cas Me If You Can"
   * Custom Cas9 provided by ONT
   * Also planning to make pre-made versions

#### Dates
 * May
   * MinKNOW 1D² 9.5
   * 8th: new flow cell
 * June 17th (Clive Brown's birthday): raw basecaller
 * June 30th: new cDNA kits
 * July: new ambient shipping methods
 * September: Cas Me If You Can

#### Epitome
 * Make standard Bioinformatics workflows
 * Platform is now pretty mature

#### Is Basecalling Necessary?
 * Do you need to basecall and align?
 * Have been teaching neural networks to look at raw signal to decide what species it is
 * Want to go from squiggle
 * There are cases that don't require base calling
   * **A sequencer that doesn't do base calling -- Clive's pet project for the rest of the year**

#### Questions
 * Gordon's ambition is to put the Flongle in as a diagnostic device
 * Consensus reading errors: just a matter of knocking downm the obvious problems
   * If ONT runs into non-software problems, just need to change the chemistry

## Day 2 (May fhe Fifth)

### Gordon Sanghera

#### Throughput
 * Since shifting to the 9 series, there has been an exponential move to throughput [DE: it was exponential prior to that, but no one cared because it was exponentially low]
 * A lot of issues will be application-specific
 * 20 gigabases is the output of a 2-day flow cell, but ONT wants to move to 3 days
 * Hope to get all customers to 15-20 gigabases
 * No reason why the flow cells can't reach their theoretical maximum
 * Sensor chip is designed to handle 1000 bases per second
   * Might be able to adjust sequencing speed in the future for application-specific uses
 * Is there an underlying single molecule optical[?] limit to accuracy?
   * Accuracy doesn't seem to have a limit with nanopore
   * 100% Accuracy is the target
   * No fundamental reason why this is not achievable
 * R9.5 is squeezing the last 10% out of the flow cells

#### Marketing
 * The challenge is getting the technology to market
 * In 2017, we might be ready for prime time
   * We are answering biological questions that other platforms cannot solve
 * Innovating quickly: it is in our DNA
   * ONT cannot rest on their laurels
   * We are disruptive innovators

#### Flongle
 * This will be big
 * Thinking about crossing the chasm into diagnostics [repeated multiple times]
   * If you could, you would probably want to sequence the whole of HIV
 * Flongle allows ONT to be applied
   * Can be HIV or HepC
   * Can delete what is not needed
 * Will challenge PCR diagnostics, a tech that has been around for 25 years
 * Next year, flongle will be available as a registered diagnostic device

#### Disruption
 * The challenge is to disrupt the diagnostic market [etc....]
 * DNA information will disrupt everybody
 * [video about student education; students having the opportunity to use the MinION]
 * Children will say, "You didn't *know* that beef was actually Kobi beef, you just ate it?"

### Nick Loman
 * Setting expectation levels corretly for this talk: The answer is NO! [DE: referring to a statement about the suitability of the MinION in the title]

#### Dr Seuss
 * People with young kids use kids books for inspiration
 * The MinION has sequenced almost everywhere
   * On a boat
   * With a goat
   * On a plane
   * On a train
   * Down some holes
   * At the poles
   * In outer space
   * At quite a pace
 * One notable place where it hasn't sequenced; more aboout that later

#### 2015
 * Nick's last talk at London Calling was in May 2015
 * Very excited, because they had done successful sequencing in New Guinea, with results back on a time scale of days
 * One genome was sequenced per flow cell
   * Generated sequence quickly enough to feed back to WTO
   * By May, had sequenced 50% of Ebola cases in Guinea
 * Really important findings came out of that ebola work
   * Data needs to be shared as quickly and as ethically as is possible
   * Could measure cross-border transmissions
   * When a new case popped up, could identify if it was linked to other existing cases

#### Ebola progression
 * It was originally thought that Ebola was over by September / October, but a number of additional flare-ups happened
   * Used MinION to identify one case
   * The seminal fluid of a survivor was infected
   * The virus was "frozen in time"
 * [Video / animation: 1600 Ebola Virus transmissions, representing 5% of all outbreaks, 30,000 cases, 10,000 deaths]
  * [10.1038/nature22040](http://dx.doi.org/10.1038/nature22040)
  * Many opportunities to stop Ebola from moving
  * MinION/NickSeq wasn't deployed until April 2015
  * Is there a case for getting sequencing done early?

#### Zika Project
 * Introduced last year
  * Unbelievable arrogance in the grant application: claimed that they would sequence 750 genomes
 * For epidemiology, see Oli Pybus' talk

#### Concentration issues
 * Zika was almost impossible to sequence using normal procedures
  * Doesn't work with metagenomic techniques
  * cT values for PCR of 34 to 36
 * Pathogen enrichment challenges
  * At the moment, 100ng of DNA is required for MinION sequencing
  * Can be done by PCR, whole-genome amplification, or bait probes
  * PCR-based approach represents a pragmatic, or easy way

#### PCR Primer design
 * Josh spent a couple of months working on sequencing
 * Developed "Primal Scheme": an application to generate a multiplex panel for siling sequencing
 * Can now sequence Zika, with reasonably complete genomes up to a cT of 36
  * Some amplicons drop out more than others
 * Now have everything in place to do this outbreak stuff in real time

#### Yellow Fever
 * Currently an outbreak in Brazil
 * Process is much quicker this time
   * Biggest hold-up was taking about a week for the university to process the primer order (actually not that bad)
 * Josh and Nick didn't have to go this time
   * Can now enable colleagues to do this
   * Could do six genomes per flow cell, 1-4 million reads
   * Yellow fever has a low cT, so easier to sequence
 * Now have easy-to-install workloads

#### Health Service Publicity
 * Check out Nick above the escalators at Euston

#### Working with high-yield MinION flow cells
 * Mix rapid kits together, pull out single contigs
 * Yield improvements make this stuff very feasible
 * Someone should sequence inside whales
 * There is a mapping from whale weight to read length
 * Still haven't got a megabase read
   * A flow cell is running outside, Nick has been checking during the conference
   * Next improvement to be trialled: extracting *E. coli* from an agarose plug
   * Have got read N50 up to 150kb
   * Can get an entire *E. coli* genome in seven reads
   * longest read so far is 886kb
 * Could we trivially finish a genome?
   * With a 30X dataset, could probably get human contig N50 to 50Mb

#### Wish list
 * All of Nick's wish list from 2015 is done, except for low-input

#### NHS -- where sequencing is not done
 * Sort it out and bring it to the UK
 * Money is an issue
 * Clinical microbiologists have been reluctant
 * Physicians seem quite into it
 * A lack of will; people just need to go and do in

#### Questions / Answers
 * Nick hasn't looked at why people are resistant
 * Could do pathogen discovery and RNA at the same time

### Lightning Talk -- Niranjan Nagarajan

#### Human Gut microbiome
 * Large ongoing project
 * Seven questions
   * Host/microbial factorss
   * Evolution of resistome
   * Novel plasmids
   * Strain dynamics
 * Begin with a pilot project, using long reads for metagenomic assembly
 * Then use real clinical samples
   * The aim is to maintain the diversity of the community
   * Many reads are longer than 5kb
 * Carried out an analysis on a single patient
   * Significant enrichment of *K. pneumoniae* with different abundances
   * N50s of hundreds of kilobases
   * Were able to identify extended-spectrum lactamase gene
 * Observe plasmid dynamics and rearrangements in plasmids

### Lightning Talk -- Michael Boemo

#### DNA base analogues
 * Use analogues to look at DNA replication
 * Pulse of thymidine analogues, then can work out where the origins of replication are in the genome
 * How well does it work?
   * Analogues make quite a difference in the signal
   * Working pretty well in synthetic substrates
 * Don't care about the exact base, just interested in the region

### Lightning Talk -- Celine Bigot

#### Free Pathogen Identification
 * NGS enables the detection of microbial species without a-priori models
   * MiSeq, MinION, PGM were all tested
 * Working on own reference material, plus the Zymo community standard, plus other types of samples
   * CNRGH standard has 10 bacteria, one fungal, and one other
   * Standard is still in progress
 * Interesting preliminary analysis
   * Has done a WIMP analysis
 * Based on processing time, the MinION and MiSeq are preferred to the PGM

### Lightning Talk -- Scott Gigante

#### Basecalling (Nanonet)
 * Custom neural net basecaller; replaced with black box in the slides
 * Wants to do away with Hidden Markov Models
 * Used two *E. coli* libraries, one treated with methyltransferase, one unmethylated by PCR
 * Used EventAlign for associating the basecall with events
 * Training neural networks is not easy
 * Feedback used with training, issues are often only realised weeks later
 * Using a longer kmer results in a faster training loss, but lower error with increasing kmer size
 * It is hard to judge when the training is complete
 * GLM calls 99% of sites correctly
 * Nanonet provides an excellent opportunity for training

### Lightning Talk -- Ben Matern

#### Identification of HLA Variants by cDNA sequencing
 * Genes are highly polymorphic
 * Interesting to look at the DNA and RNA
   * RNA has alternative splicing
 * Used GMap, which can insert introns (splicing-aware mapper)
 * Has made a software platform, an alternative to laboratory techniques
 * Aligned boundaries mapped to the reference genome
 * Can take expression profiles and cluster into expression patterns

### Lightning Talk -- Benjamin Istace

#### Banana Genome
 * One of the most sold / produced fruit around the workd, 100 million tonnes
 * Most edible species of banana are from two hybrids
 * Sequenced and assembled two genomes, looking at one now
   * Long fragments were selected with the BluePippin
 * Ran four R9.4 runs, generating 22 gigabases of reads
 * Peak [modal] read length was between 25-30kb
 * Read correction with Canu, processed into SmartDenovo
 * Produced a genome with 704 contigs, N50 of 1.85 Mb

### Lightning Talk -- Matthew McCabe

#### Sequencing of BRD viruses
 * Using the rapid sequencing kit
 * Over 20 viruses that are associated with disease
 * Diagnosis at the moment is mostly by PCR
 * Looking for a rapid, untargeted sequencing approach
 * Can untargeted MinION do this?
   * 4 cultures, each infected, pooled, and nuclease added to remove host DNA
   * Non-exised nucleic acid goes into the RAD kit
   * Got 7,000 reads in the pass folder
   * BLAST top hit took 9 hours
   * Local viral sequence took about 10s
   * 99.6% of reads were correctly identified

### Lightning Talk -- Libby Snell (ONT)

#### Direct RNA Sequencing

* Kit is available now from the ONT store
 * Sequencing of RNA molecule directly; it's possible for things that maybe couldn't have been done previously
 * Not possible using any other technology
 * Up and coming... ONT wants to get rid of cDNA; it's only there while they're stabilising the technology
 * Ideally want to move to a 30-minute rapid preparation
   * Ligate, wash, and load
 * Potentially allows for a lower input amount
 * Tested with quantitative samples: Ambion ERCC, Lexogen spike-in (SIRVs)
 * Single-stranded prep works, and a 2D prep works (with RNA stabilised by cDNA)
 * Getting full-length transcript coverage
   * Currently output is about 70% of what it should be, probably due to blocking
 

### Direct RNA Breakout -- John Tyson

[DE: I missed this; I was distracted talking to David Stoddart about
chimeric reads]

### Direct RNA Breakout -- Rachael Workman

#### Using *C. elegans* for direct RNA sequencing
 * comparing direct RNA to cDNA
 * looking at basic differences, what to expect
 * Used strand switching and ligation sequencing
 * No need for PCR when working with *C. elegans*, can get 30µg cDNA easily
 * Called datasets with both older and newer basecallers

#### Yield
 * Direct RNA had less yield (as expected)
 * Direct RNA had shorter reads
 * RNA transcripts were perfectly fine for *C. elegans*
 * lower MAQ alignments with RNA
 * Once MAQ filtered, match percentage was similar between RNA and cDNA

#### Comparing to Wormbase transcripts
 * cDNA found most transcripts
 * 1140 transcripts were detected in RNA, but not in cDNA
 * Filtering out by base length didn't throw out much

#### Full-length transcripts
 * More degredation in the RNA run
 * Looking at RNA alignments, get degredation in the UTR
   * Might be aligner clipping
 * Other end, more exon dropout, need to look at the soft clips

#### Abundance comparison
 * RNA tracked cDNA fairly well (R=0.76)
 * Would be interesting to look at an Illumina run for comparison

#### Homopolymer calling
 * cDNA and RNA were pretty identical
 * Initially compared without homopolymer correction
 * Also compared with transducer basecalling
 * [DE: With the transducer, the amount of C homopolymer bases exactly matched the amount of G bases]

#### Take-home messages
 * Library preps were robust for both cDNA and RNA
 * RNA will get better
 * You could stop doing Illumina, switch to cDNA and be fine

### Direct RNA Breakout -- Chris Vollmers

#### Single-cell RNASeq
 * Using nanopore technology to improve
 * Human cell atlas is now picking up pace
   * Looking at the types of every human cell
   * Illumina is good at defining gene expression of single cells
 * Most single cell library preps involve full-length cDNA as an intermediate step

#### B-cells
 * Lab's primary interest is in B-cells
 * Would love to do direct RNA seq, but cells contain about 10 femtograms of RNA
   * A couple of orders of magnitude less than what is needed
 * Was waiting [a *long* time] for Illumina run results to get back
   * Why not put cDNA into a MinION flow cell?
   * Designed indexes by randomly generating 60bp random sequences
 * Trying to quantify gene expression, ended up breaking tools
 * Looked at the overlap between Illumina and Nanopore expression
   * Got fairly good correlation, r = 0.9 approx.
   * Nanopore doesn't seem to have a length bias
   * Cutting is needed for short transcripts, but can't be done
   * [Possible that the inability to cut small RNA molecules means they are under-represented in Illumina reads]
 * Used SIRV / synthetic spike-in molecules as a control
   * Made 10fg of DNA, trivially easy and fairly quantitative
   * Wanted to get by without reference genome annotation

#### Pipeline -- MandalorION
 * Only wrote this because it wasn't available elsewhere
 * Picked up stuff [transcript isoforms] that wasn't in the reference sequence
 * Sort reads based on the distribution, create [model] isoforms
 * Get approximately linear correlation (r=0.97) when comparing reference-free versus reference-based mapping
   * CD20 gene -- found an exon that wasn't in the reference assembly
   * Looked at assembly by Trinity, found assemblies that were just really bad
 * Working on systematic way for naming isoforms [odd that this doesn't exist already]

### Direct RNA Breakout -- Andrew Smith

#### Direct sequencing of 16s rRNA
 * Very abundant in cells
 * Getting to 16s RNA levels from gDNA would need 13-14 rounds of PCR
 * If we could get a hold of 16s, woud be able to do a lot of good things
 * Needed to customise the ONT RNA kit a bit
   * Kit adapter was modified to be complementary to the 3' end of 16s
   * This is a very well-conserved gene at the 3' end

#### Proof of principle
 * Working with highly-purified 16s
 * 1.5kb rRNA gene
 * Proof of concept carried out first on *E. coli*
 * For methanococcus sequencing, needed to tweak the adapter a little bit
 * With increasing read length, it becomes very much easier to classify things
 * Reads that were over 1000 bases had 98% classification accuracy

#### Coverage hump
 * Hump at a particular region
 * Very consistent base miscall
 * Compared MRE600 *E. coli* with RsmG-delta
   * Base call was different
 * Nanoraw showed a modified ribonucleotide in the 16s gene
   * This is a mechanism by which some microbes can defend against other microbes
 * Wanted to show that this could be detected at other regions
   * Pronounced low-amplitude signal from the modified strain
 * Also found pseudouridine modification
   * Very exciting to be able to detect this
 * Ion current change affects current at adjacent regions
   * Probably due to 5-6bp nucleotide window from which the current is sampled

#### Diagnostic tool
 * Titration with lower and lower amounts of 16s
 * Could still see reads even at 5pg
 * Depending on the amount added, could find result in 20s
   * Basically the earliest opportunity for a read sequence to appear was when the first 16s reads came through

### Direct RNA Breakout -- General Discussion and Questions

 * Should we stop calling RNASeq [the stuff done on other systems] RNASeq?
   * We are fighting an uphill battle
   * The community will eventually come to a consensus sequence
 * Neither GMap nor BLAT use a [transcript] reference; they don't rely on genome annotations
 * Just doing cDNA is losing a lot of information
 * Read-until could get rid of ribosomal sequences
 * Direct RNA with a polyA primer is the only thing that can get the correct length of the polyA sequence
   * No need to do VT23, can just use T23
   * Can tell mispriming events when they happen
   * [DE: Why not use a polyT primer with a double-stranded component?]
   * SIRVs polyA tail is [always] 30bp
 * mRNA only makes up 15% of total RNA sequences
   * There is lots of rRNA
   * Also a whole number of small RNA molecules

### Plenary Panel -- Raymond Hulzink, KeyGene

#### Background
 * Wet lab biologist
 * Started in 2014 with the MinION
 * In 2016, started doing serious MinION sequencing
 * In 2017, started sequencing the melon genome, and some BAC clones
 * Recently obtained the PromethION, have done a lambda trial
 * Will use VolTRAX for plant genomic DNA

#### Plant / crop genomes
 * Large, usually polyploid
 * Long reads should resolve the genome complexity
   * As read length is increased, contig length increases
 * Plant cells are challenging
   * Very rigid cell wall, a bit in contradiction to what needs to be done
   * Have lots of metabolites, can damage DNA or reduce the efficiency of sequencing
   * Have chloroplasts and mitochondria
 * DNA isolation has no generic protocol; every plant is different
 * Understanding DNA quality is important
   * Can degrade over time
   * Comparison of fresh sample vs. ultra-pure sample, no difference in high-quality reads regardless of the isolation method or storage
   * QC changes when looking at reads longer than 50kb

#### Melon sequencing
 * Decided to use DNA that was less than one month old
 * Other crops may need purification
 * Compared 75% of the shortest reads to 75% of the longest reads
 * Longer reads have contigs over twice the length of the shortest reads

#### Generic workflow
 * Isolation of nuclei
 * Want to hunt for ultra-long reads
 * Use agarose-embedded nuclei
 * Needs a lot of work in the lab to get ultra-pure DNA
 * If the fragment length is greater than 25kb, typically end up with read lengths of greater than 15kb
 * New albacore improves the read quality
 * Expect to generate platinum assemblies from plants

### Plenary Panel -- Ivo Gut

 * This sequencing stuff is a bit of a clown act; Ivo prefers to play guitar
 * Doing de-novo sequencing on the hummingbird and houbara bustard

#### ONT History

 * ONT has actually been around since 2008, and collaborated with Ivo Gut at that time
   * Ivo got a ball of dirt as a prize
 * Ivo helped in the development of structures to do de-novo assemblies
   * Fosmid-pooled sequencing for a complex genome
   * Used to take a whole lot of complicated preps and bring it all together
   * Required some complicated manoevering and sequencing
   * Has gone on to throw every technology at it
 * As time when on, Ivo got more and more confident about nanopore
 * At some time, just took DNA and put it into nanopores

#### Houbara bustard
 * Endangered species: lives in the arid desert and is flightless
   * Hunted using other birds (which prefer airplane travel)

#### Hummingbird
 * Part of the genome 10k project, which turned into the vertebrate genome project
 * Has been sequenced using everything except nanopores
 * Got a lot of help from ONT for sequencing this bird
 * Generated about 20X coverage
 * Taking only Nanopore reads, got an N50 of 2.7Mb
   * Compared to PacBio, which was 5.37Mb N50 (but about 3 times more data)
 * Used a Canu assembly combined with Pilon

#### Houbara bustard
 * Did phenol chloroform extraction
 * 10X coverage by nanopore, together with Illumina sequencing
 * Got scaffold N50 of 5Mb
 * Last night, an additional 3 flow cells were mapped on top
 * N50 of 8Mb, with 181 contigs of over 1Mb

#### The hummingbird now
 * Re-exttracted DNA, got tissue shipped to Simon Mayes
 * As a pilot, Simon got some duck tissue for sequencing
 * Very optimistic that it can be done with long reads
 * With the MinION, there's no more difference between scaffolds and contigs

### Plenary Panel -- Christiaan Henkel

#### Genomes that have not been previously sequenced
 * Many amphibians and plants with extremely large genomes
 * True long-read sequencing
   * If 1Mb is the length of the shard, then the genome is the length of the sun and back
   * Get unique bits in a sea of repetitive content
 * Lightweight assembly
   * Assume perfect long reads
   * Just compare the ends, then assemble the genome
   * Doesn't work for repetitive regions at the end
   * So... find unique regions

#### Sequencing the eel
 * Want to know why they are critically endangered
 * Did an assembly: 860Mbp assembly, 2366 scaffolds with 1.2Mbp N50
 * Corrected with Pilon
 * Tried to compare against an older Illumina-based draft
   * Lots of tiny scaffolds unmapped
   * Some discontinuities, nanopore data almost always compares favourably

#### Tulip assembly with Tulip
 * Library assembly method called Tulip
 * Tulip production is easy, but tulip breeding is not
   * Reading a single chromosome would take a month on nanopore [serially-sequenced]
   * It is hoped that the PromethION will be good enough
 * Pilot with one MinION flow cell for sequencing
   * Surprisingly, the tulip genome is not very repetitive at all
   * Assembly should work well with the lightweight method

### Plenary Panel Questions

* Pilon polishing is a stop-gap measure
* Using other technologies (e.g. 10X, dovetail)... looking at that, but Ivo prefers using as few technologies as possible
* Data analysis -- No best practise for de-novo assembly
 * A few very smart people out there looking at different things

### Kazuharu Arakawa

#### Starting with the very basics
 * needed to do sequencing, so was investigating Nanopore
 * Looked at bacterial draft genome
   * Used MinION reads to finish genomes
   * "how low can you go?"
   * In under 1hr, was able to complete a full genome with one 4.4Mb circular chromosome and one 44kb plasmid

#### Spider silk
 * 4 times stronger than steel
 * in nature, about 10µm in diameter
 * More elastic than nylon
 * it's weird to have both high strength and high elasticity
   * has the highest "toughness" [combination of strength and elasticity] among all fibres
   * Made from proteins, so it's re-usable
 * If spinning a web with 1cm-diameter silk, it would be possible to catch a plane
   * If that same web were made of steel, the plane would crash and break into pieces
   * If that same web were made of rubber, the plane would break through
 * Did an experiment comparing spider silk to carbon fibre and polyester
   * Spider silk was able to handle more weight than both of them
   * Carbon fibre broke fairly quickly
   * Polyester stretched too much and broke

#### Spiber
 * Company set up by former institute members
 * Taking spider genes and putting them into bacteria
 * Creating clothes like the Moon Parker
 * Can be made into sheets, gels, and other non-thread things

#### Silk diversity
 * Spiders make a whole lot of different spider silks
 * All silk genes are monophylogenetic (from the same original gene)
 * With enough data about the genetics and properties, can work out how amino acid changes affect the properties
 * Will sequence 1,000 spiders (for funding purposes)
   * Has already done a lot of those [? over 900]
 * Spider genomes are quite long
 * Don't really know what components are in the genes
   * One gene has periodic polyalanines
   * Can only find 10 spider silk genes in GenBank

#### MinION categorisation of genes
 * Can't do PCR because of repeats
 * Next time, got a better yield
 * Did whole-genome sequencing at 2-3X coverage, got N50 of about 10kb
 * The challenge is to find entire components of spider silk
 * Protein fractionation yielded 3 bands that were very specific to drag-line silk
   * Did gland-specific transcriptome
   * Looked at top 50 most expressed genes
   * Novel genes were found that corresponded to the gland in the spider
   * But first, they needed to clone the genes
 * Tried cloning, sorted out and cloned two genes
 * The other two genes were actually different components of the same gene
   * sequenced 2.4kb
   * use MiNION to finish it
   * no conserved N-terminal sequence

#### Questions
 * Only saw repeat elements within spider silk genes

### Zoe
 * ONT can probably fit another 200 seats in the venue for next year

### Gordon Sanghera
 * Get back to your labs and get innovating
 