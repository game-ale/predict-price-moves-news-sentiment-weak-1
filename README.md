# Week 1 – Task 1: Financial News Exploratory Data Analysis (EDA)
**Predicting Price Moves with News Sentiment**  
Nova Financial Insights Challenge | November 2025  

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.2-green)
![spaCy](https://img.shields.io/badge/spaCy-3.7-orange)
![GitHub Actions](https://img.shields.io/github/actions/workflow/status/game-ale/predict-price-moves-news-sentiment-weak-1/unittests.yml?branch=main&label=CI)

---

### Project Overview
Complete **Task 1** deliverables for Week 1 of the Nova Financial Challenge.  
Analysis performed on the **FNSPID dataset** – **1.4 million** financial news headlines (2011–2020).

**Goal**: Data quality assessment, publication patterns, publisher behavior, and textual insights to prepare for sentiment–price correlation.

---

### Repository Structure
```bash
├── .github/workflows/unittests.yml           # CI/CD pipeline
├── .vscode/settings.json                     # VS Code settings
├── src/
│   └── datas/raw_analyst_ratings.csv         # Raw data (gitignored)
├── notebooks/
│   ├── eda.ipynb                             # Full interactive EDA
│   ├── README.md
│   └── reports/                              # All visualizations saved here
│       ├── articles_per_day.png
│       ├── articles_per_publisher.png
│       ├── wordcloud_headlines.png
│       ├── domains_per_publisher.png
│       ├── headline_length_dist.png
│       └── articles_per_hour.png
├── requirements.txt
├── .gitignore
└── README.md                                 # ← you are here

Key Findings

AnalysisInsightDataset Size1,407,328 rows → ~883k unique articles after URL deduplicationDuplicate Content523,899 duplicate URLs → heavy syndicationTop PublishersPaul Quintaro (228k), Lisa Levin (187k), Benzinga Newsdesk (150k) → top 3 = ~40% of dataPublication Peak Hours9 AM – 12 PM ET – critical pre-market & market-open windowHeadline LengthMedian 64 chars • Mean 73 • 95% < 140 → extremely conciseDominant Topics (LDA)Earnings • M&A • Regulatory • Analyst Upgrades/Downgrades • Product LaunchesPublisher Domainsbenzinga.com dominates • many analysts use gmail.com / aol.comMajor Volume SpikeMarch 24, 2020 – highest single-day volume (COVID crash + Fed intervention)

Visualizations (notebooks/reports/)

articles_per_day.png → full timeline + clear event spikes
articles_per_publisher.png → extreme concentration among top contributors
wordcloud_headlines.png → dominant terms: “Shares”, “Earnings”, “Price Target”, “Up”
domains_per_publisher.png → institutional vs individual sources
headline_length_dist.png → near-normal distribution
articles_per_hour.png → strong morning bias (US market hours)


Technical Highlights & Proactivity

Custom TextNewsAnalyzer class with RAKE + spaCy + TF-IDF + LDA pipeline
Built-in regex-based financial event detection (FDA approval, M&A, IPO, dividend, etc.)
Full timezone handling (UTC → America/New_York)
Efficient 20k-row sampling for heavy NLP while preserving statistical validity
All plots automatically saved with descriptive names
GitHub Actions CI/CD ready (unittests.yml)
Fully reproducible environment

Self-Learning References

LDA & Topic Modeling – scikit-learn documentation
RAKE keyword extraction research paper
TextBlob & VADER sentiment comparison (Towards Data Science)
Investopedia – Stock Market & Stock Analysis (challenge references)


Next Steps

Task 2 → Merge with stock prices (yfinance) + technical indicators (TA-Lib)
Task 3 → Sentiment scoring → daily return correlation

Branch task-2 already created.

Author: Gemechu Alemu
Date: 22 November 2025
Status: Task 1 completed – task-1 merged to main via PR
Repository: https://github.com/game-ale/predict-price-moves-news-sentiment-weak-1
"Turning headlines into actionable alpha."
