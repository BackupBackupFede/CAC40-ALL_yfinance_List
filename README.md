# Euronext Paris yfinance Tickers (Enriched)

Clean and ready-to-use dataset of Euronext Paris equities, fully compatible with yfinance.

## Dataset

The file `euronext_paris_yf_tickers_enriched.csv` contains:

* `isin`: unique security identifier
* `symbol`: base ticker (Euronext format)
* `yahoo_ticker`: ticker compatible with yfinance (e.g. `AIR.PA`)
* `name`: company name
* `sector`: business sector
* `industry`: industry classification
* `market_cap`: market capitalization

All tickers have been validated to ensure they return actual price data via yfinance.

## Usage

```python
import pandas as pd
import yfinance as yf

df = pd.read_csv("euronext_paris_yf_tickers_enriched.csv")

tickers = df["yahoo_ticker"].tolist()

data = yf.download(tickers[:10])
```

## Use cases

* Stock screening (by sector, market cap, etc.)
* Backtesting strategies on Euronext Paris equities
* Portfolio construction
* Financial data analysis in Python

## Methodology

1. Scraped Euronext official website for listed equities
2. Filtered French listings (ISIN starting with "FR")
3. Validated tickers using yfinance price data
4. Enriched dataset with sector, industry, and market capitalization
5. Merged with ISIN and company names

## Notes

* Some fields may be missing due to Yahoo Finance data limitations
* Market data is sourced from yfinance
* Dataset is limited to Euronext Paris tickers (`.PA`)

## Requirements

* Python 3.x
* pandas
* yfinance

## Disclaimer

This project is for informational purposes only and does not constitute investment advice.
