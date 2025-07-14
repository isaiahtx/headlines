# Headlines

The goal of this project is to employ different machine learning, statistical learning, or NLP methods and algorithms to use financial news headlines to predict abnormal short-term stock returns.

Specifically, given a news article, the goal

This project gets its data from the [Alpaca Markets API](https://docs.alpaca.markets/), which is free to use. In order to download said data, I am employing a small wrapper I have made called [Alpaca-API](https://github.com/isaiahtx/alpaca-api)

# Problem specification

We are given a text news headline at a specific timestamp, along with a list of stock tickers that are relevant to said headline. Our goal will be to predict abnormal return, which has the following formula:

# Project Structure:

## `1. Setup.ipynb`

This notebook downloads the news data and bar data from Alpaca. Unfortunately, our news data has an issue: 

Each news article entry is tagged with two timestamps: `created_at`, and `updated_at`. The `created_at` timestamp indicates when that article was first published, while the `updated_at` timestamp indicates when that article was last updated. Alpaca only shows the most recently-updated headline — not the original headline.

Thus, we have a potential issue with lookahead bias

1. Download all news articles from 2020 to present. Each article comes with:
- A headline
- A `created_at` timestamp, indicating when the article was first published
- A `updated_at` timestamp, indicating when the article was last updated
- A list of symbols/tickers that are associated to that article (e.g., `BTC`, `SPY`, etc.)
2. Get the 100 most commonly mentioned stock tickers across all the articles and download all available 1 minute O/H/L/C/N/V/VW bar data for those stocks from 2020 through present
3. Store the bar data as `.parquet` files
4. Filter the articles as follows:
- Keep only those articles which mention of the aforementioned 100 most common symbols
-
