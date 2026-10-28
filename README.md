# Ramen Rating Analysis — Machine Learning & Data Exploration

This project analyzes global instant ramen quality using the **Ramen Ratings Dataset**, combining data cleaning, exploratory visualization, flavor keyword extraction, and machine learning models to uncover meaningful patterns in ramen ratings across countries, brands, styles, and flavor profiles.

The notebook is structured as a polished report with hidden code cells, clear section headers, and visual storytelling throughout.

---

## Project Structure

1. Importing Libraries  
2. Data Cleaning & Preprocessing  
3. Exploratory Visualizations  
4. Modeling Dataset Preparation  
5. Regression Modeling  
6. Clustering Analysis  
7. Final Conclusion  

---

## Dataset Overview

The dataset includes:

- 2,500+ ramen products  
- 35 countries (38 names in the raw data, with 3 duplicates merged)  
- Multiple packaging styles (Pack, Cup, Bowl, Tray, Other)  
- Flavor descriptions (Variety column)  
- Official Top Ten selections  
- Star ratings from 0–5  

---

## 🧹 Data Cleaning & Preprocessing

Key steps:

- Converted star ratings to numeric values and dropped the 3 "Unrated" products (0-star ratings are kept as real reviews)  
- Created `is_top_ten` indicator from real placements only (4 rows held an empty line break, not a placement)  
- Merged duplicate names: "United States" → USA, "Holland" → Netherlands, "Sarawak" → Malaysia, "MAMA" → Mama  
- Created flavor keyword flags (spicy, seafood, chicken, beef, pork, miso, curry) from the Variety description  
- Normalized packaging styles  
- Removed extremely rare style categories  
- Filtered countries with **≥ 50 products** to avoid small-sample distortion  
- Prepared cleaned datasets for visualization and modeling  

Filtering reduced the dataset from **35 countries to 12**, improving reliability of country-level comparisons.

---

## Exploratory Visualizations

The notebook includes:

- Average ratings by country (≥ 50 products)  
- Top Ten winners by country  
- Top Ten winners by brand  
- Global ramen style distribution  
- Flavor keyword word cloud  

These visualizations reveal strong regional patterns. **Malaysia, Singapore, Indonesia and Japan** have the highest average ratings, and Singapore, Malaysia, Japan, South Korea and Indonesia lead the 37 Top Ten placements. **Prima Taste** has the most Top Ten appearances (5), followed by **Mama** (4). Region alone isn't enough, though: Thailand and Vietnam rank near the bottom on average.

---

## Regression Modeling

A **Random Forest Regression** model was trained to predict ramen ratings using:

- Flavor keyword flags  
- Country of origin  
- Packaging style  

**Top Ten status is deliberately left out.** Winners are chosen because they are rated highly (all 37 are rated 4–5 stars), so using it as a predictor would leak the answer into the model.

### Model Performance

- **MSE:** 0.9760  
- **RMSE:** 0.9879  
- **MAE:** 0.7261 (vs. 0.7320 for always predicting the average)  
- **R²:** 0.0173  

The model is only slightly better than guessing the average rating and explains under **2%** of the variance. Country, flavor and style shape *average* ratings, but they can't predict an individual product's rating, which is expected given how subjective food ratings are.

### Key Predictors

- **Country indicators**, led by Canada (lowest average rating at 2.24 stars), then Japan, Malaysia, Singapore, Indonesia, UK and Vietnam  
- **Flavor keywords**: curry / tom yum varieties rate about **+0.4 stars** above the rest, while chicken varieties rate about **0.3 stars lower**. Spicy, seafood and miso make almost no difference.  
- **Packaging styles** (Pack, Cup, Bowl), with smaller influence

---

## Clustering Analysis

A **K-Means** model was applied using:

- Flavor flags  
- Country encodings  
- Packaging style encodings  
- Star ratings  

### Silhouette Score: **0.032**

This extremely low score indicates **no meaningful cluster separation**.  
Ramen products overlap heavily across countries, styles, and flavors, so there are no distinct product groupings in this data.

---

## Final Conclusion

Across all analyses, a consistent narrative emerges:

- **Country of origin** shows the clearest differences in average ratings  
- **Flavor** matters for a few keywords: curry / tom yum rates higher, chicken lower  
- **Packaging style** has a smaller influence  
- **Individual ratings are hard to predict**: the model barely beats guessing the average  
- **Clustering models fail** due to high overlap across features  
- **Malaysia, Singapore, Indonesia and Japan** lead in average ratings, and Southeast and East Asian brands dominate the Top Ten  
- A natural next step is adding **brand** as a model feature  

This project demonstrates how data cleaning, visualization, and machine learning can reveal patterns in a subjective domain like food ratings — while also highlighting the limits of prediction when human taste is involved.

---

## Technologies Used

- Python  
- Pandas  
- NumPy  
- Seaborn / Matplotlib  
- Scikit‑learn  
- WordCloud  
- Jupyter Notebook  

---

## License

This project is for educational use.

## Dataset Source

This project uses the **Ramen Ratings Dataset** published on Kaggle:

**Ramen Ratings Dataset**  
https://www.kaggle.com/datasets/residentmario/ramen-ratings  
Created by: *residentmario*  
License: Open dataset provided for public analysis and educational use.

The dataset contains over 2,500 ramen reviews, including:
- Country of origin  
- Brand  
- Packaging style  
- Flavor variety  
- Star rating  
- Official Top Ten selections  

All analysis, visualizations, and models in this project are based on this dataset.
