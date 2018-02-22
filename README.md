# Equivalent Junctions

This repository contains the python scripts that can be used to extarct equivalent junctions for a genome. README_eq_junc provides more details on how to run the scripts and get the summary of equivalnt junctions.

# Software

- Python 2.7.5 with Biopython installed

# Pyhton scripts

## getJunctionsFromGTF.py: 
   - determines equivalent junctions from a genome fasta file and an annotation file in the GTF format
   - usage:
      ```  
     python getJunctionsFromGTF.py -f genome_file.fa
                                 -a annotation_file.gtf
                                 -o output_file.txt
      ```
   - output file: 
         - a tab delimited file with the extracted equivalent junction sequence for each annotated exon-exon boundary: 

   ```
         equiv_junc_sequence   gene_name   chromosome   donor_exon_coordinate   acceptor_exon_coordinate 
   ```
   - example equivalent junction in the output file:
   
   ```
                             AG LEPR chr1 65420740 65425302  
   ```
   ## getJunctionsFromTxt.py: 
   - determines equivalent junction sequences from a genome fasta file and annotatiaon file in the BED format containing chr, donor, and acceptor coordinates.
   - usage: 
    ```
   python getJunctionsFromTxt.py -f genome_file.fa
                                 -t annotation_file.txt
                                 -o output_file.txt
                                 -c choromosome_column (defult=0) 
                                 -d donor_coordinate_column (default=1) 
                                 -a acceptor_coordinate_column (default=2)
                                 -s strand_column (default=3)
   ```
   - output file: 
      - a tab delimited file with the extracted equivalent junction sequence for each annotated exon-exon boundary: 
   
   ```
         equiv_junc_sequence   gene_name   chromosome   donor_exon_coordinate   acceptor_exon_coordinate 
   ```
