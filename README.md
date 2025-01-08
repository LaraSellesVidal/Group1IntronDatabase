# Introduction

This repository presents the comprehensive group 1 intron database and associated files. 

The repository contains the following files and folders:
- **intronDatabaseDF.tsv.xz**: a compressed TSV (tab-separated values) file containing the main group 1 intron database. The file can be opened with standard software such as Microsoft Excel or macOS Pages, or directly parsed with Python, R, AWK, etc.
- **homingEndonucleasesDF.tsv**: a TSV file listing the potential homing endonucleases located in each group 1 intron
- **full_workflow_clean.ipynb**: a Jupyter notebook providing the entire workflow used to generate this resource
- **subtype_MSA**s: a folder containing the multiple alignment files used to generate the subtype covariance models. Multiple alignments are provided in [Stockholm format](https://sonnhammer.sbc.su.se/Stockholm.html)
- **subtype_CMs**: a folder containing the covariance model for each group 1 intron subtype. Covariance models were generated from the corresponding multiple alignments with [Infernal](http://eddylab.org/infernal/)
- **GUI**: a folder containing distributions of the main group 1 intron database as a Flask application for all major platforms (Linux, macOS and Windows)

The recommended and simplest way to use the database is to decompress the main database file (**intronDatabaseDF.tsv.xz**) and work with it directly either by opening it with tools such as Microsoft Excel or macOS Pages, or parsing it with Python/R/AWK.

The GUI provides access to the database through embedding it in a Flask application. Additionally, the database can be [accessed online](https://online-group-1-intron-database.onrender.com). The source code for the GUI implementation can be found in [this repository](https://github.com/LaraSellesVidal/OnlineGroup1IntronDatabase).

It should be noted that Microsoft Excel can mishandle the database file when opening it due to not recognizing the file encoding as UTF-8. In order to ensure all fields are properly read in Microsoft Excel, the following steps should be followed:
1.	Go to Data tab, Get Data submenu and select From Text, then choose the database file.
2.	In the next screen, options must be selected as Delimited file (since columns are not fixed width) and, importantly, Unicode (UTF-8) in the File origin menu.
3.	Then, Tab should be selected as the delimiter.
4.	In the final screen, the data type of specific columns can be chosen. We recommend choosing explicitly type Text for columns precedingExonSequence and consensusStruc-turalElements to avoid Excel interpreting them as some other data type.

# Fields available in the main intron database

The main group 1 intron database contains the following 29 fields for each intron:

-	intronID: a unique identifier for each intron, containing the GenBankID of the sequence in which it was found.
-	GenBankID: the GenBankID of the sequence in which the intron was found.
-	startPosition: the first position of the intron sequence, includ-ing the terminal U of the 5’ flanking exon.
-	endPosition: the last position of the terminal sequence (most frequently, the terminal G).
-	intronSequence: sequence of the intron.
-	intronLength: length of the intron sequence.
-	intronSubtype: subtype of the intron.
-	strand: strand in which the intron was found (either forward or reverse).
-	organism: species in which the intron is located.
-	organismType: broad category to which the organism of the corresponding intron belongs.
-	subcellularLocation: subcellular compartment where the se-quence containing the intron is located.
-	organismTaxID: unique NCBI taxonomy idenfier (taxid) of the organism of the corresponding intron.
-	precedingExonSequence: sequence of the exon located be-fore the intron (5’ exon), up to 300 nucleotides.
-	followingExonSequence: sequence of the exon located after the intron (3’ exon), up to 300 nucleotides.
-	eternafoldSecondaryStructure: EternaFold secondary struc-ture prediction of the intron, in dot-bracket notation.
-	viennaSecondaryStructure: ViennaRNA secondary structure prediction of the intron, in dot-bracket notation.
-	contrafoldSecondaryStructure: CONTRAfold secondary structure prediction of the intron, in dot-bracket notation.
-	rnastructureSecondaryStructure: RNAstructure secondary structure prediction of the intron, in dot-bracket notation.
-	consensusSecondaryStructure: secondary structure predic-tion of the intron obtained by alignment to the group I intron covariance model with Infernal, in WUSS notation.
-	consensusStructuralElements: group I intron structural ele-ment assignment based on alignment to the corresponding group I intron subtype covariance model with Infernal.
-	infernalHitStartPosition: the first position of the region in the containing GenBank sequence against which a hit with the group I intron covariance model was found.
-	infernalHitEndPosition: the last position of the region in the containing GenBank sequence against which a hit with the group I intron covariance model was found.
-	infernalHitEValue: e-value of the hit with the group I intron covariance model.
-	infernalHitBitScore: bit score of the hit with the group I in-tron covariance model.
-	infernalHitU10Position: position in the containing GenBank sequence that was aligned with U10 of the group I intron covariance model (note that, in some cases, no position was aligned with U10).
-	infernalSubtypeHitStartPosition: the first position of the re-gion in the containing GenBank sequence that aligned with the covariance model of the corresponding intron subtype.
-	infernalSubtypeHitStartPosition: the last position of the re-gion in the containing GenBank sequence that aligned with the covariance model of the corresponding intron subtype.
-	infernalSubtypeHitEValue: e-value of the hit with the corre-sponding intron subtype covariance model.
-	infernalSubtypeHitBitScore: bit score of the hit with the cor-responding intron subtype covariance model.
