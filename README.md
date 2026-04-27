# NBA Referee Bias Analysis

## Overview

This notebook examines implicit biases in NBA refereeing using Last Two Minute (L2M) reports and betting market data. It replicates and extends the methodology of Pelechrinis (2023) across three crowd presence periods: Pre-COVID (2015–2019), COVID (2020–2022), and Post-COVID (2023–2025).

## Running the Notebook

1. Clone the repository:
```bash
git clone <repo-url>
cd <repo-name>
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Download both datasets and place them in `data/input/` (see **Datasets** section below)

4. Run `bias_analysis.ipynb`

## Datasets

The datasets can be downloaded in three ways:

**Option 1 — curl (bash):**

Open bash terminal in project root, then:

```bash
cd data/input
BASE_URL="https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data"

curl -o L2M_stats_nba.zip "$BASE_URL/L2M_stats_nba.zip" \
     -o nba_2008-2025.zip "$BASE_URL/nba_2008-2025.zip"
```

**Option 1 — PowerShell:**

Open PowerShell terminal in project root, then:

```powershell
sl data\input
$BASE_URL = "https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data"

Invoke-WebRequest -Uri "$BASE_URL/L2M_stats_nba.zip" -OutFile "L2M_stats_nba.zip"
Invoke-WebRequest -Uri "$BASE_URL/nba_2008-2025.zip" -OutFile "nba_2008-2025.zip"
```

**Option 2 — manual download:**

- [L2M_stats_nba.zip](https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data/L2M_stats_nba.zip)
- [nba_2008-2025.zip](https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data/nba_2008-2025.zip)

Place both files in `data/input/` before running the notebook.

**Option 3 — direct read in notebook (no download required):**

```python
# Uncomment the URL lines in the notebook instead of the local path
# nba_data = pd.read_csv('https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data/L2M_stats_nba.zip', low_memory=False)
# betting_data = pd.read_csv('https://ai-and-ml-2026.s3.eu-north-1.amazonaws.com/decision-bias-study/data/nba_2008-2025.zip')
```

## Requirements

### Python Version

Python 3.9+

### Libraries

| Library | Version | Usage |
|---|---|---|
| `pandas` | ≥ 1.5 | Data manipulation |
| `numpy` | ≥ 1.23 | Numerical operations |
| `scipy` | ≥ 1.9 | Statistical tests (binomial, chi-squared, Spearman) |
| `matplotlib` | ≥ 3.6 | Visualizations |
| `seaborn` | ≥ 0.12 | Statistical plots |

## Repository Structure

```
├── bias_analysis.ipynb     # Main analysis notebook
├── data/
│   ├── input/              # Raw datasets
│   └── output/             # Processed datasets (game_data.csv, play_data.csv)
├── images/                 # Figures referenced in the notebook
├── requirements.txt        # Python dependencies
└── README.md               # This file
```

## Reference

Pelechrinis, K. (2023). Quantifying implicit biases in refereeing using NBA referees as a testbed. *Scientific Reports*, 13, 4664. https://doi.org/10.1038/s41598-023-31799-y
