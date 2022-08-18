---
title: "Technical performance"
teaching: 10
exercises: 0
questions:
- "What information does the timeline log file provide us?"
- "How can we estimate the CPU/memory resource requirements?"
- "What were the main observations and possible limitations when running the pipeline?"

objectives:
- "Understand the timelines for multiple processes"
- "Estimate the resource requirements for multiple processes"
- "Analysing the technical requirements to run nfcore pipelines"

keypoints:
- 
---

## Workflow timeline 

<p align="center">
<img src="{{ page.root }}/fig/timeline.png" style="margin:10px;height:500px"/>
</p>

- Different processing times for different tools.
- Each process can be assigned specifc resources using a nextflow.config file.
- Nextflow parallises runs of multiple samples for specific processes depending on the available rersources; This step can thus get constrained by available resources (CPUs/memory) on the resource (here Nimbus VM).


## Compute resource usage 
<p align="center">
<img src="{{ page.root }}/fig/cpu_usage.png" style="margin:10px;height:500px"/>
</p>

<p align="center">
<img src="{{ page.root }}/fig/memory_usage.png" style="margin:10px;height:500px"/>
</p>

- Shows multiple graphical statistics displaying the resource usage for various processes in the run.
- This helps to get an estimate of the required resources for independant processes and assign them for future runs.


### Analysing the technical requirements
- **Big data size reflecting on resource requirements**: The data used for this run is massively subsetted. Real bioinformatics samples for RNASeq are in the range of few GB. Many bioinformatics tools can use multiple CPUs and quite a few also display high memory requirements.
- **Storing big reference databases for re-use**: Resources such as "cvmfs" will be ideal for storing big sized reference datasets in central repostories. This is being demonstrated in today's workshop.
- **Storing most recent version of the 'nfcore software; as backup**: Although it is recommended (and theorotically possible) to download the latest version of a nfcore pipeline, it was observed that the most recent version of nfcore-rnaseq displayed errors when I attempted to download it. So, storing a near recent copy in the "cvmfs" solved his issue. Since (possibly) minor changes are observed between sub-versions of nfcore pipelines, this approach can be used as an effective backup.
- **Storing singularity containers in cvmfs!!**: Need to weigh the pros and cons! - Also,  this is directly dependant on whether we download the nfcore-pipeline on the fly (or use an older version)...
- **X11 Forwarding**: The analysis can be streamlined if the user is able to visualise and run GUI based applications on the Vm instances.


### Part 2 (Gene counts to Differential expression)
* This was **Part 1** of the RNASeq analyis
* The demostrated nfcore-rnaseq pipeline simplifies the processing of sequence-data to gene counts.
* We use RStudio (available on Nimbus VM) for **Part 2** of the analysis.


