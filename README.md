# Tesla Stock Data Analysis
> Multi-source data pipeline combining yfinance API extraction and Selenium-powered web scraping to visualize Tesla's historical share price and quarterly revenue using Plotly.

---

## Overview

This project fetches and combines two distinct data sources for Tesla (TSLA), live stock price history via the `yfinance` API and quarterly revenue figures scraped from Macrotrends, then visualizes them together in an interactive dual-panel Plotly chart.

**Key capabilities:**
- Full TSLA stock history pulled via `yfinance` in a single API call
- Dynamic JavaScript-rendered revenue table scraped using Selenium + BeautifulSoup
- Data cleaning pipeline to normalize raw scraped revenue strings
- Interactive dual-subplot Plotly chart with a shared range slider

---

## Tech Stack

| Category | Tool / Library |
|----------|----------------|
| Language | Python 3.x |
| Stock data API | yfinance |
| Web scraping | Selenium, BeautifulSoup4, Requests |
| Data processing | pandas |
| Visualization | Plotly |
| Notebook environment | Jupyter Notebook |

---

## Data Sources

| Data | Source | Method |
|------|--------|--------|
| Historical closing price | Yahoo Finance (via `yfinance`) | API |
| Quarterly revenue (USD millions) | [Macrotrends](https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue) | Selenium scrape |

> **NOTE:** `requests` + BeautifulSoup alone cannot retrieve the revenue table because it is dynamically rendered via JavaScript. To tackle that, Selenium library is used to fully load the page before parsing further.

---

## Pipeline

```
yfinance API ──────────────────────────────► tesla_data (DataFrame)
                                                      │
Selenium → full page HTML                             │
  └─► BeautifulSoup parse                             │
        └─► extract quarterly table                   │
              └─► clean (strip $, commas, NaNs)       │
                    └─► tesla_revenue (DataFrame)     │
                                                      │
                              make_graph(tesla_data, tesla_revenue)
                                                      │
                                              Plotly dual-subplot chart
```
