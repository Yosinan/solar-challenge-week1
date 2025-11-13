# solar-challenge-week1

Cross-country solar farm analysis for MoonLight Energy Solutions. This project performs exploratory data analysis (EDA) on solar radiation data from Benin, Sierra Leone, and Togo to identify high-potential regions for solar installation.

## Quick Start

```bash
# Clone the repository
git clone https://github.com/Yosinan/solar-challenge-week1.git
cd solar-challenge-week1

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install --upgrade pip
pip install -r requirements.txt

# Launch Jupyter
jupyter lab
```

## Project Structure

```
solar-challenge-week1/
├── .github/workflows/ci.yml    # CI/CD pipeline
├── .gitignore                   # Git exclusions
├── requirements.txt            # Python dependencies
├── README.md                   # This file
├── FINAL_REPORT.md             # Analysis report
├── data/                       # Data files (gitignored)
│   ├── benin-malanville.csv
│   ├── sierraleone-bumbuna.csv
│   ├── togo-dapaong_qc.csv
│   └── *_clean.csv            # Cleaned datasets (generated)
├── notebooks/                  # Analysis notebooks
│   ├── benin.ipynb            # Benin EDA
│   ├── sierraleone.ipynb      # Sierra Leone EDA
│   ├── togo.ipynb             # Togo EDA
│   └── compare_countries.ipynb # Cross-country comparison
└── scripts/                    # Utility scripts
    ├── generate_eda_notebooks.py
    └── generate_comparison_notebook.py
```

### Folder Descriptions

- **`data/`**: Raw and cleaned CSV files (gitignored). Contains solar radiation measurements from three countries.
- **`notebooks/`**: Jupyter notebooks for EDA and comparison analysis. Each country has a dedicated notebook.
- **`scripts/`**: Python scripts for generating notebooks programmatically.
- **`.github/workflows/`**: GitHub Actions CI configuration for automated testing.

## Usage

### Running Analysis Notebooks

**1. Country-Specific EDA** (run in order):

```bash
jupyter notebook notebooks/benin.ipynb
jupyter notebook notebooks/sierraleone.ipynb
jupyter notebook notebooks/togo.ipynb
```

Each notebook:
- Loads raw data from `data/`
- Performs cleaning and analysis
- Generates visualizations
- Exports cleaned data to `data/<country>_clean.csv`

**2. Cross-Country Comparison** (after running country notebooks):

```bash
jupyter notebook notebooks/compare_countries.ipynb
```

This notebook loads cleaned CSVs and performs statistical comparisons.

### Running Scripts

```bash
# Generate EDA notebooks
python scripts/generate_eda_notebooks.py

# Generate comparison notebook
python scripts/generate_comparison_notebook.py
```

### Example Workflow

```bash
# 1. Activate environment
source venv/bin/activate

# 2. Start Jupyter
jupyter lab

# 3. Run notebooks in order:
#    - benin.ipynb → generates benin_clean.csv
#    - sierraleone.ipynb → generates sierraleone_clean.csv
#    - togo.ipynb → generates togo_clean.csv
#    - compare_countries.ipynb → uses cleaned CSVs
```

## Dependencies

- pandas ≥2.0.0
- numpy ≥1.24.0
- matplotlib ≥3.7.0
- seaborn ≥0.12.0
- scipy ≥1.10.0
- scikit-learn ≥1.3.0
- jupyter ≥1.0.0

See `requirements.txt` for complete list.

## Output Files

After running notebooks, cleaned datasets are saved to:
- `data/benin_clean.csv`
- `data/sierraleone_clean.csv`
- `data/togo_clean.csv`

## Troubleshooting

**ModuleNotFoundError**: Ensure virtual environment is activated and dependencies installed.
```bash
source venv/bin/activate
pip install -r requirements.txt
```

**Data files not found**: Verify CSV files exist in `data/` directory.
```bash
ls data/
```

## Contributing

This is a challenge project. For improvements:

1. Review notebook markdown cells for analysis details
2. Check existing branches for feature work
3. Follow the branching strategy: `eda-<country>` for country analysis, `compare-countries` for comparison

## License

Part of the Solar Data Discovery Challenge.
