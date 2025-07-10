# Netflix Shows Analysis

![Netflix Logo](https://upload.wikimedia.org/wikipedia/commons/0/08/Netflix_2015_logo.svg)

Analyzing the global catalog of Netflix movies and TV shows. Explore content availability, trends over time, and network relationships among cast and crew.

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Dataset](#dataset)  
3. [Data Preparation & Modeling](#data-preparation--modeling)  
4. [Dashboard Pages](#dashboard-pages)  
   - [Overview](#1-overview)  
   - [Detailed](#2-detailed)  
5. [Key Insights](#key-insights)  
6. [Interactive Dashboard](#interactive-dashboard)

---

## Project Overview

Netflix is one of the world’s leading streaming platforms, offering over 8,800 titles (movies and TV shows) to more than 200 million subscribers globally (mid‑2021). This Power BI project provides an interactive analysis of Netflix’s catalog, highlighting content distribution by country, genre, rating, duration, and release trends, as well as network analyses of directors and actors.

---

## Dataset

- **Source**: [Kaggle – Netflix Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows)  
- **Records**: ~8,801 shows (6,128 movies, 2,675 TV shows)  
- **Fields include**:
  - `show_id`, `type` (Movie/TV Show)  
  - `title`, `release_year`, `date_added`  
  - `rating`, `duration`  
  - Text fields: `description`, `cast`, `director`, `listed_in` (genres)  
  - `country`  

---

## Data Preparation & Modeling

1. **Import & Clean**  
   - Loaded CSV via Power Query  
   - Verified data types, removed duplicates, handled nulls  
2. **Semantic Model**
   <img width="917" height="404" alt="Screenshot 2025-07-08 172342" src="https://github.com/user-attachments/assets/5911e603-2ae4-4ee4-a31b-2c4ad9e30c14" />

   - Star schema with fact table `netflix_titles` and dimension tables:
     - **Cast** (`show_id`, `cast`)  
     - **Director** (`show_id`, `director`)  
     - **Country** (`show_id`, `country`)  
     - **Listed_in** (`show_id`, `listed_in`)  
   - Disabled auto‑summarization on all columns  
   - Defined custom measures (avoided calculated columns to keep the model lightweight)

---

## Dashboard Pages

### 1. Overview
![Screenshot 2025-07-08 173349](https://github.com/user-attachments/assets/df6e4b30-9f85-4d30-a2c4-dfb7b7422903)

Filters (slicers):
- Country  
- Rating  
- Genre  
- Type (Movie / TV Show)  

**Cards**  
| Metric            | Value  |
|-------------------|-------:|
| Total Shows       | 8,801  |
| # Movies          | 6,128  |
| # TV Shows        | 2,675  |
| # Countries       | 122    |

**Visuals**  
- **Top 5 Common Ratings** (Bar)  
  - “Mature Audience Only” leads with 3,207 titles.  
- **Top 5 Genres** (Bar)  
  - “International Movies” tops at 2,752 titles.  
- **Shows by Type** (Donut)  
  - Movies: 69.6%, TV Shows: 30.4%  
- **Shows by Year** (Area Chart)  
  - Peak in 2019 (2,016 titles)  
- **Top 10 Countries by # Shows** (Treemap)  
  - United States leads with 3,689 shows.

### 2. Detailed
![Screenshot 2025-07-08 173522](https://github.com/user-attachments/assets/f299ed77-7334-45d1-a1a2-c11471cf1faa)

Filters:
- Release Year (slider: 1925–2021)  
- Actor  
- Director  

**Cards**  
| Metric           | Value           |
|------------------|----------------:|
| # Actors         | 36,000          |
| # Directors      | 4,989           |
| Most Common Rating  | Mature Audience Only |
| Most Common Country | United States    |

**Visuals**  
- **Top 10 Directors by # Shows** (Bar)  
  - Rajiv Chilaka leads with 22 shows.  
- **Top 10 Actors by # Shows** (Bar)  
  - Anupam Kher leads with 43 shows.  
- **Movies by Duration** (Column)  
  - “90 min” is most common (152 movies).  
- **TV Shows by Season Count** (Column)  
  - “1 Season” most common (1,793 shows); only 7 shows have 10 seasons.  
- **Shows by Release Decade** (Column)  
  - 2010s dominate (5,927 releases).

---

## Key Insights

- **Ratings**: “Mature Audience Only” is the single most common rating.  
- **Genres**: International content (movies & TV) dominates the catalogue.  
- **Content Type Trend**: Movie releases outnumber TV shows overall, but TV‑show growth has accelerated in recent years.  
- **Geography**: The United States accounts for over 40% of all titles.  

---

## Interactive Dashboard

Explore the live report on Power BI service:  
🔗 [View on Power BI](https://app.powerbi.com/view?r=eyJrIjoiODIwOTcyODAtNTY0NS00ZWM5LTgyMzYtMjA3NjMyM2E3OWJlIiwidCI6IjhmY2Y0Y2Q5LTJmZTQtNDU3MS04NDMxLWIxN2MzZjI5ZWZiMyJ9&pageName=d753bf8729c9ca0a9c01)

