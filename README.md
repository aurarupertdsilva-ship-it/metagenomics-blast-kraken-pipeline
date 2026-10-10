# 👋 Hello, I'm Aura Rupert Dsilva

**Biotechnology & Bioinformatics Professional** specializing in genomic data analysis, high-performance computing, and computational pipeline development. I hold a Master's degree in Bioinformatics and Biotechnology from the University of Aberdeen, combining wet-lab molecular expertise with robust command-line and scripting workflows.

---

### 🛠️ Technical Toolkit

* **Programming & Scripting:** Python, Bash / Shell Scripting, Linux Command-Line Environment
* **Bioinformatics & Genomics Tools:** BLAST, Kraken2, FASTQ Utilities, ABySS, SPAdes, Velvet, Slurm Job Schedulers
* **Core Competencies:** Functional Genomics, Sequence Analysis, Data Quality Control, Pipeline Automation, Reproducible Research

---

### 🚀 Featured Bioinformatics Projects

#### 1. Genomic Analysis & Taxonomic Classification Pipeline
* **Description:** Developed command-line workflows for high-throughput genomic data analysis, focusing on sequence alignment and taxonomic profiling.
* **Key Actions:** 
  * Implemented **BLAST** for sequence homology searches and **Kraken2** for rapid metagenomic taxonomic classification.
  * Utilized FASTQ utilities for quality control, filtering, and preprocessing raw sequencing reads.
* **Tools Used:** Bash, Python, BLAST, Kraken2, Linux CLI

#### 2. De Novo Genome Assembly Pipeline
* **Description:** Built and executed automated assembly pipelines for short-read sequencing data within high-performance computing environments.
* **Key Actions:**
  * Leveraged assemblers including **ABySS, SPAdes, and Velvet** to optimize contig generation.
  * Managed resource allocation and job execution using **Slurm Job Schedulers** on HPC clusters.
* **Tools Used:** Slurm, ABySS, SPAdes, Velvet, Linux

---

### 🔬 Research Background
* **MSc Dissertation (*University of Aberdeen*):** *Screening Protein Interactions of Wapl Using In Vivo Site-Specific Cross-Linking* — Investigated chromatin-associated molecular dynamics and protein-level interactions using advanced in vivo techniques.
* **BSc Dissertation (*University of Aberdeen / Viva College*):** *Microgreen Magic* — Conducted comprehensive biochemical assays (including DPPH, DCPIP, Kjeldahl, and DNSA methods) to evaluate nutritional profiles, vitamin contents, and health-promoting properties of microgreens.

---

### 📬 Connect with Me
* **LinkedIn:** [Insert your LinkedIn URL here]
* **Email:** aurarupertdsilva@gmail.com

* #!/usr/bin/env python3
"""
Sequence Quality & Composition Analyzer
Author: Aura Rupert Dsilva
Description: A lightweight utility script to analyze sequence length, GC content, 
and nucleotide distribution for bioinformatics workflows.
"""

def calculate_gc_content(sequence):
    """Calculate the GC content percentage of a given nucleotide sequence."""
    seq_upper = sequence.upper()
    g_count = seq_upper.count('G')
    c_count = seq_upper.count('C')
    total_valid = sum(seq_upper.count(base) for base in ['A', 'T', 'G', 'C'])
    
    if total_valid == 0:
        return 0.0
    return round(((g_count + c_count) / total_valid) * 100, 2)

def analyze_sequence(header, sequence):
    """Perform basic compositional analysis on a single sequence."""
    seq_upper = sequence.upper()
    length = len(seq_upper)
    gc_content = calculate_gc_content(seq_upper)
    
    counts = {
        'A': seq_upper.count('A'),
        'T': seq_upper.count('T'),
        'G': seq_upper.count('G'),
        'C': seq_upper.count('C'),
        'N': seq_upper.count('N')
    }
    
    print(f"--- Analysis Report ---")
    print(f"Header: {header}")
    print(f"Total Length: {length} bp")
    print(f"GC Content: {gc_content}%")
    print("Base Counts:")
    for base, count in counts.items():
        print(f"  {base}: {count}")
    print("-" * 25)

if __name__ == "__main__":
    # Example dataset to test the workflow locally
    sample_header = ">Test_Sequence_001"
    sample_seq = "ATGCGTACgtaCGTACGTAGCTAGCTAGCTAatcgatcgatcgaNNN"
    
    analyze_sequence(sample_header, sample_seq)
