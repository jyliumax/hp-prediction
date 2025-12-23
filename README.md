# Housing Price Prediction and Link Analysis

This repository contains the solution for the **Model Prediction** and **Link Analysis** tasks for housing price analysis.

---

## Environment

- **Python**: 3.11.9
- Tested on Windows / macOS with Jupyter Notebook

---

## Repository Structure

├── HTX_EDA_and_Modeling.ipynb # Data exploration, feature engineering, and price prediction models
├── HTX_Linkanalysis.ipynb # Graph construction and link analysis
├── data/ # Supporting datasets (see below)
├── requirements.txt # Python dependencies
├── hdb_analysis_slides.pdf # Presentation slides for interview discussion
└── README.md


### `data/` folder contents
The `data` folder contains supporting datasets used for feature engineering:
- `rpi.csv` – HDB Resale Price Index (for price adjustment)
- `primary_school_df.csv` – Singapore primary school locations
- `mrt_df.csv` / `mrt.csv` – MRT station information and opening year
- `geo_df1.csv` – HDB block geolocation data

> **Note:** Raw HDB resale transaction data is **not included** and should be provided by the user.

---

## Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/jyliumax/housing-price-prediction.git
cd housing-price-prediction
```

Create a virtual environment
```bash
python -m venv venv
```

Activate the environment:

Windows
```bash
venv\Scripts\activate
```

macOS / Linux
```bash
source venv/bin/activate
```

Install dependencies
```bash
pip install -r requirements.txt
```

OneMap API Access (Required)

This project uses OneMap API for geocoding and distance-based feature engineering.

Obtain OneMap access token

Register for a OneMap account
https://www.onemap.gov.sg/

In HTX_EDA_and_Modeling.ipynb, obtain an access token:

```bash
import requests

url = "https://www.onemap.gov.sg/api/auth/post/getToken"

payload = {
    "email": "YOUR_EMAIL",
    "password": "YOUR_PASSWORD"
}

response = requests.post(url, json=payload)
print(response.text)

# Extract access_token from response
access_token = "YOUR_ACCESS_TOKEN"

```

Paste the access_token into the notebook where indicated.

! Do not commit API credentials or tokens to GitHub.

Launch Jupyter Notebook
jupyter notebook


2. Prepare data

Place the HDB resale transaction dataset under the data/ folder.

Ensure file paths in the notebooks match your local directory.

3. Run notebooks (in order)

HTX_EDA_and_Modeling.ipynb

Data exploration

Feature engineering

Ridge Regression (baseline)

XGBoost Regression (advanced model)

Model evaluation and findings

HTX_Linkanalysis.ipynb

Graph construction based on listing similarity

Connected components analysis

Degree centrality 

Interpretation of graph-based insights

Outputs

Model evaluation metrics (MAE, RMSE, R²)

Feature importance and visualizations

Graph statistics and network visualizations

Slides summarizing assumptions, methodology, results

Notes

This repository focuses on modeling logic, analysis, and interpretation.

Large raw datasets and trained model artifacts are intentionally excluded.

All results are reproducible using the provided notebooks and instructions.