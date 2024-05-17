# Phylogeny

## Requisites
- txt files with genes;
- Python;
- Mafft;
- modeltest-ng;
- raxml-ng;
- Figtree.


## Procedure
#1
Download sequences from the GeneBank
```
python download_ASCN.py input_file output1
```

#2
1.    Align the sequences
```
mafft --auto output1 > output2
```
2.    Followed by finding the model that suits best
```
modeltest-ng -i output2 -t ml
```

#3
Concatenate
```
concatenate_fastas.concatenate_fastas(folder_output2,output3)
```

#4
Run the following lines in order

``` raxml-ng --msa {output3} --model {modelo} --threads {NUMBEROFTHREADS} --seed 27 --tree pars{{100}},rand{{100}} --force perf_threads ```

``` raxml-ng --bootstrap --msa {output3} --model {modelo} --threads {NUMBEROFTHREADS} --seed 27 --bs-trees autoMRE{{{10000}}} --force perf_threads ```

``` raxml-ng --support --tree {output_tree} --bs-trees {output_bs} --threads {NUMBEROFTHREADS} --force perf_threads ```
