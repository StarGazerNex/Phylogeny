# Phylogeny

## Requisites
- txt files with genes;
- Python;
- Mafft;
- modeltest-ng;
- raxml-ng;
- Figtree.


## Procedure
1- Download sequences from the GeneBank
```
python download_ASCN.py input_file output_file
```

2- 1.Align the sequences
```
mafft --auto {output1} > {output2}
```
    2.Followed by finding the model that suits best
```
modeltest-ng -i {output2} -t ml
```

