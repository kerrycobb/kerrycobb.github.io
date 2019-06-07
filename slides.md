# Sequence Data Archiving



## What to do with sequence data when you're done?
- It is difficult to safely store your data long term
- Your raw data might have value to others
- Tax payers or generous donors might have funded your research



## International Nucleotide Sequence Database Collaboration (INSDC)
- Includes:
  - National Center For Biotechnology (NCBI)
  - European Bioinformatics Institute (EBI)
  - DNA Database of Japan (DDBJ)
- Data submitted to any one of them is shared among all of them.



## Upload Your Data!
- Don't risk losing it by trying to store it yourself
- Many journals and funding agencies require it
- Owe it to society for supporting research



## Sequence Read Archive (SRA)
- Formerly the Short Read Archive
  - Changed in anticipation of longer reads
- Repository for high-throughput sequence data



### How To Upload
<iframe data-src="https://www.ncbi.nlm.nih.gov/sra" width="1000" height="500" frameborder="0" marginwidth="0" marginheight="0" scrolling="yes" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen > </iframe>
<a href="https://www.ncbi.nlm.nih.gov/sra">https://www.ncbi.nlm.nih.gov/sra</a>



## Download Data
- Don't have a grant for sequencing?
- Can the question you have be addressed with existing data?
- Will existing data help with analyzing or augmenting data you collected?



## Existing Data
<img src="https://www.ncbi.nlm.nih.gov/Traces/sra/i/g.png" alt="SRA Database growth" style="max-height: 500px;" />



### Browse and Download Available Data
<iframe data-src="https://www.ncbi.nlm.nih.gov/sra" width="1000" height="500" frameborder="0" marginwidth="0" marginheight="0" scrolling="yes" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen > </iframe>
<a href="https://www.ncbi.nlm.nih.gov/sra">https://www.ncbi.nlm.nih.gov/sra</a>



### Browse and Download Available Data
- Most data cannot be downloaded from SRA website
- Command line tools are needed



## Command Line Data Browsing
Use Entrez Direct to fetch run info:
```
esearch -db sra -query "Placozoan [organism]" | \
efetch --format runinfo > sra_query.csv
```

Get the accession numbers:
```
awk -F "," '{print $25}' sra_query.csv
```



## Command Line Data Download
Using SRA Toolkit
```
fastq-dump --split-files <accession>.sra
```



## Command Line Data Download
- `fastq-dump` in the SRA Toolkit might be too slow for some use cases
- Aspera Connect is a faster alternative
  - It's a little harder to use



## Command Line Data Download
Using Aspera Connect and SRA Toolkit

Download sra file
```
ascp \
  -i ~/.aspera/connect/etc/asperaweb_id_dsa.openssh \
  -T \ # Disable encryption
  -k 1 \ # Permit restart of partial download
  <accession-url> \
  <file-name>.sra  
```

Accession URL looks like this:
anonftp@ftp.ncbi.nlm.nih.gov:/sra/sra-instant/reads/ByRun/sra/SRR/SRR676/SRR6768529/SRR6768529.sra



## Command Line Data Download
Using Aspera Connect and SRA Toolkit

Convert sra to fastq:
```
fastq-dump --split-files <file-path>.sra
```



### Other Repositories
- There are many other repositories for more specific types of data:
  - Expression
  - Annotations of Protein, RNA, Transposable Element, etc.
  - Genetic Variants
  - Metagenomics
  - Model Organisms



### Other Repositories
- Repositories for items associated with sequence data
  - DRYAD
  - Github
  - Zenoto
  - Open Science Framework
  - Fig Share
- Several of these provide a Digital Object Identifier (DOI) link
