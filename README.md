# Week-7-assessment-for-PfLS

# NGS Mutation analysis in *Schizosaccharomyces pombe*

This pipeline analyses next-generation sequencing (NGS) reads against a reference sequence to identify single nucleotide mismatches and compare change patterns.

## How to run

1.	Open the Jupyter Notebook in Google Colab
2.	Run the Setup code cells
3.	Execute all calls in the Project 1 Section from top to bottom in order

## Input and expected output

### The pipeline assumes you have 2 datasets:
-	Reference  - str – a line of sequenced to be tested against (as .txt file)
-	Reads – list of dict – a list of dictionaries for each of the invidual reads, the keys:
    -	“read_id”
    - “sample”
    - “group”
    - “sequence”
  The reads file is assumed to be .csv format
### The pipeline will give you a table for each of the groups with:
-	number of valid and invalid sequences
-	total percentage of reads with mismatches
-	total events of mismatches per sample in group
-	top 3 positions for substitutions to occur (amendable in get_top_3_pos())
-	individual substituation amount and percentage in each of the samples
-	statistical analysis of top 3 mismatch positions (amendable in get_top_3_pos())

## Code design
1. **Helper function**

      Using get_top_3_pos helped to avoid duplicating the sorting and the tie breaker when summarised the sample data and compared the positions of mismatches

2. **Kept the original data as it is**

      In analyse_reads() sequence reads were converted to uppercase and stored in new dictonaries without mutating the initial input, thus prventing the crashing in the future.

3. **Zero-valid read handling**

      summarise_samples retains samples with zero valid reads by setting mismatch_oercentage = None and compare_positions() filters and notes excluded samples before running statistics

## Testing

1. used assert to check if the function worked or not
2. made fake datasets with various errors
3. tested with empty datasets to test  for zero-valid read handling
