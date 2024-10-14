# Predictive Crime Intelligence for Buffalo

Buffalo Crime Dynamics is a machine learning project focused on predicting high-crime areas in Buffalo, NY. The system uses various machine learning models and real-time data scraping techniques to predict the crime level in a specific area based on historical data. It also provides crime-related insights and visualizations through a Streamlit-based dashboard.

## Project Overview

This project aims to:
- Predict high-crime areas in Buffalo, NY using machine learning models like Random Forest, Gradient Boosting, Logistic Regression, and more.
- Provide insights into crime patterns using visualizations through a Streamlit dashboard.
- Display crime-related statistics, such as occurrences by district, crime type, and hour of the day.

## Features

- **Real-time Crime Prediction**: The system predicts whether an area will experience a high or low level of crime based on user-input data (date, time, zip code, etc.).
- **Visualizations**: Includes visual insights like crime type distribution, crime occurrences by district, and crime density by hour of the day.
- **Interactive Dashboard**: The dashboard allows users to enter custom data and visualize crime trends through various graphs and plots.
- **Scraping & Data Processing**: The project uses data scraping techniques to pull real-time crime data from public data portals, including data from Buffalo's open data portal.
  
## Technology Stack

- **Machine Learning**: Random Forest, Gradient Boosting, Logistic Regression, SVM, KNN, Decision Tree, Naive Bayes.
- **Programming Languages**: Python
- **Libraries & Tools**:
  - `pandas`, `numpy` - Data handling and preprocessing
  - `scikit-learn` - Machine learning models and metrics
  - `matplotlib`, `seaborn` - Data visualization
  - `joblib` - Model saving and loading
  - `streamlit` - Frontend dashboard for user interaction
  - `sodapy` - Socrata API client for scraping real-time crime data from Buffalo's data portal
  - `sqlite3` - For database interaction
- **Frontend**: Streamlit for an interactive dashboard

## Dataset

- The dataset is obtained via real-time scraping from [Buffalo's open data portal](https://data.buffalony.gov/).
- Features include:
  - `incident_datetime`: The date and time when the crime occurred.
  - `incident_type_primary`: The primary type of crime.
  - `zip_code`: The ZIP code where the incident occurred.
  - `latitude`, `longitude`: The geographical coordinates of the crime scene.
  - `police_district`: The police district that responded to the incident.
  - `council_district`: The council district in which the crime occurred.

## Special Tasks Performed

1. **Data Scraping**:
   - Real-time crime data is scraped using `sodapy` from Buffalo's open data portal, ensuring that the data is up-to-date for crime prediction.

2. **Data Cleaning**:
   - Duplicate entries and non-essential features are dropped to reduce noise in the dataset.
   - Date and time fields are normalized, and additional columns like `Year`, `Month`, `Day`, and `Hour` are created for better feature extraction.

3. **Outlier Removal**:
   - Outliers are identified and removed using Interquartile Range (IQR) to improve the model’s accuracy.

4. **One-Hot Encoding & Label Encoding**:
   - Categorical features such as `police_district` and `incident_type_primary` are one-hot encoded for use in machine learning models.

5. **Model Training & Evaluation**:
   - Various machine learning models (Logistic Regression, Random Forest, Gradient Boosting, SVM, etc.) were trained and evaluated.
   - Evaluation metrics include accuracy, precision, recall, F1 score, and confusion matrix visualization.

6. **Streamlit Dashboard**:
   - A custom-built Streamlit dashboard provides an interactive UI for users to input crime details (e.g., date, time, zip code) and receive crime predictions.
   - It also visualizes crime statistics like occurrences by district, crime type distribution, and crime density by time of day.

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/YOUR_GITHUB_USERNAME/Buffalo-Crime-Dynamics.git
   cd Buffalo-Crime-Dynamics
   
2. **Install Required Dependencies**:

```bash
pip install -r requirements.txt
```

3. **Download or Scrape the Data: Use the provided scraping code to pull real-time data from Buffalo's open data portal**:
```bash
from sodapy import Socrata
client = Socrata("data.buffalony.gov", None)
results = client.get("d6g9-xbgu", limit=400000)
df = pd.DataFrame.from_records(results)
```

4.**Run the Backend**: 
Use the Python script to train machine learning models and evaluate crime predictions.

``` bash
python crime_predictor.py
```

5.**Start the Streamlit Dashboard**: 
Launch the frontend dashboard for interactive crime predictions.
```bash
streamlit run app.py
```

6. **Access the Dashboard**:
Open your browser and go to:
```bash
http://localhost:8501
```

7. **Making Predictions**:

- Input date, time, and ZIP code into the dashboard.
- Select the incident type and district to receive a crime prediction.
  
## Future Enhancements
- Enhanced Scraping: Improve scraping to include data from additional platforms like FBI crime databases, weather data to correlate crime rates, and more.
- Improved Machine Learning Models: Implement deep learning models and neural networks for improved prediction accuracy.
- User Authentication: Add login features for police departments or government officials to access sensitive crime data and insights.
