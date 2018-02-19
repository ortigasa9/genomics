# taenia_script
Outline of the scripts contained in this repository and their functions

Name: Inframe//
Description: 
A python script using the biopython package. Using a multiple alignment fasta file as input,
it starts by identifying the positions of every gap in the reference sequence and saving the
values in the form of a list. Using these values as parameters, the script then generates a
new multiple sequence alignment object only including columns where a gap in the reference
sequence at that position wasn't identified. Finally, in a very similar fashion, the script
parses through each individual sequence searching for mid-sequence stop codons, records the
position values, and generates one final multiple sequence alignment object where all columns
corresponding to either gaps in the reference sequence or mid-sequence stop codons have been
removed. V01 inherently specifies the input file name, while V02 allows for user-defined input
and is thus more convenient for use in pipelines. 

Name: Inter_leaved//
Description: 
A python script. This script adds an "I" to the first line of a multiple sequence alignment fasta
file. This step is necessary when using an interleaved alignment format, as otherwise PAML will
assume a sequential format by default. Must be used after Phylip and before PAML.

Name: Out_extract//
Description:
A python script. This script generates a text file from the PAML output containing only the table
with the dN/dS values for each branch. This is the input required for the R script.

Name: Master_script//
Description:
A bash script. Uses all the previous scripts, along with the following programs: Clustal Omega,
Phylip, PAML. If executed inside a file containing any number of raw sequences, it will produce
an equal number of text files containing their respective dN/dS tables, which can then be used
as input for the R script. Executed as "yes | ./script" in the command line due to the user input
requested by Phylip. 

Name: R_script//
Description:
An R script. Set the working directory to the folder containing the output files from master_script.
Running the script will automatically combine all the dN/dS tables from the text files into a single
table and generate a new column to indicate the corresponding gene name for each value. 




