# COMP 334 – Assignment 1: International Football Results Analysis

## Overview

For this assignment, I worked with the **International Football Results** dataset from Kaggle, which contains records of international football matches from 1872 to 2026. I used **Anaconda** and **Jupyter Notebook** to explore the data, answer the exercise questions, and produce the required visualizations. Everything is documented step by step inside my notebook with both code and markdown explanations.

## Repository Contents

| File | Description |
|------|-------------|
| `Assignment1.ipynb` | My completed Jupyter Notebook with all code, explanations, and visualizations |
| `results.csv` | The main dataset I loaded and analysed |
| `goalscorers.csv` | Supplementary dataset – goal scorers for each match |
| `shootouts.csv` | Supplementary dataset – penalty shootout records |
| `former_names.csv` | Supplementary dataset – historical team name changes |
| `requirements.txt` | Python packages required to run the notebook |
| `README.md` | This file |

## What I Did in the Notebook

My notebook follows the exact structure of the exercise document. Each section contains the code I used together with a markdown explanation of what the code does and what I found.

### Step 1 – Loading the CSV
I imported `pandas` and `matplotlib`, loaded `results.csv` into a DataFrame, and converted the `date` column to datetime so that year-based queries work correctly.

### Step 2 – Basic Exploration
I answered every question the exercise asked:

| Question | My Answer |
|----------|-----------|
| How many matches are in the dataset? | **49,071** matches |
| What is the earliest and latest year? | **1872** to **2026** |
| How many unique countries are there? | **269** unique countries |
| Which team appears most frequently as home team? | **Brazil** with 610 home matches |

I used `df.shape`, `df["date"].dt.year.min()` / `.max()`, `df["country"].nunique()`, and `df["home_team"].value_counts()` to arrive at these answers, as the exercise hinted.

### Step 3 – Goals Analysis
I created a `total_goals` column (`home_score + away_score`) and then answered:

| Question | My Answer |
|----------|-----------|
| Average goals per match | **2.94** |
| Highest scoring match | **Australia 31–0 American Samoa** (11 Apr 2001) |
| More goals at home or away? | Home teams scored **86,182** vs away **58,011** |
| Most common total goals value | **2** |

### Step 4 – Match Results
I wrote a `match_result` function that classifies each row as Home Win, Away Win, or Draw, then used `value_counts(normalize=True)` to compute percentages:

| Outcome | Percentage |
|---------|------------|
| Home Win | **49.00%** |
| Away Win | **28.27%** |
| Draw | **22.73%** |

Based on this, I concluded that **home advantage clearly exists** — home teams win nearly half of all matches, far more than away teams.

I also counted total wins per team (combining home and away wins) and found that **Brazil** leads with **669** wins overall.

### Step 5 – Visualizations
I produced the three charts the exercise required:

1. **Histogram of total goals per match** – shows that low-scoring matches dominate, with a right-skewed distribution.
2. **Bar chart of match outcomes** – visually confirms the home-win pattern.
3. **Top 10 teams by total wins (horizontal bar chart)** – Brazil, England, Germany, Argentina, and Sweden fill the top five.

All charts use `matplotlib` with the `seaborn-v0_8-whitegrid` style for a clean look.

## Key Findings

- The dataset spans **154 years** of international football.
- On average, a match produces roughly **3 goals**.
- Home advantage is real: home teams win **49%** of matches and outscore away teams by a wide margin.
- **Brazil** is both the most frequent home team and the most successful team historically.

## How to Run

1. Make sure you have Python with `pandas` and `matplotlib` installed (or use Anaconda):
   ```bash
   pip install -r requirements.txt
   ```
2. Open `Assignment1.ipynb` in Jupyter Notebook or JupyterLab and run all cells.

## Tools I Used

- **Python 3** (via Anaconda)
- **Jupyter Notebook** for interactive exploration
- **pandas** for data manipulation
- **matplotlib** for plotting
