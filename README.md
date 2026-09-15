AssemblyQC Replication – Bacillus subtilis Genome QC
Nextflow pipeline reproduction evaluating genome assembly quality on HPC using Singularity containers
Class project for BINF6310 – Northeastern University | Sep 2026

What This Project Does
Reproduces the AssemblyQC pipeline to assess the quality of a Bacillus subtilis genome assembly (NCBI GCF_000009045.1) using multiple QC tools (Assemblathon2, LAI, NCBI FCS-GX) and generates an interactive HTML report. Demonstrates proficiency in bioinformatics workflow automation, HPC execution, and reproducible research practices.

Tech Stack & Environment
Component	Tool/Version
Workflow Manager	Nextflow
Containerization	Singularity 3.10.3
Environment	Miniconda (binf6310)
Compute	Discovery HPC Cluster (Northeastern)
Input Data	B. subtilis FASTA (NCBI Assembly)
Pipeline	Plant-Food-Research-Open/assemblyqc

Repository Structure

assemblyqc-replication/
├── README.md                  # This file
├── execution_notes.md         # Full terminal commands & setup
├── config/
│   └── assemblysheet.csv      # Input file (tag, fasta)
├── output/
│   └── report.html            # QC summary report (view in browser)
└── assemblyqc/                # Cloned pipeline directory

How to Reproduce
Prerequisites: Access to HPC with Singularity, Nextflow, and Miniconda.

bash
# 1. Start interactive session
srun --pty --partition=courses --export=ALL --mem=16G -t 4:00:00 -c 2 bash

# 2. Load modules
module load miniconda3/23.11.0
source activate binf6310
module load singularity/3.10.3

# 3. Clone and run pipeline
git clone https://github.com/Plant-Food-Research-Open/assemblyqc.git
cd assemblyqc
nextflow run Plant-Food-Research-Open/assemblyqc \
  -revision main \
  -profile singularity \
  --input config/assemblysheet.csv \
  --outdir output
Resume after interruption: add -resume flag to the nextflow run command.

Key Results
Assemblathon2, LAI, NCBI FCS-GX: Completed successfully

BUSCO: Failed inside Singularity (known compatibility issue); run separately for gene-space completeness

Output: Interactive report.html with unified QC metrics across tools

What I Learned
Containerized workflow execution on HPC environments

Troubleshooting pipeline failures (BUSCO/Singularity incompatibility)

Reproducible research documentation for bioinformatics projects

Interpreting multi-tool QC reports for genome assemblies


References
Rashid, S., et al. (2024). AssemblyQC: A Nextflow pipeline for reproducible reporting of assembly quality. Bioinformatics.

Pipeline: github.com/Plant-Food-Research-Open/assemblyqc

Documentation: plant-food-research-open.github.io/assemblyqc

Contact
Sushma Ankathi
Bioinformatics Professional | Toronto, ON
LinkedIn - www.linkedin.com/in/
sushma-ankathi-3369a535a
