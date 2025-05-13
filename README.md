# String-Reconstruction-from-Gapped-Patterns-k-d-mers-

#  Description

This script implements functions for reconstructing a string from a sequence of gapped patterns, also known as (k,d)-mers. These are pairs of k-length substrings separated by a fixed distance d. This method is used in computational biology to reconstruct nucleotide sequences from paired-end reads, where each read consists of two k-mers with a known gap between them.

# The script includes two main functions:

* StringSpelledByPatterns(patterns): Reconstructs a string from a list of overlapping k-mers.
* StringSpelledByGappedPatterns(k, d, gapped_patterns): Reconstructs a string from a list of gapped patterns using a given k-mer size and gap distance.



# Usage
```
k = 4
d = 2
gapped_patterns = [
    "GACC|GCGC",
    "ACCG|CGCC",
    "CCGA|GCCG",
    "CGAG|CCGG",
    "GAGC|CGGA"
]

result = StringSpelledByGappedPatterns(k, d, gapped_patterns)
print(result)
```
# Expected Output
GACCGAGCGCCGGA

# Function Descriptions
StringSpelledByPatterns(patterns)

Reconstructs a contiguous string from a list of overlapping patterns. Assumes that each pattern overlaps the next by k-1 characters.
```
def StringSpelledByPatterns(patterns):
    k = len(patterns[0])
    text = patterns[0]
    for pattern in patterns[1:]:
        text += pattern[-1]
    return text
```
StringSpelledByGappedPatterns(k, d, gapped_patterns)

Reconstructs a string from gapped (k,d)-mers, where each pattern is of the form "prefix|suffix". The function combines the prefix and suffix strings reconstructed from the respective k-mers and resolves the gap d to form the final output.

# Applications

* Sequence assembly from paired-end sequencing data
* Educational purposes in string reconstruction problems in bioinformatics
* Algorithm development for genome assembly pipelines

# License

*  This project is licensed under the MIT License.
