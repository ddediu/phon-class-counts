# Features (and feature counts) from PHOIBLE and Ruhlen's databases

**Dan Dediu** ([Dan.Dediu@mpi.nl](mailto:Dan.Dediu@mpi.nl)) and **Scott Moisik** ([Scott.Moisik@mpi.nl](mailto:Scott.Moisik@mpi.nl))<a name="origin1"></a><sup>[1](#footnote1)</sup>

Max Planck Institute for Psycholinguistics, Nijmegen, The Netherlands

October 2015, version 1.0


## Introduction

This document describes the input data, the processing and the output files associated with defining classes of segments on two databases uses two feature systems.
Please note that these are released in the hope that they will help the community but with the understanding that this is *work in progress* and there are bound to be errors and some aspects are known to be incomplete at this time (e.g., the encoding of click accompaniments).
Nevertheless we will strive to extend this work and fix the errors and we will release new versions accordingly.
The data and code are available on [GitHub](https://github.com/ddediu/phon-class-counts) ([https://github.com/ddediu/phon-class-counts](https://github.com/ddediu/phon-class-counts)).

## The databases

PHOIBLE [http://phoible.org/](http://phoible.org/) (Moran & McCloy, 2014) is a vast database that contains (in the 2014 edition used here) 2155 phonological inventories for 1672 distinct languages (some languages have more than one description available) covering 2160 segment types, as well as a proposed description of its segments in terms of "+", "-", "0" and "" (absent) values on 37 features; we will denote in the following both the database and the feature system as *Phoible* (or simply *P*), disambiguating where necessary.
The files `./input/phoible-phonemes.tsv` and `./input/phoible-segments-features.tsv` (TAB-separated, no quotes) contain the segment inventories and feature system respectively in the original format.

Recently, Creanza *et al.* (2015) have published as Supplementary Materials Online (Datasets [S1](http://www.pnas.org/content/suppl/2015/01/15/1424033112.DCSupplemental/pnas.1424033112.sd01.txt) and [S2](http://www.pnas.org/content/suppl/2015/01/15/1424033112.DCSupplemental/pnas.1424033112.sd02.txt)) a database collected and curated by Merritt Ruhlen containing the presence/absence of 728 phonemes (after some pre-processing such as removing symbols that seem to stand for more abstract categories, such as "c" and "v" and their variants or "vowelharmony", there are 644 potential phonemes) in 2082 languages; we will denote this database as *Ruhlen* (or *R*).
The files `./input/pnas.1424033112.sd01.txt` and `./input/pnas.1424033112.sd02.txt` (plain text) contain the inventories and segments respectively in the original format explained in the files themselves.


## The Fonetikode feature system

Scott Moisik constructed a feature system of a more phonetic nature inspired from the International Phonetic Alphabet ([IPA](https://www.internationalphoneticassociation.org/content/ipa-chart)) containing 13 features with each with its own values; we will denote this system as *Fonetikode* (or *F*).
These features (**bold**) and their possible values (*italic*) are:

* **GC** (general class): *c* (consonant), *v* (vowel), *ss* (suprasegmental/tone);
* **VV** (vowel vertical or tongue height): *c* (close), *nc* (near close), *cm* (close mid), *m* (mid), *om* (open mid), *no* (near open), *o* (open);
* **VH** (vowel horizontal or tongue anteriority): *f* (front), *nf* (near front), *c* (central), *nb* (near back), *b* (back);
* **VM** (vowel modifiers): *none*, *n* (nasal), *r* (round), *nr* (nasal & round), *ur* (-round to +round), *ru* (+round to -roun), *un* (-nasal to +nasal), *nu* (+nasal to -nasal), *nur* (nasalized u), *nru* (nasalized r);
* **CP** (consonantal place of articulation): *b*(bilabial), *bld*(bilabio-labiodental), *ba* (bilabio-alveolar), *bpa* (bilabio-postalveolar), *ld* (labiodental), *lv* (labiovelar), *lu* (labiouvular), *ll* (linguolabial), *i* (interdental), *d* (dental), *a* (alveolar), *pa* (postalveolar), *r* (retroflex), *dv* (dentivelar), *av* (alveolovelar), *ap* (alveolopalatal), *p* (palatal), *pav* (postalveolar-velar), *v* (velar), *u* (uvular), *ph* (pharyngeal), *e* (epiglottal), *g* (glottal);
* **CM** (consonantal manner of articulation): *s* (stop), *f* (fricative), *af* (affricate), *n* (nasal), *a* (approximant), *t* (tap/flap), *tr* (trill), *clk* (click);
* **CS** (consonantal sequencer): *s* (simplex), *c* (complex), *prn* (pre- nasalized), *pon*(post-nasalized), *prs*(pre-stopped), *pos*(post-stopped), *prg*(pre-glottalized), *pog*(post-glottalized), *pra*(pre-aspirated), *poa* (post-aspirated), *prag*(pre-aspirated & glotatlized), *poag*(post-aspirated & glottalized);
* **Phon** (phonation): *vl* (voiceless), *vd* (voiced), *pvd* (pre-voiced voiceless), *b* (breathy voiced), *c* (creaky);
* **Init** (initiation): *p* (pulmonic egressive), *gi* (glottal ingressive [implosive]), *ge* (glottal egressive), *vi* (velaric ingressive);
* **Pri** (primary articulation diacritics): *none* (no primary articulation diacritics), *ret* (retracted), *adv* (advanced), *mc* (mid-centralized), *lwd* (lowered), *rzd* (raised), *ap* (apical ), *lam* (laminal), *dvb* (double vertical bar below), *dhb* (double horizontal bar below), *ola* (open left angle below), *d* (dental), *c* (centralized);
* **Sec** (secondary articulation diacritics): *none* (no secondary articulation diacritics), *w* (labialized), *j* (palatalized), *v* (velarized), *ph* (pharyngealized), *jw* (palatalized labialized), *jv* (palatalized velarized), *wv* (labialized velarized), *wph* (labialized pharyngealized), *l* (lateral or lateral release), *r* (rhoticized/rhotic release), *wr* (labialized with rhotic release), *jr* (palatalized with rhotic release), *lv* (lateral and velarized), *lj* (lat- eral and palatalized), *lw*(lateral and labialized), *lph*(lateral and pharyngealized), *glt* (glottalized [vowels only]), *nas* (nasalized), *vs* (velar stop [clicks only]), *vf* (velar frication [clicks only]), *va* (velar affrication [clicks only]), *us* (uvular stop [clicks only]), *uf* (uvular frication [clicks only]), *ua* (uvular affrication [clicks only]);
* **Pros** (prosodic properties): *none* (no prosodic properties), *syl* (syllabic), *nsyl* (non-syllabic), *brev* (brief/breve), *long* (long/geminate), *ds* (downstep);
* **Tone** (tone markers): Chao digits (1-5).

The files `./input/phoible_Features_Fonetikode.csv` and `./input/Ruhlen_Features_Fonetikode.csv` (TAB-separated, no quotes) contain the feature system as applied to the *Phoible* and *Ruhlen* segments, respectively.


## Matching the languages and Universally Unique Language Identifiers

Here we use a procedure described elsewhere (Dediu, *forthcoming*) for matching the most used language identifiers: ISO 639-3 standard three-letter codes, the WALS three-letter codes, the AUTOTYP numeric codes, and the Glottolog alpha-numeric codes.
These result in combined codes, denoted here as **Universally Unique Language IDentifiers** (UULID), of the form **[i-I][w-W][a-A][g-G]** where "I", "W", "A" and "G" stand for the ISO 639-3, WALS, AUTOTYP and Glottolog codes of the language, respectively, where any (or all) of the codes may be missing or have more than one value (separated by "-").
These UULID codes make it easy to cross-reference across linguistic databases.
The file `./input/code_mappings_iso_wals_autotyp_glottolog.csv` (TAB-separated, no quotes) contains this mapping for more than 17,000 linguistic entities (many more than present in the *Phoible* and *Ruhlen* databases).


## Classes of segments

We then used the two features systems to define *classes* of segments and produce counts of such classes per inventory.
More precisely, we used both the *Phoible* and *Fonetikode* feature systems to classify the *Phoible* segments, but only the *Fonetikode* feature system to classify the *Ruhlen* segments (as the *Phoible* system does not cover some of the segments present there).
There are currently 174 such classes such as "segment", "mid vowel", "retroflex stop", "bilabial fricative" and "level tone"; the *Phoible* feature system cannot describe some of these classes (e.g., "level tone", "contour tone", "doubly articulated consonant").
For each inventory in the two databases, we categorized each segment in terms of these classes and produced *counts* (more details in the section below).


## Methods and outputs

We implemented the procedure as an [`R`](https://www.r-project.org/) (R Core Team, 2015) script available as `./code/Extract features.r`.
This script uses libraries `stringr` (Wickhamm, 2015), `dplyr` (Wickham & Francois, 2015), and `parallel` and `compiler` (part of standard `R`).
The script has **XXX** sections.

### Assembling the languages

The first step is to filter the 17,000+ entries in the `./input/code_mappings_iso_wals_autotyp_glottolog.csv` file, retaining only those with geographical information (for plotting and spatial statistics), with Glottolog and ISO 639-3 codes (for cross-referencing with both *Phoible* and *Ruheln* databases, among others); the resulting 7519 entries are saved into the `./output/languages-info.csv` (TAB-separated, no quotes) file.

### Assembling the segments

Then we assembled the sets of segments and their occurrence in each language for both *Phoible* and *Ruhlen*.

For *Phoible*, we considered only the inventories marked as `*Trump* == 1` (important where there are multiple inventories available for the same language) and for each such inventory (with a well-defined ISO 639-3 code), we extracted its segments.
These segments are collected in a `data.frame` (basically a data table with observations as rows and variables as columns) where each row represents one language, and the columns are the ISO 639-3, WALS, AUTOTYP and Glottolog codes, followed by the Ethnologue, WALS, AUTOTYP and Glottolog language names, the Latitude and Logitude, the UULID, and the list of all segments ascertained in the database (a total of 2011 segments such as \*R \*R̪ \*R̪̥ \*R̪̰ and so on), where each cell is 0 if the segments in *not* present in the language's inventory, 1 otherwise.
We saved this collection in the `./output/inventories-phoible.RData` (`R` data file, XZ-compressed).

For *Ruhlen* we produced a similar data table with the same format (saved as the XZ-compressed `R` Data `./output/inventories-rhulen.RData` file); processing *Ruhlen*'s database was complicated by the custom format used to encode the original data.

Finally, we built a list of the unique segments that appear in both databases, comprising 2438 unique entries.

### The feature systems

We imported the *Phoible*, *Fonetikode* for *Phoible*, and *Fonetikode* for *Ruhlen*<a name="origin2"></a><sup>[2](#footnote2)</sup> feature systems, defined in the files `./input/phoible-segments-features.tsv`, `./input/phoible_Features_Fonetikode.csv`, and `./input/Ruhlen_Features_Fonetikode.csv` respectively (each row represents one segment the columns the features, and the cells the actual values), and merged them, identifying duplicates or undefined segments, and retaining only the featural defintions for the segments actually present in the inventories.
In total, we have 2008 segments defined in the *Phoible* system, 2004 in the *Fonetikode* for *Phoible*, and 414 in the *Fonetikode* for *Ruhlen*.

### Defining classes of segments

We have implemented a very flexible and powerful system for specifying sets of features and values and combinations thereof.
The most fundamental operator is `.` which takes a set of segments and a description of feature values and returns the segments matching the feature values.
The `.` operator supports two ways of describing feature values: the system used by the *Phoible* features which uses a "+", "-" or "0" preceding the feature name, and the system used by the *Fonetikode* systems which use the feature names followed by ":" and the feature values separated by ",".
For example, the definition of a "segment" in the two systems is "0tone" (*Phoible*) and "GC:c,v" (*Fonetikode*), while a "vowel" is defined as ("+syll" & "-cons" & "+sonorant") and "GC:v", respectively.

Atomic calls to the `.` operator can be combined using boolean logic (and, or, not) but also with more advanced processing , resulting in a Turing-complete system.
Each class is thus encapsulated by a function with a pretty transparent definition, allowing the defined classes to be tweaked and new classes to be easily defined.

### Counting classes of segments

For each inventory in each of the two databases using the appropriate feature systems, the number of segments in each class is counted, resulting in three CSV (TAB-separated, no quotes) files `./output/counts-fonetikode.csv` (*Fonetikode* system on *Phoible* database), `./output/counts-moran.csv` (*Phoible* system on *Phoible* database) and `./output/counts-ruhlen.csv` (*Fonetikode* system on *Ruhlen* database) containing the languages as rows (identified by their UULID) and the classes as columns, each cell giving the count<a name="origin3"></a><sup>[3](#footnote3)</sup> of a class for an inventory.

We merged these counts in the CSV (TAB-separated, no quotes) file `./output/counts-merged.csv` where the class names have suffixes "_F" (for *Fonetikode* system on *Phoible* database), "_P" (for *Phoible* system on *Phoible* database), and "_R" (for *Fonetikode* system on *Ruhlen* database). 
Moreover, the CSV (TAB-separated, no quotes) file `./output/counts-merged-separate-codes.csv` also splits the UULIDs into its component codes (ISO 639-3, WALS, AUTOTYP and Glottolog) for easier processing and cross-database matching.

The process also outputs the details about the actual class membership for each class and inventory in the log files (CSV, TAB-separated, no quotes) `./output/log/phoible--fonetikode-features.csv`, `./output/log/phoible--moran-features.csv` and `./output/log/ruhlen--fonetikode-features.csv`.



## Summary of the input and output files

In summary, the `R` script `./code/Extract features.r` needs several input files and produces multiple output files, all described in the Table below:

| File                                         	| Location      	| Type   	| Format                        	| Comments                                                                                                                                                                                                      	|
|----------------------------------------------	|---------------	|--------	|-------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| code_mappings_iso_wals_autotyp_glottolog.csv 	| ./input       	| input  	| CSV, TAB-separated, no quotes 	| Contains the mappings between  the ISO 639-3, WALS, AUTOTYP and Glottolog codes, the language name as given by Ethnologue, WALS, AUTOTYP and Glottolog, the language's Latitude and Longitude, and its UULID. 	|
| phoible-segments-features.tsv                	| ./input       	| input  	| CSV, TAB-separated, no quotes 	| The Phoible database                                                                                                                                                                                          	|
| pnas.1424033112.sd01.txt                     	| ./input       	| input  	| TEXT custom format            	| The Ruhlen database (together with the next file)                                                                                                                                                             	|
| pnas.1424033112.sd02.txt                     	| ./input       	| input  	| TEXT custom format            	| The Ruhlen database (together with the previous file).                                                                                                                                                        	|
| phoible-segments-features.tsv                	| ./input       	| input  	| CSV, TAB-separated, no quotes 	| The Phoible feature system                                                                                                                                                                                    	|
| phoible_Features_Fonetikode.csv              	| ./input       	| input  	| CSV, TAB-separated, no quotes 	| The Fonetikode feature system for Phoible                                                                                                                                                                         	|
| Ruhlen_Features_Fonetikode.csv               	| ./input       	| input  	| CSV, TAB-separated, no quotes 	| The Fonetikode feature system for Ruhlen                                                                                                                                                                          	|
| languages-info.csv                           	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| Subset of code_mappings_iso_wals_autotyp_glottolog.csv relevant for the Phoible and Ruheln databases                                                                                                          	|
| inventories-phoible.RData                    	| ./output      	| output 	| XZ-compressed RData           	| Cached Phoible inventories                                                                                                                                                                                    	|
| inventories-rhulen.RData                     	| ./output      	| output 	| XZ-compressed RData           	| Cached Ruhlen inventories                                                                                                                                                                                     	|
| counts-fonetikode.csv                        	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| Category counts for the Phoible database using the Fonetikode feature system                                                                                                                                      	|
| counts-moran.csv                             	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| Category counts for the Phoible database using the Phoible feature system                                                                                                                                     	|
| counts-ruhlen.csv                            	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| Category counts for the Ruhlen database using the Fonetikode feature system                                                                                                                                       	|
| counts-merged.csv                            	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| The above three count files combined                                                                                                                                                                          	|
| counts-merged-separate-codes.csv             	| ./output      	| output 	| CSV, TAB-separated, no quotes 	| The above file with the UULID split into component codes                                                                                                                                                      	|
| phoible--fonetikode-features.csv             	| ./output/logs 	| output 	| CSV, TAB-separated, no quotes 	| Details over the actual segments in each class and inventory for Phoible using Fonetikode feature system                                                                                                        	|
| phoible--moran-features.csv                  	| ./output/logs 	| output 	| CSV, TAB-separated, no quotes 	| Details over the actual segments in each class and inventory for Phoible using the Phoible feature system                                                                                                     	|
| ruhlen--fonetikode-features.csv              | ./output/logs 	| output 	| CSV, TAB-separated, no quotes 	| Details over the actual segments in each class and inventory for Rhulen using the Fonetikode feature system                                                                                                       	|


## Licenses

The `R` script `./code/Extract features.r` is released under a [GPL version 3](http://www.gnu.org/licenses/gpl.html) ([http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)) license.

The input files that belong to us (`code_mappings_iso_wals_autotyp_glottolog.csv`, `phoible_Features_Fonetikode.csv` and `Ruhlen_Features_Fonetikode.csv`) are released under a [Creative Commons Attribution 4.0 International (CC BY 4.0)](http://creativecommons.org/licenses/by/4.0/), as are all output files.

The input files that do not belong to us are governed by their respective licenses: 
[Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)](http://creativecommons.org/licenses/by-sa/3.0/) for the Phoible data (`phoible-phonemes.tsv` and `phoible-segments-features.tsv`) and by the [PNAS terms](http://www.pnas.org/site/misc/terms.xhtml) for the Ruhlen database (`pnas.1424033112.sd01.txt` and `pnas.1424033112.sd02.txt`).



<a name="footnote1"><sup>1</sup></a> **Author contributions:** DD and SM desgined the research; SM defined the *Fonetikode* feature system and applied it to the *Phoible* and *Ruhlen* databases; SM defined the segment classes and their specification in both feature systems; DD wrote the `R` script and generated the UULIDs; DD and SM checked the results; DD wrote this report. [↩](#origin1)

<a name="footnote2"><sup>2</sup></a> We needed to specify two different *Fonetikode* feature systems, one for the *Phoible* and on for the *Ruheln* databases, because these two use different transcription conventions and it was not always trivial to determine the correspondence between them, or actual the meaning of several symbols in the *Ruhlen* database. [↩](#origin2)

<a name="footnote3"><sup>3</sup></a>: Please note that some of these "counts" are in fact ratios of counts (e.g., "ratio.voiced.voiceless.obstruents"). [↩](#origin3)


## Bibliography

Creanza, N., Ruhlen, M., Pemberton, T. J., Rosenberg, N. A., Feldman, M. W., & Ramachandran, S. (2015). A comparison of worldwide phonemic and genetic variation in human populations. *Proceedings of the National Academy of Sciences*, **112**(5):1265-1272. [doi:10.1073/pnas.1424033112](http://doi.org/10.1073/pnas.1424033112).

Dediu, D. (*forthcoming*), Language classifications as standardized Newick phylogenetic trees with branch length.

Moran, Steven & McCloy, Daniel & Wright, Richard (eds.) 2014. [*PHOIBLE Online*](http://phoible.org/).

R Core Team (2015). *R: A language and environment for statistical computing*. R Foundation for Statistical Computing, Vienna, Austria. URL [https://www.R-project.org/](https://www.R-project.org/).

Wickhamm, H. (2015). *stringr: Simple, Consistent Wrappers for Common String Operations*. R package version 1.0.0. [http://CRAN.R-project.org/package=stringr](http://CRAN.R-project.org/package=stringr).

Wickham, H., & Francois, R. (2015). *dplyr: A Grammar of Data Manipulation*. R package version 0.4.3. [http://CRAN.R-project.org/package=dplyr](http://CRAN.R-project.org/package=dplyr).




 

