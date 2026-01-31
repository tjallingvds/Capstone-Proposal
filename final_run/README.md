# TNBC Drug Cytotoxicity Prediction Model - Final Run

This directory contains all files needed to run the model training and evaluation on cloud compute.

## Directory Structure

```
final_run/
├── run.ipynb                 # Main notebook (run this)
├── requirements.txt          # Python dependencies
├── README.md                 # This file
├── data/
│   ├── raw/                  # Input data files
│   │   ├── cell_ge.csv
│   │   ├── GDSC2 Fitted Dose Response Oct 27 2023.xlsx
│   │   ├── DepMap Model Data.csv
│   │   └── drugs_with_smiles.csv
│   └── processed/            # Generated processed data
│       └── drug_graphs.pkl
├── models/                   # Saved model checkpoints
├── results/                  # All output files (metrics, plots, etc.)
├── data_splits/              # Saved train/val/test split indices
└── prebatched_data/          # Pre-batched data for faster training
```

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Run the notebook:
```bash
jupyter notebook run.ipynb
# or
jupyter lab run.ipynb
```

## What Gets Saved

The notebook automatically saves:

- **Data Splits**: Train/val/test indices saved to `data_splits/data_splits_{SPLIT_TYPE}.json`
- **Model Checkpoints**: Best models saved to `models/trial2_phase{1,2,3}_pathway_{split_type}.pt`
- **Performance Metrics**: CSV and pickle files in `results/`
- **Pre-batched Data**: Batched datasets in `prebatched_data/`
- **All Plots and Visualizations**: Saved to `results/`

## Configuration

- **SPLIT_TYPE**: Set in Cell 6. Options: `'cell_line'` (no data leakage) or `'random'`
- **Device**: Automatically uses CUDA if available, otherwise CPU
- **Paths**: All paths are relative to the notebook directory

## Notes

- All outputs are saved to files for reproducibility
- Split indices are saved to prevent data leakage during evaluation
- Model checkpoints include full state (model, optimizer, epoch, metrics)
- Results can be checked later without re-running the notebook
