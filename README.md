# Human Brain Functional Connectome Analysis

## Biological Question

**"Which human brain regions act as the most critical communication hubs in the resting-state functional connectome, and what modular community structure does the human brain network exhibit?"**

This project analyzes the functional connectome of the human brain to identify:
1. Critical hub regions that serve as central communication nodes
2. Modular community structure within the brain network
3. Network properties that characterize human brain organization at rest

## Dataset Description

**Dataset**: ADHD200 Resting-State fMRI Dataset (nilearn)
- **Number of subjects**: 20
- **Data type**: Resting-state functional MRI (rs-fMRI)
- **Repetition Time (TR)**: 2.5 seconds
- **Brain Parcellation**: Destrieux 2009 Atlas (163 regions)
- **Expected size**: < 300 MB

The ADHD200 dataset provides high-quality resting-state fMRI data for studying intrinsic functional brain organization. Subjects were scanned at rest without any external task.

## Methods Summary

### Notebook 01: Download and Setup
- Initialize project and set random seeds for reproducibility
- Download Destrieux 2009 atlas for brain parcellation
- Download ADHD200 dataset (20 subjects)
- Create project directories and verify downloads

### Notebook 02: Extract Brain Signals
- Load raw fMRI data (4D volumes)
- Apply brain parcellation using NiftiLabelsMasker
- Extract time series signals from all 163 regions
- Standardize signals for subsequent analysis
- Visualize sample time series data

### Notebook 03: Functional Connectivity
- Calculate Pearson correlation matrices for each subject
- Average correlation matrices across all subjects
- Create publication-quality heatmaps
- Identify and rank strongest connections

### Notebook 04: Build Connectome Graph
- Apply correlation threshold (r > 0.3) to focus on strong connections
- Build weighted undirected network graph
- Calculate basic graph properties
- Export as GraphML for reproducibility

### Notebook 05: Graph Analysis
- Compute node-level centrality metrics:
  - Betweenness centrality (identifies hub regions)
  - Degree centrality
  - PageRank
  - Clustering coefficient
  - Strength (sum of edge weights)
- Detect modular community structure using greedy modularity optimization
- Compute global network statistics
- Generate comprehensive results table

### Notebook 06: Visualization
- Figure 1: Connectivity heatmap with region labels
- Figure 2: Interactive 3D connectome
- Figure 3: Static connectome projected on brain surface
- Figure 4: Hub regions bar chart colored by community
- Figure 5: Network graph with spring layout
- Figure 6: Structural vs functional connectivity comparison

## Installation

### 1. Create a virtual environment (recommended)
```bash
python -m venv connectome_env
source connectome_env/bin/activate  # On Windows: connectome_env\Scripts\activate
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter
```bash
jupyter lab
```

## How to Run the Project

Run the notebooks in order:

```bash
# Open Jupyter and execute:
1. notebooks/01_download_and_setup.ipynb
2. notebooks/02_extract_signals.ipynb
3. notebooks/03_functional_connectivity.ipynb
4. notebooks/04_build_graph.ipynb
5. notebooks/05_graph_analysis.ipynb
6. notebooks/06_visualization.ipynb
```

**Estimated Runtime**: 15-30 minutes total (depending on internet speed for downloads)

## Expected Outputs

### Data Files (in `data/`)
- `all_time_series.npy` - Extracted time series for all subjects and regions
- `functional_matrix.npy` - Group-averaged functional connectivity matrix

### Results Files (in `results/`)
- `human_connectome.graphml` - Network graph in GraphML format
- `hub_regions.csv` - Node metrics and rankings
- `communities.json` - Community detection results

### Figures (in `figures/`)
- `time_series_sample.pdf` - Sample time series from first subject
- `functional_connectivity_matrix.pdf` - Group connectivity heatmap
- `degree_distribution.pdf` - Node degree histogram
- `connectome_3d.html` - Interactive 3D connectome visualization
- `connectome_brain.pdf` - Static connectome on brain surface
- `hub_regions.pdf` - Hub regions bar chart
- `network_graph.pdf` - Network graph visualization
- `struct_vs_func.pdf` - Structural vs functional comparison

All figures saved in both PDF (300 dpi) and PNG (150 dpi) formats.

## Key Findings

*To be filled in after running the analysis*

### Hub Regions (Top 15)
[Hub region names and betweenness centrality values will be generated]

### Community Structure
[Number of communities detected and their composition]

### Network Properties
- Graph density: [value]
- Average clustering coefficient: [value]
- Number of connected components: [value]

## Dependencies and Versions

| Package | Version |
|---------|---------|
| nilearn | 0.10.4 |
| nibabel | 5.2.1 |
| numpy | 1.26.4 |
| pandas | 2.2.0 |
| matplotlib | 3.8.3 |
| seaborn | 0.13.2 |
| networkx | 3.2.1 |
| scipy | 1.12.0 |
| scikit-image | 0.22.0 |
| plotly | 5.18.0 |
| jupyterlab | 4.0.9 |
| tqdm | 4.67.0 |

## How to Cite the Dataset

If you use this dataset in your research, please cite:

```bibtex
@article{ADHD200,
  title={The ADHD-200 Consortium: A Model to Advance the Translational
         Research on Neuroimaging in Childhood},
  year={2012}
}
```

## Project Structure

```
human-brain-connectome/
├── data/                          # Downloaded datasets and intermediate data
├── notebooks/                     # Jupyter notebooks (run in order)
│   ├── 01_download_and_setup.ipynb
│   ├── 02_extract_signals.ipynb
│   ├── 03_functional_connectivity.ipynb
│   ├── 04_build_graph.ipynb
│   ├── 05_graph_analysis.ipynb
│   └── 06_visualization.ipynb
├── figures/                       # Generated visualizations
├── results/                       # Analysis results and metrics
├── requirements.txt               # Python dependencies
└── README.md                      # This file
```

## License

This project uses publicly available datasets. See individual dataset documentation for licensing details.
