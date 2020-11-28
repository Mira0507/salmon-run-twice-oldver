## Q: Do two Salmon (ver. 0.12.0) runs in a row give exactly the same counts?

### Conda environment 

```yml
name: salmon-old
channels:
  - conda-forge
  - bioconda 
  - defaults 
dependencies:
  - salmon=0.12.0 
  - r-base 
  - bedtools 
  - gawk 
```

### Indexing
This run requires reindexing due to indexing incompatibility 
(reindex.sh) 

```bash
#!/bin/bash 

salmon index -t ../rawdata/Mock_72hpi_S1.fastq.gz -i reindex -k 31 -p 8

```

### 1. with --gcBias & --seqBias

```bash

#!/bin/bash

samples=(Mock_72hpi_S{1..3} SARS-CoV-2_72hpi_S{7..9})

rawdir=../rawdata

prefix=gc-seq-quant1


for read in ${samples[*]} 
do
    salmon quant -i reindex -l A --gcBias --seqBias -r $rawdir/$read.fastq.gz -p 8 --validateMappings -o $prefix/${read}.quant
done
```
