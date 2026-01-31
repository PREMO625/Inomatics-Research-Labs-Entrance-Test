# 🍔 Inomatics Research Labs - Entrance Test Hackathon

<div align="center">

![Data Analysis](https://img.shields.io/badge/Data-Analysis-blue?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.x-yellow?style=for-the-badge&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Time](https://img.shields.io/badge/Time%20Taken-1.5%20Hours-purple?style=for-the-badge)

**A comprehensive data analysis challenge focused on Food Delivery Analytics**

</div>

---

## 📋 Table of Contents

- [About The Project](#-about-the-project)
- [Problem Statement](#-problem-statement)
- [Dataset Overview](#-dataset-overview)
- [Data Pipeline](#-data-pipeline)
- [Challenge Structure](#-challenge-structure)
- [Key Analysis Areas](#-key-analysis-areas)
- [Getting Started](#-getting-started)
- [Technologies Used](#-technologies-used)

---

## 🎯 About The Project

This repository contains my solution for the **Inomatics Research Labs Entrance Test Hackathon**. The challenge simulates a real-world data engineering and analysis scenario where data comes from multiple sources in different formats, requiring integration before meaningful insights can be extracted.

> ⏱️ **Completion Time:** ~1.5 hours (from reading the Google Form → data analysis → submitting the GitHub repo link back to the form)

### Why This Matters

In the real world, data rarely comes from a single, clean source. Companies deal with:
- 📊 **Transactional databases** (CSV exports)
- 👥 **User management systems** (JSON APIs)
- 🏪 **Legacy systems** (SQL databases)

This hackathon tests the ability to **integrate heterogeneous data sources** and derive actionable business insights from them.

---

## 🧩 Problem Statement

Build a unified food delivery dataset by combining three different data sources and answer analytical questions covering:

| Category | Questions |
|----------|-----------|
| 📝 Multiple Choice Questions | 10 |
| 🔢 Numerical Questions | 6 |
| ✏️ Fill in the Blanks | 9 |

**Total: 25 Questions**

---

## 📁 Dataset Overview

### Source Files

| File | Format | Description | Key Fields |
|------|--------|-------------|------------|
| `orders.csv` | CSV | Transactional order data | `order_id`, `user_id`, `restaurant_id`, `order_date`, `amount`, etc. |
| `users.json` | JSON | User master data | `user_id`, `name`, `city`, `membership_type`, etc. |
| `restaurants.sql` | SQL | Restaurant master data | `restaurant_id`, `name`, `cuisine`, `city`, `rating`, etc. |

### Data Relationships

```
┌─────────────────┐         ┌─────────────────┐
│     USERS       │         │   RESTAURANTS   │
│   (users.json)  │         │ (restaurants.sql)│
└────────┬────────┘         └────────┬────────┘
         │                           │
         │ user_id                   │ restaurant_id
         │                           │
         └───────────┬───────────────┘
                     │
              ┌──────▼──────┐
              │   ORDERS    │
              │ (orders.csv)│
              └─────────────┘
```

---

## 🔄 Data Pipeline

### Step-by-Step Process

```python
# Step 1: Load CSV Data (Transactional Orders)
orders_df = pd.read_csv('orders.csv')

# Step 2: Load JSON Data (User Information)
users_df = pd.read_json('users.json')

# Step 3: Load SQL Data (Restaurant Information)
# Parse SQL file and load restaurant data

# Step 4: Merge the Data (LEFT JOIN)
merged_df = orders_df.merge(users_df, on='user_id', how='left')
final_df = merged_df.merge(restaurants_df, on='restaurant_id', how='left')

# Step 5: Export Final Dataset
final_df.to_csv('final_food_delivery_dataset.csv', index=False)
```

### Join Strategy

| Join | Left Table | Right Table | Key | Type |
|------|------------|-------------|-----|------|
| 1st | `orders` | `users` | `user_id` | LEFT |
| 2nd | `result` | `restaurants` | `restaurant_id` | LEFT |

> 💡 **Why Left Join?** We want to retain ALL orders, even if some user or restaurant data might be missing.

---

## 🏆 Challenge Structure

### 📝 MCQ Questions (10)
Multiple choice questions testing conceptual understanding of data patterns and relationships.

### 🔢 Numerical Questions (6)
Quantitative analysis requiring precise calculations on the dataset.

### ✏️ Fill in the Blanks (9)
Questions requiring specific values or insights extracted from data analysis.

---

## 🔍 Key Analysis Areas

Students must analyze and understand:

| Analysis Area | Description |
|---------------|-------------|
| 📈 **Order Trends** | Temporal patterns in ordering behavior |
| 👤 **User Behavior** | Customer ordering patterns and preferences |
| 🏙️ **City Performance** | Geographic distribution of orders and revenue |
| 🍕 **Cuisine Analysis** | Popular cuisines and their performance metrics |
| ⭐ **Membership Impact** | Gold vs Regular member comparison |
| 💰 **Revenue Distribution** | Financial metrics and seasonal patterns |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.x
- Jupyter Notebook
- Required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`

### Installation

```bash
# Clone the repository
git clone <repository-url>

# Navigate to project directory
cd "Inomatics Research Labs Entrance Test"

# Install dependencies
pip install pandas numpy matplotlib seaborn

# Launch Jupyter Notebook
jupyter notebook
```

### Running the Analysis

1. Open `IRL_Entrance_Test (1).ipynb`
2. Run all cells sequentially
3. The final dataset will be generated as `final_food_delivery_dataset.csv`

---

## 🛠️ Technologies Used

<div align="center">

| Tool | Purpose |
|------|---------|
| ![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) | Core programming language |
| ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white) | Data manipulation & analysis |
| ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white) | Numerical computations |
| ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white) | Interactive development |
| ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat) | Data visualization |

</div>

---

## 📊 Output

The final deliverable is:

```
📁 final_food_delivery_dataset.csv
```

This unified dataset serves as the **single source of truth** for answering all hackathon questions.

---

## 📜 License

This project is part of an educational assessment for Inomatics Research Labs.

---

<div align="center">



*Happy Analyzing! 🚀*

</div>
