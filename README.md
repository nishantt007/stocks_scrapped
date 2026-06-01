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
| Quarterly revenue (USD millions) | Macrotrends | Selenium scrape |
