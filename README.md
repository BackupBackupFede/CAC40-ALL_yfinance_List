# Euronext Paris yfinance Dataset (Enriched)

Clean and ready-to-use dataset of **Euronext Paris equities**, fully compatible with `yfinance`, enriched with market data and ICB classification.

## Dataset

The file `euronext_full_enriched.csv` contains the following columns:

- `symbol`: base Euronext ticker
- `yahoo_ticker`: ticker compatible with Yahoo Finance / yfinance (e.g. `AIR.PA`)
- `isin`: unique security identifier
- `name`: company name
- `market`: listing market (e.g. Euronext Paris)
- `market_cap`: market capitalization (when available)

### ICB classification (Industry Classification Benchmark)

- `icb_industry`: high-level industry group
- `icb_supersector`: supersector classification
- `icb_sector`: sector classification
- `icb_subsector`: detailed subsector classification

## Usage

```python
import pandas as pd
import yfinance as yf

df = pd.read_csv("euronext_paris_yf_tickers_enriched.csv")

tickers = df["yahoo_ticker"].dropna().unique().tolist()

data = yf.download(tickers[:10], period="1y", interval="1d")
```

## Use cases

Stock screening (by sector, industry, market cap, etc.)
Factor research and quantitative analysis
Backtesting strategies on Euronext Paris equities
Portfolio construction & diversification studies
Financial data analysis in Python

## Methodology

Scraped official Euronext listings
Filtered French-listed equities (ISIN starting with FR)
Mapped tickers to Yahoo Finance format (.PA)
Validated tickers using yfinance price availability
Enriched dataset with:
Market capitalization
ICB classification (industry → subsector)
Company names and ISIN mapping

## Notes

Some fields (notably market_cap) may be missing or partially outdated due to Yahoo Finance limitations
All tickers are validated against live data availability in yfinance
Dataset is focused on Euronext Paris (.PA) listings only

## Requirements

Python 3.x
pandas
yfinance

```python
pip install pandas yfinance
```

## Disclaimer

This dataset is provided for informational and research purposes only.
It does not constitute financial or investment advice.