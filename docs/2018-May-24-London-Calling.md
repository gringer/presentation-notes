---
title: "London Calling 2018"
author: "David Eccles"
date: "24 Mai 2018"
output: html_document
---

# Gordon Sanghera - Opening

## Intro music - Arctic Monkeys

* A band that was around when most ONT staff were alive
* In 2005, they went straight in at number 1
* No sales, no marketing, used myspace to allow people to download one sing
* It was a bunch of kids
* Since then, there's been no need to pander to the large organisations

## Sequencing landscape

* So many things have been proposed for nanopore sequencing
* The oil industry has problems with microbes
* The shipping industry has problems with ballast tanks

## Statistics

* The conference has 600 people - 500 customers, and 100 Nanopore people (with blue lanyards)
* Goal of ONT: Allowing anyone to sequence anything anywhere
* There are 7,000 MinIONs; 140 GridIONs; 40 beta PromethIONs; all done with community-based campaigns

## What it all means

* We are at the cusp of the fourth industrial revolution
* We are seeing things that are in sci-fi films
* Uber's actual goal: delivering anything to anyone anywhere
* We are bringing testing closer to the customers
* People can use Air B&B instead of hotels
* With nanopore, we are enabling the Internet of Living things
* There are 12500 sequencing centres in the world
* When people are provided access to real-time tools, we open up new opportunities
* Genoscope has 85 coral species
* General theme: More people, more diverse applications

## Service Provision

* KeyGene is the first authorised PromethION service provider
    * Providing service to the lettuce industry

## The Dunbar Number - 150

* About the number that were in the first nanopore conference
* Need to work out how to help people
* Ninja programming schedule
    * Repeating some breakout sessions
    * A workshop to improve the digital community (Andy Davies)
    * 300 people have downloaded the software App
    * Interact button allows people to ask questions during plenary sessions

# Angela Brooks

See the post-plenary questions [here](https://vimeo.com/271707634).


* Every cell has the same genome, but different cell types have different functions
* The transcriptome is what distinguishes cells

## Polyadenylated RNAs

* Have non-coding as well as protein-coding
* Can be edited or modified; over 100 types of modifications exist
* Limitations of short-read sequencing
    * Fragmentation 
    * Conversion into cDNA
    * doing PCR (even a problem with long-read cDNA)

## Nanopore Sequencing

* Sequencing is 3´ to 5´ (not typical)
* RNA consortium was formed to look at human cell lines
* 6 universities sequencing GM12878
* The same cell culture was sent to five institutes, a separate culture was done by Birmingham
* Can go to github to see the data
* 13 million native RNA reads, 24 million cDNA reads

## Observations

* Native RNA was longer than cDNA
* Error rates about the same
* Good correlation in gene expression levels
* Also good correlation with Illumina
* Birmingham clustered separately when using PCA
* Same sample clustered well together

## Read fragmentation

* A lot of reads that seemed to be fragmented
* MTCO1
* Read length doesn't drop over time (so there's no fragmentation happening within the flow cell)
* 45% of the reads were full length
* 20% were partial due to artefacts (e.g. basecaller truncating the read)
* 35% other partial reads, maybe due to sample prep, or degredation of RNA

## Full-length assembly

* Using orthogonal information to distingush full-length transcripts
* e.g. ChipSeq - looking for the promoter region. If not correlated, then it's probably not full-length
* Using short-read support for read correction
* Can look at full length and compare to annotation
* Can pick up novel transcripts
* Largest high-confidence transcript: 10313 nucleotides with 48 exons

## How many sequenced reads are needed?

* At about 5M reads, the number of transcripts *start* to plateau
* Transcripts keep getting detected at high coverage (more than 75k transcripts)

## Challenges

