# Customer Segmentation Project

## Project Overview
This project performs **customer segmentation** on an e-commerce dataset containing purchase records of approximately 4,000 customers over one year. The goal is to analyze customer behavior, group similar customers, and provide actionable insights for marketing, retention, and sales optimization.

By clustering customers based on their purchasing patterns, basket size, and product categories, businesses can identify high-value customers, frequent buyers, and one-time customers, and target them with personalized strategies.

---

## Dataset

- **Source:** E-commerce dataset (2010–2011)  
- **Size:** ~400,000 entries  

**Key Features:**
- `InvoiceNo` – Unique invoice number
- `StockCode` – Product identifier
- `Description` – Product description
- `Quantity` – Number of items per transaction
- `InvoiceDate` – Date and time of transaction
- `UnitPrice` – Price per product unit
- `CustomerID` – Unique customer identifier
- `Country` – Country of the customer

**Data Cleaning:**
- Removed rows with missing `CustomerID`
- Dropped duplicates
- Handled canceled orders
- Processed special stock codes (e.g., discounts, postage)
- Created `TotalPrice` and per-category spending variables

---

## Methodology

### 1. Product Clustering
- Extracted keywords from the `Description` column using **NLTK** for text processing
- Filtered out irrelevant words (colors, tags, symbols) and rare keywords
- One-hot encoding of keywords to create a binary feature matrix for products
- Added price range features to the product matrix
- Applied **KMeans clustering** to group products into 5 clusters
- Visualized clusters using:
  - Word clouds for keyword distribution
  - Principal Component Analysis (PCA) for dimensionality reduction

### 2. Customer Segmentation
- Aggregated each customer’s purchase behavior:
  - Number of purchases, min/max/average basket size
  - Category-wise spending distribution
  - Days since first and last purchase
- Standardized numerical features using **StandardScaler**
- Applied **KMeans clustering** to segment customers into 11 clusters
- Validated clustering using **silhouette scores** and PCA visualization

### 3. Insights
- Identified **high-value customers** with frequent and large purchases
- Highlighted **one-time customers** (~40% of all customers) as potential targets for retention campaigns
- Discovered **customer preferences** for product categories via clustering

---

## Key Results
- **Product Clusters:** 5 clusters representing gift items, luxury products, home décor, everyday items, and miscellaneous
- **Customer Clusters:** 11 clusters based on spending, frequency, and category preferences
- **Silhouette Scores:** 
  - Products: ~0.15  
  - Customers: 0.477
- PCA visualizations confirm distinct clustering patterns

---

## Technologies & Libraries
- **Python 3**  
- **Data Manipulation:** `pandas`, `numpy`  
- **Visualization:** `matplotlib`, `seaborn`, `plotly`  
- **Machine Learning:** `scikit-learn` (`KMeans`, `PCA`, classifiers)  
- **Text Processing:** `nltk`  
- **Word Clouds:** `wordcloud`  

---

## How to Run

1. Clone the repository:
```bash
git clone https://github.com/yourusername/customer-segmentation.git
cd customer-segmentation
