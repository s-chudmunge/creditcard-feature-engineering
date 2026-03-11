# COVID-19 Global Data Analysis

**Author:** Sankalp Chudmunge  
**Module:** Python Data Science — Module 1: EDA & Visualizations

## Dataset

[Our World in Data — COVID-19 Dataset](https://ourworldindata.org/covid-deaths)  
Source CSV: `https://raw.githubusercontent.com/owid/covid-19-data/master/public/data/owid-covid-data.csv`

Covers 200+ countries from January 2020 to present. Updated daily. Includes case counts, deaths, vaccinations, and population-normalized metrics.

## What This Notebook Does

1. **Data Loading** — Pulls the live OWID CSV directly into pandas
2. **Data Cleaning** — Filters out aggregate regions (non-countries), handles missing values, selects key columns
3. **Descriptive Statistics** — Global totals, top 10 countries by cases, continent-level breakdown with case fatality rates
4. **Visualizations:**
   - Global daily new cases with 7-day rolling average (wave structure)
   - Total cases per million by continent (box plot showing geographic disparity)
   - Case fatality rate vs vaccination rate scatter plot with trend line

## Key Findings

- The Omicron wave (early 2022) produced the highest case counts globally, but deaths did not scale proportionally
- Europe and South America had the highest cases per million; Africa's lower numbers reflect both real demographic differences and likely underreporting
- Higher vaccination rates correlate with lower case fatality rates, though healthcare system quality is a confounding factor

## How to Run

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook module1_covid_eda.ipynb
```
