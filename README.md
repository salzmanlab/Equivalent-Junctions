# Equivalent Junctions

This repository contains the python scripts that can be used to extarct equivalent junctions for a genome. The links for downloading a number of example genomes analyzed in the paper are [here](https://github.com/roozbehdn/Equivalent-Junctions/blob/master/equiv_junc_genomes.md).

# Software

- Python 3.6.1 with Biopython 1.71 installed

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
         equiv_junc_sequence   gene_name   strand   chromosome   donor_exon_coordinate   acceptor_exon_coordinate 
   ```
   - example equivalent junction in the output file:
   
   ```
                                    AG LEPR chr1 + 65420740 65425302  
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
         equiv_junc_sequence   gene_name   strand   chromosome   donor_exon_coordinate   acceptor_exon_coordinate 
   ```
   Note: Example genome and annotations that have been analyzed for equivalent junctions are provided in equiv_junc_genomes.md. The codes are pretty general and any genome can be used for equivalent junction analysis.

## Computing the number of equivalent junctions:

After running the python script and obtaining the output_file containing the equivalent junction sequence for each exon-exon junction, the following command gives the total number of each equivalent junction sequence:
```
cut -f1,3,4,5,6 output_file.txt | sort -u |cut -f1 | sort |uniq -c| sort -k1nr > output_file_equivSeqCounts.txt 
```
