# London Calling 2017

Presentation notes on London Calling, written by David Eccles.

## Day 1 (May the Fourth)

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
