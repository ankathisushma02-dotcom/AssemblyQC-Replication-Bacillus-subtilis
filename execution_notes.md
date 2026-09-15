# 🧾 Pipeline Execution Notes

## Environment
- Executed on: HPC with Singularity support
- Container profile used: `-profile singularity`
- Environment: Miniconda + Nextflow + Singularity
- Tools: AssemblyQC (Nextflow-based genome assembly QC pipeline)
- No local tool installations required

---

## Setup Commands

```bash
# Start interactive session
srun --pty --partition=courses --export=ALL --mem=16G -t 4:00:00 -c 2 bash

# Load environment and Singularity
module load miniconda3/23.11.0
source activate binf6310
module load singularity/3.10.3
```

---

## Clone and Test Pipeline

```bash
# Clone the AssemblyQC pipeline
git clone https://github.com/Plant-Food-Research-Open/assemblyqc.git
cd assemblyqc

# Optional: test run to validate configuration
nextflow run . -profile singularity,test --outdir output
```

---

## Dataset Preparation

```bash
# Download genome FASTA
wget ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/009/045/GCF_000009045.1_ASM904v1/GCF_000009045.1_ASM904v1_genomic.fna.gz
gunzip GCF_000009045.1_ASM904v1_genomic.fna.gz
```

---

## Input File

`assemblysheet.csv` (in `config/` folder):

```csv
tag,fasta
B_subtilis,GCF_000009045.1_ASM904v1_genomic.fna
```

---

## Run Command

```bash
nextflow run Plant-Food-Research-Open/assemblyqc \
  -revision main \
  -profile singularity \
  --input config/assemblysheet.csv \
  --outdir output
```

To resume after interruption:

```bash
nextflow run Plant-Food-Research-Open/assemblyqc \
  -revision main \
  -profile singularity \
  --input config/assemblysheet.csv \
  --outdir output \
  -resume
```

---

## Output

```bash
# Transfer HTML report to your machine
scp <username>@login.discovery.neu.edu:/path/to/output/report.html ~/Downloads/
```

Open `report.html` in a browser to explore the full QC summary.

---

## Notes
- BUSCO module failed inside Singularity container (known compatibility issue).
- BUSCO was run separately to assess gene-space completeness.
- Other modules (Assemblathon2, LAI, NCBI FCS-GX) completed successfully.