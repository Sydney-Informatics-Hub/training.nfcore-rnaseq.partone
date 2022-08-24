---
title: "The nfcore-rnaseq command"
teaching: 10
exercises: 0
questions:
- "What are the main input parameters?"
- "What are the main log files?"
- "What are the main outputs?"

objectives:
- "Understanding nfcore-rnaseq inputs and outputs"

keypoints:
- Reference daatsets can be pre-downloaded or downloaded/indexed on the run.
- System resouces such as cpus and memory can be customised per step using config files.
- Excecution and timeline logs files provide a detailed summary of the run.
---


### Nextflow run command
Run the following commands when working inside this directory

```
base_path=/cvmfs/data.biocommons.aarnet.edu.au/Final_resources_250722

nextflow run $base_path/nfcore_pipeline/rnaseq/ \
        --input samplesheet.csv \                                                      # samplesheet file-name
        --outdir results \                                                             # Results folder
        --genome GRCm38 \                                                              # Reference genome
        -profile singularity \                                                         # profile e.g. singularity
        --fasta $base_path/Mouse_references/genome.fa \                                # Path: Genome fasta file
        --gtf $base_path/Mouse_references/Mmus.gtf \                                   # Path: annotation (gtf) file 
        --max_memory '6 GB' --max_cpus 2 \                                             # memory and cpu resources          
        --star_index $base_path/Mouse_references/STARIndex_sarekGenome/ \              # Path: Genome 'STAR' index file
        -with-report excecution_report.html \                                          # Excecution log file-name 
        -with-timeline timeline_report.html \                                          # Timeline log file-name
        -with-dag flowchart.png                     
```




  
