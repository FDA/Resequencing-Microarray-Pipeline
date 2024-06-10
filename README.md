Project overview

The safety of blood and blood-based products is a critical priority in blood transfusion and 
organ transplantation. The Duncan Laboratory at the Center for Biologics Evaluation and 
Research, FDA, has developed a proof-of-concept, multiplexed detection, and identification 
platform- RPM-BBPv.2, that interrogates clinical samples for the presence of viral, bacterial, and 
protozoan pathogens [1]. 

The bbp_i2o data processing pipeline

The bbp_i2o was originally implemented to process data from the RPM-BBPv.2 platform and 
provide a readout of the list of pathogens likely present in a test sample. 
The program is adapted to take the sequence file (a text file of the base calls for all the tiles on 
the microarray) from a run of RPM-BBPv.2 as its only user-defined input.
It outputs the following files:
(a)	List of tile sequences with C3 scores greater than or equal to 20.0 that were aligned 
against the nt database (file name: <sample name>.blast.in.fst. Can be read with 
Notepad)
(b)	The BLAST report listing the top hits for each tile, along with control results (file name: 
<sample name>.blast.report. Opens with Notepad)
(c)	The detailed BLAST report in HTML format (file name: <sample name>.blast.html)
(d)	A calculation of the rank order of the species hits in the BLAST results (file name: 
<sample name>.ID.report. Can be opened with Notepad)
(e)	A file containing species rejected for unknown names (file name: <sample 
name>.Unrecognized.Names. Can be read with Notepad)

Installation/Dependencies

The bbp_i2o program is written in Perl.
To run the program, you will need to install the following
i.	Perl modules: (a) File::Path (b) List::MoreUtils
ii.	Packages: the BLAST, sequence alignment package from NCBI
iii.	Databases: nt, the non-redundant NCBI nucleotide collection
iv.	Additional files: tile_contaminating_sequences: a mask file with coordinates on each 
sequence tile to be masked; ScientificNamesList - a file that contains the list of less 
specific scientific names. These files are included with this version of bbp_i2o.

After downloading bbp_i2o onto your machine, open the program with a text editor and 
update:
i.	$BLASTN to the full path of the blastn module of your BLAST package.
ii.	$BLAST to the full path to the nt database on your machine.
iii.	$TILECONTFILE to the full path to the tile_contaminating_sequences file on your 
machine.
iv.	$ScientificNamesFile to the path of ScientificNamesList file on your machine.
The bbp_i2o program has examples of paths we use in our laboratory.

Running bbp_i2o

The program is run as perl bbp_i2o <name of input sequence file>. It takes 5 -10 minutes to 
complete running.


1.	Kourout, M., et al., Multiplex detection and identification of viral, bacterial, and 
protozoan pathogens in human blood and plasma using a high-density resequencing 
pathogen microarray platform. Transfusion, 2016. 56(6 Pt 2): p. 1537-47.

