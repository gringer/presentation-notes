# London Calling 2017

Presentation notes on London Calling, written by David Eccles.

## Day 1 (May the Fourth)

### Clive Brown

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

