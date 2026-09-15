# 🧬 AssemblyQC Replication – *Bacillus subtilis*

This project documents the reproduction of the AssemblyQC pipeline using the *Bacillus subtilis* genome as part of a class assignment for BINF6310 at Northeastern University.

AssemblyQC is a Nextflow-based pipeline that evaluates genome assembly quality using tools like Assemblathon2, BUSCO, LAI, and NCBI FCS-GX. This reproduction was executed on the Discovery HPC cluster using Singularity.

---

## 📦 Dataset

- **Organism**: *Bacillus subtilis*
- **Data Source**: NCBI Assembly (Accession: GCF_000009045.1_ASM904v1)
- **Raw FASTA**: Downloaded via FTP (not included in this repo)
- **Input Sheet**: See `assemblysheet.csv`

---

## 🔁 Pipeline Used

- GitHub Repo: [Plant-Food-Research-Open/assemblyqc](https://github.com/Plant-Food-Research-Open/assemblyqc)
- Version: Latest main branch (`-revision main`)
- Environment: Nextflow + Singularity on Discovery HPC

---

## 📄 Files Included

| File | Description |
|------|-------------|
| `README.md` | Project summary |
| `execution_notes.md` | Full terminal commands and environment setup |
| `assemblysheet.csv` | Input file listing genome used |
| `report.html` | Output HTML summary from the pipeline |

---

## ⚠️ Notes

- Raw genome files are not included due to file size.
- BUSCO failed under Singularity; this was a known issue. Other modules ran successfully.
- Only the configuration file was modified; no changes were made to the pipeline code.

---

## 📚 References

- Rashid, S., et al. (2024). *AssemblyQC: A Nextflow pipeline for reproducible reporting of assembly quality.* Bioinformatics.
- [AssemblyQC GitHub](https://github.com/Plant-Food-Research-Open/assemblyqc)
- Yang et al. (2024). [doi:10.1016/j.intimp.2024.113083](https://doi.org/10.1016/j.intimp.2024.113083)
