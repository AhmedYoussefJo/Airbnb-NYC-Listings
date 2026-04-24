# 🏙️ Airbnb NYC Listings — Exploratory Data Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)
![Folium](https://img.shields.io/badge/Folium-Geospatial-77B829)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Overview

Exploratory Data Analysis on **~48,000 Airbnb listings in New York City (2019)**, aiming to uncover the key factors that influence pricing and help hosts build smarter pricing strategies.

**Business Question:**
> *What factors influence Airbnb listing prices in New York City, and how can hosts optimize their pricing strategies?*

---

## 📁 Project Structure

```
airbnb-nyc-eda/
│
├── AB_NYC/
│   └── AB_NYC_2019.csv        # Dataset
│
├── arbnbHosts.ipynb            # Main analysis notebook
├── nyc_airbnb_map.html         # Interactive geospatial map
└── README.md
```

---

## 🛠️ Tools & Libraries

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, manipulation |
| `numpy` | Numerical operations & log transformation |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualizations |
| `folium` | Interactive geospatial heatmap |

---

## 🔍 Analysis Steps

### 1. 📊 Data Understanding
- Explored dataset shape, types, and distributions
- Detected right-skewed price distribution (`Mean > Median > Mode`)

### 2. 🧹 Data Cleaning
- Identified and handled missing values logically (reviews null = new listings with no bookings)
- Filled `reviews_per_month` with `0`, host names with `'unknown'`
- Converted `last_review` from `object` → `datetime`
- Engineered new feature: `has_review` (1 = reviewed, 0 = never booked)

### 3. 📉 Outlier Detection
- Used **IQR method** to detect outliers (~6% of data)
- Applied **log transformation** (`np.log1p`) to normalize price distribution

### 4. 📈 Exploratory Data Analysis
- Price distribution by room type and neighbourhood group
- Correlation heatmap across all numeric features
- Regression plot: price vs. availability

### 5. 🗺️ Geospatial Analysis
- Interactive heatmap using **Folium** showing price intensity across NYC
- Static scatter plot mapping listing locations colored by log price

---

## 💡 Key Insights

- 🏠 **Entire home/apartment** listings command the highest median price (~$160)
- 📍 **Manhattan** is the most expensive neighbourhood group (~$150 median)
- ⭐ **Reviews have almost no correlation with price** (r = 0.09) — engagement and pricing are independent
- 🗺️ High-priced listings cluster around **Manhattan and Brooklyn waterfront**
- 📊 Outliers (~6%) represent a real **luxury segment**, not data errors
- 📐 **Median** is a more reliable price metric than mean due to skewness

---

## 📌 Recommendations for Hosts

- Focus on **location and room type** when setting prices — not review count
- Hosts in premium areas should emphasize **exclusivity and amenities**
- Lower-priced listings can benefit from **review-generation campaigns** to improve visibility
- Pricing strategy should be **segmented**: budget vs. luxury listings

---

## 🚀 How to Run

1. Clone the repo
```bash
git clone https://github.com/your-username/airbnb-nyc-eda.git
cd airbnb-nyc-eda
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn folium
```

3. Add the dataset inside `AB_NYC/` folder  
   *(Dataset source: [Inside Airbnb](http://insideairbnb.com/) / Kaggle AB_NYC_2019)*

4. Run the notebook
```bash
jupyter notebook arbnbHosts.ipynb
```

---

## 📂 Dataset

**AB_NYC_2019.csv** — New York City Airbnb Open Data  
Source: [Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

Key columns: `price`, `room_type`, `neighbourhood_group`, `number_of_reviews`, `availability_365`, `latitude`, `longitude`, `last_review`

---

## 👤 Author

Made with ❤️ as a Data Analysis practice project  
Feel free to ⭐ the repo if you found it useful!
