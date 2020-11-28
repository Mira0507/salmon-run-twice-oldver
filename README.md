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

```bash
#!/bin/bash 

salmon index -t ../rawdata/Mock_72hpi_S1.fastq.gz -i reindex -k 31 -p 8

```
