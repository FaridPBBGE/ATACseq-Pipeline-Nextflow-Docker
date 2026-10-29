# ATAC-seq Analysis Pipeline (Nextflow & Docker)

[![Nextflow](https://img.shields.io/badge/nextflow-%E2%89%A525.10.4-brightgreen.svg)](https://www.nextflow.io/)
[![docker](https://img.shields.io/badge/container-Docker-blue.svg)](https://www.docker.com/)
[![nf-core](https://img.shields.io/badge/nf--core-atacseq-orange.svg)](https://nf-co.re/atacseq)

## Overview
This repository contains a containerized, reproducible bioinformatics pipeline for processing and analyzing **Assay for Transposase-Accessible Chromatin using sequencing (ATAC-seq)** data. The pipeline maps chromatin accessibility, identifies transcription factor binding sites, and discovers open chromatin regions.

---

## Pipeline Architecture (`nf-core/atacseq`)
1. **Quality Control & Trimming**: FastQC and Trim Galore! for adapter removal and read quality verification.
2. **Alignment**: Mapping paired-end reads to the reference genome using **BWA**.
3. **Filtering**: Removing mitochondrial reads, multi-mappers, and duplicates using **SAMtools** and **Picard**.
4. **Peak Calling**: Identifying open chromatin regions using **MACS2**.
5. **Consensus Peaks & Annotation**: Generating consensus peak sets and annotating genomic features using **HOMER**.

---

## System Requirements & Execution
Optimized for local containerized execution on resource-constrained environments (e.g., 8 GB RAM laptop running WSL2/Docker) using a custom configuration (`laptop.config`).

### Quick Start (Test Profile)
```bash
nextflow run nf-core/atacseq \
  -profile test,docker \
  -c laptop.config \
  --outdir ./results
