# Primeira Liga Season Prediction 🇵🇹⚽

A machine learning project that predicts the 2025-2026 Primeira Liga (Portuguese football league) season outcomes using historical data from 2014-2025.

## Overview

This project scrapes historical league table data from FBref, engineers features based on team performance trends, and uses Random Forest regression to predict final season points and championship probabilities for the 2025-2026 season.

## Key Features

- **Historical Data Collection**: Scrapes 12 seasons of Primeira Liga data (2014-2026)
- **Feature Engineering**: Creates sophisticated features including:
  - Previous season statistics (points, goal difference, wins, rank)
  - Multi-season rolling averages (2-year and 3-year means)
  - Performance trends (point trajectory over last 3 seasons)
  - Per-game efficiency metrics (goals for/against per match)
- **Machine Learning Model**: Random Forest Regressor with 300 estimators
- **Probability Estimation**: Temperature-adjusted softmax for championship win probabilities
- **Validation**: Compares predictions against historical top-3 averages

## 2025-2026 Season Predictions

| Rank | Team | Predicted Points | Win Probability |
|------|------|-----------------|-----------------|
| 1 | Sporting CP | 83 | 26.11% |
| 2 | Benfica | 80 | 21.82% |
| 3 | Porto | 73 | 13.94% |
| 4 | Braga | 65 | 9.12% |

*Full predictions available in the notebook*

## 🔧 Requirements

```python
pandas
numpy
scikit-learn
scipy
```

Install dependencies:
```bash
pip install pandas numpy scikit-learn scipy
```

##  Usage

1. **Clone the repository**:
```bash
git clone https://github.com/yourusername/primeira-liga-prediction.git
cd primeira-liga-prediction
```

2. **Run the notebook**:
```bash
jupyter notebook ligaportugalpred.ipynb
```

3. **Key cells to run**:
   - Data scraping cells (handles rate limiting)
   - Feature engineering pipeline
   - Model training and prediction
   - Results visualization

## Project Structure

```
├── ligaportugalpred.ipynb    # Main analysis notebook
├── primeira_all_seasons.csv  # Combined historical data (generated)
└── README.md                 # This file
```

## 🔬 Methodology

### 1. Data Collection
- Scrapes FBref for seasons 2014-2015 through 2025-2026
- Handles rate limiting with try-catch blocks
- Extracts: Rank, Squad, MP, W, D, L, GF, GA, GD, Pts, Pts/MP, Attendance

### 2. Feature Engineering
The model uses 10 key features:
- **prev_pts**: Previous season points
- **prev_gd**: Previous season goal difference
- **prev_wins**: Previous season wins
- **prev_rank**: Previous season ranking
- **last2_pts_mean**: 2-year rolling average points
- **last3_pts_mean**: 3-year rolling average points
- **pts_trend_last3**: Point trajectory (slope)
- **prev_gf_per_mp**: Goals scored per match
- **prev_ga_per_mp**: Goals conceded per match
- **prev_gd_per_mp**: Goal difference per match

### 3. Model Performance
- **Test Set MAE**: ~2.94 points
- **Feature Importance**: Multi-season averages (last2/last3_pts_mean) account for ~88% of importance
- **Validation**: Predicted top-3 mean (78.83 pts) aligns with historical average (80.18 pts)

### 4. Probability Calculation
- Uses temperature-adjusted softmax to avoid over-confident predictions
- Maximum individual win probability capped at ~35%
- Reflects the competitive nature of the "Big Three" (Benfica, Porto, Sporting)

##  Historical Insights

### The Big Three Dominance
- **Benfica**: 5 championships (2014-2025)
- **Porto**: 4 championships
- **Sporting CP**: 3 championships
- All three teams have been in the top 3 every season

### Consistent Performers
- **12/12 seasons**: Benfica, Porto, Sporting CP, Braga, Vitória
- **11/12 seasons**: Rio Ave, Boavista, Moreirense

##  Contributing

Contributions are welcome! Areas for improvement:
- Add player-level statistics
- Incorporate xG (expected goals) data
- Include head-to-head records
- Add match result predictions (not just season totals)
- Create visualization dashboards


---

**Note**: This is a predictive model for educational purposes. Actual results will vary based on countless real-world factors not captured in historical statistics.
