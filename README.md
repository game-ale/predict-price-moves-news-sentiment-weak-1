📈 ***Predicting Price Moves with News Sentiment***

***Nova Financial Insights Challenge – Week 1–3 Full Project***

***🔍 Project Overview***

This repository contains all three tasks of the Nova Financial Insights Challenge:

Task 1 – Exploratory Data Analysis (EDA)

Analyze 1.4M financial news headlines (2011–2020) to understand publisher behavior, news timing, headline text patterns, and dataset quality.

Task 2 – Quantitative Stock Analysis

Load historical stock prices, compute technical indicators with TA-Lib, financial metrics with PyNance, and visualize price behavior.

Task 3 – News–Price Correlation

Combine news sentiment with stock daily returns to measure correlation between news tone and market movement.


🧪 Task 1 — Financial News Exploratory Data Analysis (EDA)
📌 Dataset Summary

FNSPID Dataset — 1,407,328 financial news headlines (2011–2020)
After cleaning: ~883k unique articles

📊 Key Findings
| Analysis                   | Insight                                                        |
| -------------------------- | -------------------------------------------------------------- |
| **Dataset Size**           | 1.4M rows → 883k unique after URL deduplication                |
| **Duplicate Content**      | 523,899 repeated URLs → heavy news syndication                 |
| **Top Publishers**         | Paul Quintaro, Lisa Levin, Benzinga Newsdesk → 40% of all data |
| **Peak Publication Hours** | **9 AM – 12 PM ET** (pre-market → market open)                 |
| **Headline Length**        | Median 64 chars, Mean 73, 95% < 140 → concise                  |
| **Dominant Topics (LDA)**  | Earnings, M&A, Analyst Ratings, FDA/Regulatory                 |
| **Publisher Domains**      | benzinga.com dominates; many individual analyst emails         |
| **Major Spike**            | March 24, 2020 (COVID crash + Fed intervention)                |


🖼️ Visualizations (located in notebooks/reports/)

articles_per_day.png – full timeline, event spikes

articles_per_publisher.png – publisher concentration

wordcloud_headlines.png – common financial keywords

headline_length_dist.png – length distribution

articles_per_hour.png – market-hour bias

domains_per_publisher.png – institutional vs individual sources

🔧 Technical Highlights – Task 1

Custom NewsAnalyzer class using:

RAKE

spaCy pipelines

TF-IDF

LDA topic modeling

Regex-based financial event detector (M&A, IPO, FDA approval, dividend, etc.)

timezone normalization: UTC → America/New_York

Efficient 20k-row sampling for heavy NLP tasks

Auto-saving plots with semantic filenames

CI/CD: GitHub Actions enabled

🟢 KPIs (Task 1)

✔ Proper Git branch workflow (task-1)

✔ Minimum 3 commits/day

✔ Complete EDA

✔ Repo structure correct

✔ CI workflow passing

📉 Task 2 — Stock Technical Analysis (TA-Lib & PyNance)
📥 Data Preparation

Load stock prices (Open, High, Low, Close, Volume)

Handle missing dates, holiday gaps

Compute daily OHLC aggregates if needed

📈 Technical Indicators

Examples implemented:

df['SMA_20'] = talib.SMA(df['Close'], timeperiod=20)
df['RSI'] = talib.RSI(df['Close'], timeperiod=14)
df['MACD'], df['MACD_signal'], df['MACD_hist'] = talib.MACD(df['Close'])


Additional metrics via PyNance:

Volatility

Sharpe ratio

Moving average crossovers

Trend strength scores

📊 Visualization Highlights

Price + SMA overlays

RSI oscillation behavior

MACD divergence

Volume spikes

(Figures saved inside notebooks/reports/)

🟣 Task 2 KPIs

✔ Branch created (task-2)

✔ Indicators computed correctly

✔ Visualizations included

✔ Merged Task-1 into main via PR

✔ Accurate technical analysis

📰 Task 3 — Sentiment vs Stock Movement Correlation
🧠 Sentiment Analysis Example
from textblob import TextBlob
df['sentiment'] = df['headline'].apply(lambda x: TextBlob(x).sentiment.polarity)


Positive sentiment: > 0

Neutral: = 0

Negative: < 0

📅 Date Alignment

Normalize timestamps (YYYY-MM-DD)

Map news dates → stock trading dates

Multiple headlines/day → aggregate mean sentiment

📊 Stock Returns
df['Returns'] = df['Close'].pct_change()

🔗 Correlation Analysis
df[['daily_sentiment', 'Returns']].corr(method="pearson")


Outputs:

Correlation coefficient

Direction of relationship

Strength of predictive value

🟡 Task 3 KPIs

✔ Sentiment pipeline working

✔ Daily alignment correct

✔ Pearson correlation computed

✔ Branch task-3 created

✔ Pull Request workflow followed

⚙️ CI/CD – GitHub Actions

The pipeline at:

.github/workflows/unittests.yml


Runs:

Dependency installation

Lint checks

Unit tests (pytest)

Notebook execution tests

📦 Requirements
pandas
numpy
matplotlib
seaborn
nltk
textblob
spacy
scikit-learn
wordcloud
pyyaml
talib
pynance
jupyter
yfinance


🧠 Self-Learning References

scikit-learn: LDA topic modeling

RAKE keyword extraction (original paper)

TextBlob & VADER sentiment analysis

Investopedia market structure

TA-Lib indicator math

📌 Next Steps

Integrate sentiment pipeline with multi-stock universe

Build a daily sentiment index

Perform Granger Causality tests

Build a prediction baseline model

👤 Author

Gemechu Alemu
November 2025
“Turning headlines into actionable alpha.”

GitHub: https://github.com/game-ale/predict-price-moves-news-sentiment-weak-1