# Flickchart-Movie-Dataset-Scraper
Scrape and enrich 10k+ Flickchart movies with IMDb, Wikipedia, and TMDb data in R

# Flickchart Movie Scraper

Scrape and enrich **10k+ movies from Flickchart** with additional data from **IMDb (OMDb API)**, **Wikipedia**, and **TMDb API** — all in **R**.  
The pipeline produces a rich dataset including titles, year, director, cast, genre, duration, ratings, budgets, revenues, and calculated profits.

---

## Features
- Scrapes:
  - **Title, Year, Duration, Genre, Director, Cast** from Flickchart
- Fetches:
  - **IMDb Ratings** (via OMDb API, with fallbacks)
  - **Budget & Box Office** (via Wikipedia infobox parsing)
  - **Budget & Revenue** (via TMDb API)
- Cleans financial data into **USD** and computes **profit percentage**

---

## Output Datasets
- `data/flickchart_titles_all_pages.csv` – raw scraped titles + metadata
- `data/flickchart_full_dataset.csv` – cleaned Flickchart-only dataset
- `data/enriched_movies.csv` – fully enriched dataset with external APIs

**Columns in final dataset:**
- `title`, `year`, `director`, `duration`, `cast`, `genre`
- `imdb_rating`
- `budget`, `box_office` (raw Wikipedia strings)
- `tmdb_budget`, `tmdb_revenue` (numeric from TMDb)
- `budget_usd`, `revenue_usd` (cleaned USD values, best source chosen)
- `profit_percent` = `(revenue_usd - budget_usd) / budget_usd * 100`

---

## 🛠 Requirements

Install required R packages:
```r
install.packages(c(
  "rvest", "dplyr", "readr", "stringr", "purrr",
  "tidyr", "httr", "jsonlite"
))

