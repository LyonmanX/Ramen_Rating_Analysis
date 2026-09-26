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
- 38 countries  
- Multiple packaging styles (Pack, Cup, Bowl, Tray, Other)  
- Flavor descriptions (Variety column)  
- Official Top Ten selections  
- Star ratings from 0–5  

---

## 🧹 Data Cleaning & Preprocessing

Key steps:

- Converted star ratings to numeric values  
- Created `is_top_ten` indicator  
- Normalized packaging styles  
- Removed extremely rare style categories  
- Filtered countries with **≥ 50 products** to avoid small-sample distortion  
- Prepared cleaned datasets for visualization and modeling  

Filtering reduced the dataset from **38 countries to 12**, improving reliability of country-level comparisons.

---

## Exploratory Visualizations

The notebook includes:

- Average ratings by country (≥ 50 products)  
- Top Ten winners by country  
- Top Ten winners by brand  
- Global ramen style distribution  
- Flavor keyword word cloud  

These visualizations reveal strong regional patterns, with Southeast Asia and East Asia dominating both production volume and high-rated products.

---

## Regression Modeling

A **Random Forest Regression** model was trained to predict ramen ratings using:

- Flavor keyword flags  
- Country of origin  
- Packaging style  
- Top Ten status  

### Model Performance

- **MSE:** 0.7666  
- **RMSE:** 0.8756  
- **MAE:** 0.6448  
- **R²:** 0.1422  

The model predicts ratings within roughly **±0.9 stars**, but explains only **14%** of the variance — expected due to the subjective nature of food ratings.

### Key Predictors

- **Top Ten status**  
- **Country indicators** (Canada, UK, Netherlands, Japan, Malaysia, Vietnam, Thailand)  
- **Packaging styles** (Pack, Cup, Bowl)  

Flavor keywords contribute meaningfully but are not the strongest predictors.

---

## Clustering Analysis

A **K-Means** model was applied using:

- Flavor flags  
- Country encodings  
- Packaging style encodings  
- Star ratings  

### Silhouette Score: **0.0345**

This extremely low score indicates **no meaningful cluster separation**.  
Ramen products overlap heavily across countries, styles, and flavors, suggesting instant ramen is a globally homogeneous product category.

---

## Final Conclusion

Across all analyses, a consistent narrative emerges:

- **Country of origin** is a strong predictor of ramen quality  
- **Packaging style** contributes moderately  
- **Flavor profile** adds meaningful but secondary influence  
- **Top Ten selections** reliably identify standout products  
- **Clustering models fail** due to high overlap across features  
- **Southeast Asia and East Asia dominate** global ramen production and quality  

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
