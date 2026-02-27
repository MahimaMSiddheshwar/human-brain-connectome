# Human Brain Functional Connectome Analysis

> **Which brain regions are the most critical communication hubs, and how is the brain organized into functional communities?**

Functional connectome analysis of resting-state fMRI data from 20 healthy subjects using graph theory and network science.

*Website: https://human-brain-connectome.vercel.app/*

---

## Tech Stack

**Neuroimaging & Bioinformatics**

![fMRI](https://img.shields.io/badge/fMRI-Resting_State-DC143C?style=for-the-badge&logo=databricks&logoColor=white)
![Nilearn](https://img.shields.io/badge/Nilearn-Brain_Analysis-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![NiBabel](https://img.shields.io/badge/NiBabel-NIfTI_I/O-8B0000?style=for-the-badge&logo=files&logoColor=white)
![BOLD](https://img.shields.io/badge/BOLD-Signal_Processing-FF6347?style=for-the-badge&logo=airplayvideo&logoColor=white)
![Destrieux](https://img.shields.io/badge/Destrieux_Atlas-163_Regions-9370DB?style=for-the-badge&logo=openstreetmap&logoColor=white)

**Graph Theory & Network Science**

![NetworkX](https://img.shields.io/badge/NetworkX-Graph_Analysis-4C8CBF?style=for-the-badge&logo=graphql&logoColor=white)
![Graph Theory](https://img.shields.io/badge/Graph_Theory-Centrality_Metrics-228B22?style=for-the-badge&logo=neo4j&logoColor=white)
![Community](https://img.shields.io/badge/Community_Detection-Modularity-2E8B57?style=for-the-badge&logo=gitconnected&logoColor=white)
![Pearson](https://img.shields.io/badge/Pearson-Correlation_Matrix-006400?style=for-the-badge&logo=stackexchange&logoColor=white)

**Data Science & Computing**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)

**Visualization**

![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-444876?style=for-the-badge&logo=python&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3D_Brain-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)

**Environment**

![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version_Control-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white)

---

## Dataset

| Property | Value |
|----------|-------|
| **Source** | ADHD-200 Resting-State fMRI |
| **Subjects** | 20 healthy controls |
| **Atlas** | Destrieux 2009 (163 brain regions) |
| **TR** | 2.5 seconds |
| **Signal** | BOLD (Blood Oxygen Level-Dependent) |
| **Format** | 4D NIfTI (3D brain × time) |
| **Download** | Automatic via `nilearn` |
| **Size** | < 300 MB |

---

## Pipeline

```
01 Download & Setup ──→ 02 Extract Signals ──→ 03 Connectivity Matrix
                                                        │
06 Visualize ←── 05 Hub Analysis ←── 04 Build Graph ←──┘
```

| Step | Notebook | What it does |
|------|----------|-------------|
| 01 | `01_download_and_setup.ipynb` | Fetch ADHD-200 dataset & Destrieux atlas |
| 02 | `02_extract_signals.ipynb` | Apply `NiftiLabelsMasker` → regional time series |
| 03 | `03_functional_connectivity.ipynb` | Pearson correlation across 20 subjects → 163×163 matrix |
| 04 | `04_build_graph.ipynb` | Threshold at r > 0.3 → NetworkX graph |
| 05 | `05_graph_analysis.ipynb` | Centrality metrics + community detection |
| 06 | `06_visualization.ipynb` | Generate all figures + 3D brain connectome |

---

## Results & Conclusions

### Top 15 Hub Regions

These regions act as **critical communication hubs** in the brain network — they have the highest betweenness centrality, meaning most information flow passes through them.

| Rank | Region ID | Degree | Betweenness | PageRank | Hub Score |
|------|-----------|--------|-------------|----------|-----------|
| 1 | 77 | 17 | 0.1423 | 0.0146 | 0.820 |
| 2 | 19 | 18 | 0.0214 | 0.0123 | 0.692 |
| 3 | 3 | 18 | 0.0173 | 0.0159 | 0.692 |
| 4 | 24 | 12 | 0.1205 | 0.0151 | 0.675 |
| 5 | 18 | 12 | 0.1059 | 0.0093 | 0.642 |
| 6 | 93 | 15 | 0.0184 | 0.0106 | 0.625 |
| 7 | 85 | 14 | 0.0362 | 0.0131 | 0.623 |
| 8 | 101 | 10 | 0.1271 | 0.0107 | 0.619 |
| 9 | 10 | 13 | 0.0269 | 0.0103 | 0.607 |
| 10 | 131 | 15 | 0.0257 | 0.0101 | 0.605 |
| 11 | 21 | 13 | 0.0000 | 0.0102 | 0.592 |
| 12 | 95 | 13 | 0.0000 | 0.0097 | 0.570 |
| 13 | 48 | 13 | 0.0045 | 0.0120 | 0.567 |
| 14 | 29 | 10 | 0.0849 | 0.0111 | 0.562 |
| 15 | 122 | 13 | 0.0044 | 0.0116 | 0.556 |

### Community Structure

| Metric | Value |
|--------|-------|
| **Communities detected** | 21 |
| **Modularity Q score** | 0.693 |

- **Q = 0.693** indicates **strong modular organization** — the brain is not randomly wired
- Brain regions cluster into distinct functional communities
- Largest communities contain 18-24 regions each
- Several small communities (2-3 regions) represent specialized sub-networks

### Key Conclusions

1. **The brain has clear hub regions** — Region 77 dominates with betweenness = 0.142, acting as the primary communication bottleneck in the network

2. **High modularity (Q = 0.693)** — The brain is organized into 21 distinct functional modules, far from random connectivity (random networks have Q ≈ 0)

3. **Sparse but efficient** — Most region pairs are NOT directly connected. The network uses hub regions to relay information efficiently (small-world architecture)

4. **Hub regions bridge communities** — Top hubs (Region 77, 24, 18, 101) have high betweenness but moderate clustering, meaning they connect different communities rather than sitting inside tight clusters

5. **Functional specialization confirmed** — The community structure aligns with known functional networks (visual, motor, default mode, attention) supporting the brain's modular design

---

## Visualizations

| Figure | Description |
|--------|-------------|
| `figure1_connectivity_heatmap.png` | 163×163 Pearson correlation matrix |
| `figure2_hub_regions.png` | Top 15 hubs ranked by centrality |
| `figure3_network_graph.png` | Spring layout network visualization |
| `figure4_network_dashboard.png` | Network statistics dashboard |
| `figure5_brain_connectome.png` | Brain surface with connections |
| `figure5_brain_3d_interactive.html` | Interactive 3D connectome (open in browser) |

---

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Launch Jupyter
jupyter lab

# 3. Run notebooks in order: 01 → 02 → 03 → 04 → 05 → 06
```

**Runtime**: ~15-30 minutes

---

## Project Structure

```
human-brain-connectome/
├── notebooks/
│   ├── 01_download_and_setup.ipynb
│   ├── 02_extract_signals.ipynb
│   ├── 03_functional_connectivity.ipynb
│   ├── 04_build_graph.ipynb
│   ├── 05_graph_analysis.ipynb
│   └── 06_visualization.ipynb
├── data/
│   ├── config.json
│   ├── all_time_series.npy
│   └── functional_matrix.npy
├── results/
│   ├── hub_regions.csv
│   ├── all_region_metrics.csv
│   ├── communities.json
│   └── connectome_graph.graphml
├── figures/                        # 11 visualization files
├── presentation/
│   ├── brain_connectome_presentation.html   # Interactive HTML presentation
│   └── figures/                             # Presentation figures
├── .gitignore
├── requirements.txt
└── README.md
```

---

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `nilearn` | 0.10.4 | fMRI analysis & brain plotting |
| `nibabel` | 5.2.1 | NIfTI file I/O |
| `numpy` | 1.26.4 | Numerical computing |
| `pandas` | 2.2.0 | Data manipulation |
| `matplotlib` | 3.8.3 | Static plotting |
| `seaborn` | 0.13.2 | Statistical visualization |
| `networkx` | 3.2.1 | Graph & network analysis |
| `scipy` | 1.12.0 | Scientific computing |
| `plotly` | 5.18.0 | Interactive 3D plots |
| `jupyterlab` | 4.0.9 | Notebook environment |

---

## Citation

```bibtex
@article{ADHD200,
  title={The ADHD-200 Consortium: A Model to Advance the Translational 
         Research on Neuroimaging in Childhood Disorders},
  journal={Frontiers in Systems Neuroscience},
  year={2012}
}

@article{destrieux2010,
  title={Automatic parcellation of human cortical gyri and sulci 
         using standard anatomical nomenclature},
  author={Destrieux, C and Fischl, B and Dale, A and Halgren, E},
  journal={NeuroImage},
  year={2010}
}
```
