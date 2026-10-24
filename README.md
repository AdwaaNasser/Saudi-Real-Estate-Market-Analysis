# Saudi Real Estate Market Analysis

An analysis of real estate sale transactions in Saudi Arabia from April to June 2026. The project examines transaction prices, property areas, and differences across cities and property classifications.

The repository contains the original dataset, the shared cleaned dataset, and notebooks for data cleaning and exploratory data analysis (EDA).

## Dataset

| Item | Details |
| --- | --- |
| Period | April 1–June 30, 2026 |
| Original records | 34,664 |
| Cleaned records | 34,279 |
| Main fields | Region, city, neighborhood, transaction reference, dates, property classification, property count, price, and area |
| Derived field | Price per square metre |

Each record represents a transaction, which may include more than one property. The original CSV is preserved in `data/raw/`. The cleaning notebook writes to `data/cleaned/`, and the EDA notebook reads that output.

## Repository Structure

```text
data/
├── raw/
│   └── transactions.csv
└── cleaned/
    └── clean.csv
notebooks/
├── 01_cleaning.ipynb
└── 02_eda.ipynb
reports/
└── figures/
requirements.txt
```

## Getting Started

Requires Python 3.10 or later and Git. A Python virtual environment is recommended.

```bash
git clone https://github.com/AdwaaNasser/Saudi-Real-Estate-Market-Analysis.git
cd Saudi-Real-Estate-Market-Analysis
python -m pip install -r requirements.txt
cd notebooks
jupyter notebook
```

Run notebooks with `notebooks/` as the working directory so their relative data paths resolve correctly.

### Google Colab

Open either notebook in Colab and run the following setup cell once in a new session:

```python
!git clone https://github.com/AdwaaNasser/Saudi-Real-Estate-Market-Analysis.git /content/real-estate
%cd /content/real-estate/notebooks
%pip install -r ../requirements.txt
```

If Colab requests a runtime restart after installation, restart it and run the `%cd` line again before executing the notebook. Files generated in Colab remain in that session until downloaded or committed to the repository.

## Notebook Workflow

| Notebook | Purpose | Output |
| --- | --- | --- |
| [01_cleaning.ipynb](notebooks/01_cleaning.ipynb) | Prepare the raw transaction data and apply the cleaning rules | `data/cleaned/clean.csv` |
| [02_eda.ipynb](notebooks/02_eda.ipynb) | Explore distributions, relationships, and differences between transaction groups | Charts and observations in the notebook; three PNGs in `reports/figures/` |

Run the cleaning notebook first when regenerating the dataset, then run the EDA notebook from top to bottom. To explore the committed dataset, start directly with the EDA notebook.

The EDA covers:

- Price distributions on original and logarithmic scales.
- Area, property count, and price-per-square-metre distributions.
- Price comparisons by area and city.
- Pearson and Spearman correlations.
- Differences across property classifications.

## Data Notes

- The cleaning rules exclude 385 transactions. These exclusions reflect the chosen thresholds, rather than independently verified data-entry errors.
- Price and area are treated as Saudi riyals and square metres. These units still need confirmation against the original source documentation.
- Findings describe the supplied three-month dataset and should not be treated as estimates for the entire Saudi market.
- Price per square metre is calculated from transaction price and area. It should not be used as an independent input when predicting transaction price.

Changes to data preparation belong in the cleaning notebook. Regenerate `clean.csv` and rerun the EDA after any cleaning changes so the shared data and reported results remain consistent.