* Allele bias
* Also looking at polyA tail lengths [see [polya_estimator](https://github.com/jts/nanopolish/tree/polya_estimator)]
* Generally 30-150 nucleotides
* Detecting m6A, found that it was kmer-dependent
    * More differences for some, but not others
* Remaining challenge: hard to distingush full from partial RNA

## In-depth analysis of 100 reads

* Done manually by Mark Akeson

## Questions

* Looked at squiggle for capturing the 5´ cap (methods in progress)
* Using minimap
* Longest read from titin (aiming for 100 kb)

# Clive Brown

See the video [here](https://vimeo.com/272526835).

## Novel statements selected by David Eccles

* Live sample prep, sequencing, and WIMP analysis of Clive Brown's DNA by Ruth Moysey
* Voucher for Series D ASIC; longer run time, potentially 30 Gb from a single MinION
* ONT has a roadmap for moving to 500 Gb from a single PromethION flow cell (NovaSeq-busting prices)
* [Read-until is coming back [in anger]
* MinIT is orderable in the store
* Mk1C sequencer (MinION combined with MinIT) should be available December
* Epi2me will be embedded in MinIT, GridION, PromethION (local analysis workflows)
* Epi2me will be commercialised via MetriCoin (workflow currency, included with flow cell / kit purchases)
* New 1D² kit coming that uses UMIs in adaptors, increasing accuracy to Q20 and allowing amplicon sequencing
* Miyagi tool for combining reads from different pores for increased consensus accuracy
* Slightly mutated forms of R9.4 have been tested; could release a variant-pore flow cell in a few weeks if there is interest
* Flongle early-access begins now, released commercially in Q3
* Zumbador's official name is Ubiquibopsy (or Ubik tube)
* V2 VolTRAX (heat, PCR, 10 samples) is available for ordering in the store
* New SkunkWorx technology: a combined MinION + VolTRAX, dynamically embeds pores between droplets
    * *Too much novel stuff to summarise, see [here](#skunkworx)*

## Introduction

* Next year O2 arena -- looks like a nanopore, fits 20,000 people
* Every year, I have been told that I need to do this: promised investors I would do a live demo.
* Have been spitting in tubes, but soomeone else will do the prep.
* Ruth Moysey takes a tubefull of spit from Clive.

## Recap - get into rhythm

* Aim: Anybody to sequence anything anywhare
* Trying to make runnable outside labs
* real-time full-length reads
* ultra-low cost.
* In the past day, a few people have been demonstrating all features.
* This was a dream a few years ago.

## Olbigatory nanopore slide

* An array of membranes on a chip that we designed
* catch DNA from solution
* stream through the pore
* generate tiny signals (a lot of work decoding) All asynchronous
* get a full-lenth read in a few seconds
* Electronics can be made small, cheap
* Design breaks the traditional mould - Would be stupid to make an electronic device with fluidics
* Also key for ONT was designing array in the factory

## Other talks

* There have been a number of previous talks [by Clive]
* recently spoke about sub-1000 sequencing run; mostly on PromethION ($600)
* GridION conceived Feb last year, has been relatively successful

## Platform

* Product line as it stands, all in-field
* MinION is the most established
* Out there GridION is doing well; easy to own, people using it as service
* PromethION - a beast of a machine, now out, runnable, generating pretty high yields
* Over 1000 Customers for GridION; We think we can ship within a week of an order.
* Certification program, growing quite rapidly

## Grab bag

* In your bags is a token that gets you access to a slightly modified version of the MinION flow cell: a series D ASIC
* It's just better
* First design had a few faults, including current cross-talk; all things ate into yield
* This is a fixed-up version of the ASIC
* Can now enable very-long run times with sustainable yield of up to 100 hours
* **Enables 30Gb on a MinION**

## PromethION

* 48 individually-controllable flow cells
* 144,000 concurrent independent nanopore channels
* Can hot-swap
* Designed for quite lumpy workflows
* Can be run as a high-throughput sequencer, just like any other.

* Now dependent on Ruth on the Maracas
* Now dependent on You lot for reporting on what's happening on PromethION
* Now out of the Early access phase; $160,000 starter pack
* Can take box back
* When you buy PromethION can have access to upgrades
* Next version will run 48 flow cells

* Have shipped 40 PromethION by this conference
* should get to 60 by end of June.

## PromethION Yields

* What do new customer yields look like?
* Most getting over 50 Gb (this was the target)
* Some getting over 60
* ONT is getting internally over 170 Gb
* **A roadmap to move to 500 Gb per flow cell**
* These are NovaSeq-busting prices, provided you get the yields.
* New flow cell: single channel. Also a redesign of the multi-channel flow cell.
* Will make sure that all of MinION kits will work on PromethION (RNA coming in June)

## MinKNOW

* MinKNOW upgraded
* Very nice UI, innards of the GUI have been completely refactored.
* Thinking about things like read-until
* Including progressive unblock & dynamic voltage control, should increase data quality.

## Progressive unblock

* Blockages when you shove DNA thought a hole. Single strand forms structures on the other side of the pore.
* Can unblock by inverting potential.
* The old software was the simplest thing that worked
* Unblocking was quite violent, would remove channels
* The new version doesn't destroy the channel; a more subtle, sophisticated version of unblocking the pore
* Probably a larger uplift in difficult samples.
* Have generally improved kit quality

## Software

* 3-4 years ago pulled in software team to talk about Read Until
* As DNA is going through the pore, can basecall and do something with it before it's gone through the pore
* An in-silico selection
* We wrote an API.

* **Entire innards of MinKNOW have been rejigged, read-until is coming back**

* balancing amplicons
* Sequencing a certain region of human

* Coming back in second-half of year, coming back in anger
* Will be able to dynamically select molecules on the fly

## MinIT

* For MinION: Common complaint is the computer; that has caused a lot of trouble
* Making a device called MinIT
* It should be almost zero configuration.

* Plug it in, connect it, pair your iPhone display, ready to sequence.

* Can run off batteries. Can run off 12V supply.

* Will put Guppy in there, will keep up with MinION basecalling, critical for ReadUntil
* **Also embedding Epi2Me.**

* Pretty confident that a large number of people will want a hand with analysis
* **MinIT Should be orderable today.**

* Have gone for GPUs in MinIT; going for neural-network based AI
* A bunch of sequential matrix computations
* Quite a large number of bioinformatics things can be optimised on the same hardware with the same performance.

* **MinION Mk1C - MinIT with the aility to load a flow cell, or flongle**
* Target December
* Should be able to run a single flow cell without any external needs

* It's the kind of thing a dentist can run
* It also looks really cool

## Epi2Me

* A bioinformatics platform
* Embedded workflows doing the kind of analyses that people want to run
* Can be run in the cloud, or workflows can come to the computer: GridION, PromethION, MinIT. 
* Lots of reasons, 1) a lot of computing in the boxes.

* Expertise in optimising on GPUs
* Sometimes people don't want to pipe data over to the over side of the world

* We think it's more usable now, can upload custom reference, will provide data storage

* We will release Epi2Me on MinIT in Q3 - a MinIT with MinION will do this locally in Q3

## Epi2Me Commercialisation

* Will be commercialised
* When you buy a flow cell; have invented something called MetriCoin
* **When you buy flow cells or reagents, will get MetriCoin, can use to run workflows**
* People who don't have bioinformatics support will have access to bioinformatics services

## Chemistry improvements

* Platform performance is now much closer to what Clive tweets
* Customer runs by kits is converging, variance is decreasing
* Largely due to kit simplification
* Early kits had a cholesterol tether; it sticks to everything that is hydrophobic
* We have been removing that from all of our kits.
* Generally customer performance has started to converge with nanopore.

## Read Length

* Fragment length is read length; largely in customer hands
* Most platforms, the optics / chemistry conks out
* If you can present with long reads, it will sequence it

* Some of thought-leading developers have tried to present pore with enormous, intact lengths of DNA
* The developers found a bug in the software, ONT software was chopping up reads
* In principle, if you can do 2 Megabases, can do 20 Megabases
* Challenge is whole-chromosomal sequencing

## Yield Drop-off

* Initial software that classified data was the simplest that worked
* Software misclassified reads, which would degrade the data
* Low-complexity regions, rectified in next software release in June

* Need to Scale data, scaling can be biased, to be fixed (fix went out 2 weeks ago)

## Unblocking

* Extracting from chitinous insect won't be the same as a drop of blood
* Not the whole story, can get DNA out
* There have been issues with things sticking to tubes

* If initial yield was high, would drop off suddenly
* Chickens do this

* Software that you need to kick out DNA is different for different samples

* Some kinds of DNA form secondary structure as they get to the other side of the pore, creating a block that kills the pore.

* Another upgrade coming to change the unblock logic that should level out yield differences over time.

## Kits

* Recently settled lawsuit about hairpin

* Came up with a system to do 1D²
* Version 1 went out a few months ago
* It is now due for a revamp
* Adapters will be improved to imporoved the performance of the system
* Looking for 60% reads 1D², should get to Q20
* Software is antediluvian, 4 years old

* A lot of people have complained that they can't do amplicons
* **New kit optimised for PCR uses a special set of barcodes that will enable barcodes to be paired up (UMI).**
* Will go back again, revamp it, and make a performant version.

## Targeted sequencing

* Technology was to take a deactivated Cas9
* Guide RNA, hybridised to sample, subset of reads is pulled down to pore
* Working quite nicely
* Will be out as a kit later in the year.

## Direct RNA sequencing

* Can put RNA through the pore just like DNA
* Proven very popular, there's lots of stuff in RNA
* Not as performant as DNA product
* Get full-length RNA molecules, can see all the modifications
* Can really get to the full-length biology.

* Nanopore is quantitative, see all the splice formas.

* Now focusing on making RNA as performant as DNA
* Want to increase speed RNA goes through the pore
* Will move to 110 bases per second
* Looking at improved adapters, simpler, fast library prep, incremental advances in basecalling

## Field sequencing

* Despair when looking at what people take to the field - polystyrene ice bucket kills me
* A lot of work has gone to ambient shipping
* Looking to post flow cells without cooling

* Can ship at ambient, most reagents

* Looking at storing ambient, a few kits left to lyophilise
* Especially an issue in places where don't have a lab

## Consensus Accuracy

* Looked at fixing this issue a few months ago
* The thing that most people hold up to nanopore

* Cornering the rat, and then stamping on it
* We're now tickling the rat

* We're not at the limit yet
* Worth talking to the team who are here
* There are some limitations in the current software

* Current training set, issues with scaling / chunking of data
* Still aren't learning all the context
* We still train on bacteria
* We don't learn in damage and modifications
* There are some software limitations, and other issues.

* People assemble and polish, not fully-utilising all the signal
* People don't exploit alll the information in the signal
* Quite a lot of work to do.

* Bases are not modelled, similar current for different sequences.

* Progress on homopolymers, over past few months.

* Nanopolish is still the gold standard for treating these data, but medaka can do well in some contexts.

## Nanopore solutions

* Have medaka, only works in base-space
* Comparable to nanopolish, but much faster

* Have been working on a new tool, miyagi, for correcting homopolymers
* HMM based, that's the way to do it
* comparable or better to nanopolish in some circumstances

## Fixing the problem

* One way: improve the chemistry.

* People are alreads combining data with another certain company
* Has been long on our agenda to do the same thing on one platform
* Would then not need the other company

* If you could combine multiple pores, would get flattening out of errors

* R9.4 pore signal comes mostly from 3-4 bases
* A run of Ts bigger than 3-4 gives flat signal
* Can estimate bases using time domain
* Would be better if we could de-flat the sections of data

* Using read-ahead to look at more bases, rather than less
* Will always be averaging over more bases

* Deal with more bases using machine learning

## Pore changes

* Use Pore R8 - Lysenin based
* R10 has two points about 9 bases apart

* A particularly pathocogical error is a round of 5 Ts followed by two Gs
* R10 spans the homopolymer giving an uppy-downy signal that the software can decode

* Equally, number of percentage correct homopolymers with R10 is better
* Think that green accuracy line will shift up.

* Can generate orthogonal errors that can shift consensus
* These are now under very active development as potential products

* What about combining together?
* 50-fold R9 with 50-fold R10
* can easily exceed Q40 in consensus, proof of concept
* **These methods are being implemented in miyagi tool, can use yourself (if you had R10 data).**

* Still not using dwell in these data
* Using time domain, can boost these further.

* The principle is shown.

* Why not 5 pores?
* Why not 500, each with completely different error modes?

* We're going to crack this this year, and get it out to you as soon as you can.

* Doing very well on variant calling, specifically on SNVs.

* Have made at least one mutant of R9.4; R9.6. 9.4 gets one homopolymer wrong, 9.6 doesn't.
* **Can make even variants of 9.4 that have significantly uncorrelated signal. Could release this in 2-3 weeks.**

## Template changes

* Could mess with the complement of the sequence
* About 20 minutes, a pot of nucleotides in the kits, swap T for U and train basecaller
* A/C/G/U version has different errors from A/C/G/T version. More complicated.

* My preference is to put multiple pores in the chip.
* Can provide these tools to allow people to mess with the pores.

* Combining all three: two pores plus complement
* Combining data that isn't correlated, as long as you pick the right data.

* Will keep 9.4, but could make 9.6, could make R10

* Question: is this useful? is that of interest? When would you like it? [let ONT staff know]

## Flongle

* It's coming, really soon

* MiNION + 1-off adapter, that's the flongle
* Has most of the electronics that's in the MinION
* An array of copper electrodes
* Can then make a very cheap crappy plastic flow cell with magical chemistry
* Separates the cheap bits from the expensive bits

* 128 channels, limited by the forces that are needed to make connections

* The data is the same, can flongleise a MinION
* Can flongleise a GridION
* Projecting that v1 up to a Gb from one flow cell, should get 3Gb from a flongle.

* People don't want lots of data, problem is about how quickly enough data can be obtained. 
* Also good for bacteria and virused
* People should buy more if it's cheaper

* Flongle works, just like MinION

* Squiggles are squiggles, they are the same

* Invites for early adopers have going out

* Looking at $90-$100 per flow cells, about 5-10% of the total treatment cost for dentist

* **Early access begins now, will release commercially in Q3**

## Where to go

* Drive is to get sequencing out of the lab
* Can survey what's going on in a river
* Cheaper, easier, package it up, remove any extraneous equipment.

## Zumbador

* Clive had the largest office, but had to rename Zumbador.

* Idea is that you can take something very cheap, a piece of plastic, introduce a liquid because they're easy
* After some reasonable time, like 10 minutes, can just sequence what's in there.

## **New name: Ubikwibopsy (Ubik tube)**

* Ubiquitious
* Kwick
* Liquid
* Biopsy

* Turns out that DNA is really informative
* Don't want to ship samples off to california
* Want anyone to be able to do this themselves, and have complete control over their own data.

* Video: can put spit in a tube, a bunch of stuff happens in the tube, can bind DNA onto solid phase support, then separate. It drops onto the flow cell.

* Have embedded the library prep onto the flow cell, comes ready to run.

* DNA in, sample prep appears early in the pore

* Can get meaningful data really quickly
* Yields aren't massive, but we've got it
* 10 minutes from spit prep to WIMP

* Had bacterial infection, could fix it, see a drop in the bacteria.

* Saliva, lysis 10 minutes on Ubik tube.

* Dentist offered to buy one.

* If you encapsulated enrichment, could use read-until to exclude human, or include human.

* We Might not be the right audience for that.

* Future versions like flongle and smidgION will move towards anybody being able to touch a sample to a flow cell and know what's in.

* Metrichor will make quantitative analysis of the self available direct ot the consumers.

## VolTRAX

* Version 1 a while back.
* Main use is the proper version, version 2 ready to go out a bit later this year.
* Supports all kinds of complex lab workflows.
* 15 inlets. 
* Can do heat, PCR, fluorescence detection. It is a lab on a chip.

* Starter pack for V2 $8,000

* **As I speak, the shop is open for orders, can buy a VolTRAX v2.**
* Will prioritise people who got a V1.

* Can do up to 10 samples, 2xGridION.
* Pricing starts to get quite attractive for multiple samples.

## SkunkWorx

* A few years ago, pulled people into my office, asked them to do a thing.

* Amazingly, people went off and did it.

* **A VolTRAX - MinION hybrid, amalgamating into a single device.**
* Now have another DNA sequencer that can be made.

* Completely automated, very complicated droplet-based workflows can be built in.
* No physical handling, can work directly from cells.

* Form dynamic membranes between droplets on the VolTRAX.
* Can insert a pore, and have a sequencer.
* Move the droplet to a certain part of the array and droplets look like a MinION channels.

* Squiggles are the squggles; they are the same.

* Droplets can be quite small, or quite big.

* Can swap the droplet.

* Can access the trans side.
* Can take the things you sequenced, and PCR them, or sequence again.

* Target is to get to 128 channels.
* More likely to be less than that.
* Currently 8-channel breadboard.

* Extraction zone, Library zone, sequencing zone.

* Henrietta Lacks cells being aligned and lysed.
* No shearing; what if you could just get whole chromosomes and put it between two droplets.

* Lots of things you can do.
* We tend to stick DNA to the membrane.
* Can coat up the droplet with DNA, DNA whizzes around and will find pore within seconds.
* If you have a tiny amount of material that you want to mine digitally, can mine out that cell.

* With read-until, can eject high-abundant stuff.

* Schemes where you can re-pair sequenced DNA and put it through again.

* Can also just hybridise things to DNA.
* Some Cas9 are SNP sensitive, can count thousands of presence - absense.
* Spit blood in, all in one, very flexible measuring device.

* We have the proof of concept, all now about making the box.
* Will be coming your way; not talking years.

* The mind boggles of what you can do.
* A small platform at relatively low plex. Our next likely major product launch.

## Timeline

* Revision D ASIC, can get now. Probably broadly by middle of Q3. Should see 20-30 Gb.
* Kit9 much improved ligation kit
* PromethION went on commerical release today
* PromethION flow cells orderable
* Epi2Me commericalisation
* Software umblocking fixes
* MinIT shipping in July
* Ambient shipping in July
* First flongle shipments in July
* Voltrax V2 in August
* Much more performant 1D² in August
* RNA upgrade in terms of yield / quality in September
* In December fully-performant PromethION (48 flow cells) 
    * ONT has just got 3Tb internally
    * target is 12 Tb per run, equivalent to 3-4 NovaSeqs
* December Mk1C MinION

## Questions

* Flongle flow cells should be able to be chuckable; throwing away electronics is difficult.

* Multiple pores - Coverage will be reduced because errors aren't correlated. As long as you can pick the right one, which is the high and low quality base.

* Trying to get the same kits and settings on all devices.

* SmidgION - We can make it, that's not a problem. ASIC is reallyy cheap. Flongle comes first.

* R10 pore - frequency of homopolymers. Current software can call homopolymers as -1, some bias in software that is consistently doing it wrong. Will get a lot further with just incremental improvements.

# Lightning Talks / Day 2 (Thomas Bray)

## Franz Josef Müller

* Nanopore sequencing of short repetitive DNA
* A number of short repeat disorders (e.g. fragile X: GGC repeat, usually 30-50, but can expand up to 200 repeats)
* Why nanopore sequencing? Looking at kilobase stretches of 100% GC sequence, southern blot remains a diagnostic tool
* Good news: raw signal allows tracing / counting cases
* Regardless of the system, no real ground truth of the repeat number (in the normal case)
* Used nanopore-simulation (crohrandt)
* Pulls data, generates raw signal
* Entered defined repeat expansions based on the ground truth
* Made another tool: nanostrike
* Uses a signal model to identify repeat boundaries, quite good agreement with manual counts
* Cpf1 enrichment
* Poster actually describes a different tool

## Natacha Couto

* University of gronigen
* Looking at vancomycin-resistant enterococci
* Intrinsic resistance to several microbial classes
* VRE dissemination can exchange mobile genetic elements
* Colleagues studying 36 isolates
* Did Illumina sequencing, found 7 clusters
* Some strains were clustered differently, but isolated from the same patient, or the same ward
* Wanted to look at transposons
* [Showed photo of PI - John, because he kept showing photos of her] -- she did the sequencing herself, it wasn't John's work
* No shearing, assemblies using Unicycler
* Could see transposons, look for differences, two on the chromosome, other two in a plasmid
* Looking back at the tree, found that core genes could be linked by common transposons
* Important to study structures, combine short-read sequencing with long-read sequencing

## Stefanos Siozios
* Works with microbes and arthropods
* Microbes that pass from mother to offspring
* Image of maternal transmission to oocytes, paternal transmission as well (but rare)
* Biologically important, can alter vector competence
* Can, for example, kill of male offspring
* Has been hard to complete genomes
* Only a minority of microbes can be cultured outside the host
* Microbes have highly repetitive genomes
* Repetitive content is difficult to resolve
* Trying to make an improved reference genome (estimated size of about 3.5 Mb)
* Large amount of extra-chromosomal elements; PacBio also failed
* Two different library protocols. Very long reads provided the ability to assemble the main chromosome into a single circular contig - got extra-chromosomal elements as well

## Rainer Waldmann

* Likes idea of VolTRAX-based single-cell sequencer
* Doing Illumina sequencing, need to fragment DNA, end up with only 3´ sequences
* Problem with amplification, need to correctly identify UMIs and cell barcodes
* Clustering gets easier if you know the barcode + UMI sequences
* Did 1 nanopore run with 190 cells, 30M reads needed for 5X UMI
* Did 951 cells using targeted nanopore sequencing
* With one cell: reads with the same UMI should be the same molecule; some outliers
* Nanopore data can be linked to Illumina
* Good idea to use Illumina data with single-cell data

## Yutaka Suzuki

* Sequencing core laboratory
* Started analysis with cancer cells
* 9 patients, some initial success for cancer results
* Used the same process to genotype malaria patients
* Making a geographic distribution of modifications
* Moving to Papua, needed to modify protocols
* Replaced PCR with isothermal amplification
* Expanded to global G-RAID meeting
* BBC (UK) found out about this
* Wanted to do the first human cancer genome
* With the field kit, first do Malaria in Indonesia

## Markus Haak

* In spare time, likes to detect unnatural bases (e.g. isoG, isoC)
* Detection method should be PCR-free and polymerase-independent
* MAX: looking at different restriction enzymes, method applicable for certain sequencing contexts
* Developed iCG ased on sequencing reference DNA samples
* Unnatural bases have substantial influence
* Automated model, does event correction
* During event correction, bad events are redistributed
* Data points are based on Dynamic Time Warping, shift to correct misalignment due to unnatural base calling
* Quite potentially adoptible to other bases or base calling
* Haven't tested against existing modified natural bases

# Liana Kafetzopoulou

## Intro

* ONT managed to fit her name on a MinION two years ago
* Want to be able to sequence all RNA viruses with a single protocol
* Charles Chiu published a protocol: reverse transcription using a random nonamer [9-mer]
    * creates a cDNA library

## Samples for testing

* RIPL
* Samples that were the most prevalent: chikungunya & Dengue
* Had to test sensitivity as well
    * Even at higher CTs, can get the whole genome with the random nonamer protocol
    * Percentage of reads (coverage) on MinION match Illumina and MinION
* What about when you don't know what is there?
    * When you can assemble 80% of the genome, it's probably there
    * Three different kits, consistent results

## Taking it into the field

* Testing on Lassa virus, a very divergent RNA virus
* Lassa is endemic in Nigeria, outbreaks twice a year
* Take positive samples for sequencing
* Working great until Nigeria hit more cases than were ever before seen
* Got data out as soon as it was generated

## Processing

* Only doing DNAse treatment
* PoreChop
* Using Canu to assemble, then BLAST to find the closest reference
* Used De-novo approach to feed mapping

## Diagnostics

* Existing in-country diagnosis uses two RTPCRs
* Looked at the phylogeny; MinION assemblies were all spread around, all independent spillovers
* MinION is definitely accurate enough to tell if there's human to human transmission
* There were two samples that looked marvelously identical
    * Looked at patient forms, found out that they were from the same patient, taken 6 hours apart, one SNP difference
* NCDC and WHO had a great need to know what was happening; the country as well...
* Country took the time and attention to listen

## Challenges

* MinION overheated in the first run
* Time scale changed massively, changed from pilot run to something else

## Outcome

* Were able to make 35 lassa virus sequences in a month