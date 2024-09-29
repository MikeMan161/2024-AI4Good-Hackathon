# 2024-AI4Good-Hackathon
Apartment Scam Detection Project
Project Overview
----------------------
This project focuses on detecting fraudulent housing listings using machine learning algorithms, anomaly detection methods, and geospatial analysis. The dataset consists of rental property listings from Duval County, and the goal is to identify potential scams based on numerical, textual, and geospatial features.

Project Objectives
----------------------
Clean and preprocess housing listing data.
Generate additional features related to price metrics, anomaly detection, and scam keyword identification.
Apply machine learning models (Isolation Forest, Local Outlier Factor) to flag suspicious listings.
Use geospatial data to score listings based on proximity to high-risk areas.
Visualize the results through various plots and maps.

Data
----------------------
The project uses housing listing data stored in CSV format. Some of the key features include:

List Price: The listed price of the rental property.
Bedrooms Total: Number of bedrooms in the listing.
Bathrooms Total: Number of bathrooms in the listing.
Living Area: Total area in square feet.
Days on Market: How long the listing has been available.
Latitude and Longitude: Coordinates for geospatial analysis.
Additional features are created in the project through feature engineering to help improve model accuracy and provide better insights into the data.

Project Structure
---------------------
Here is a breakdown of the steps involved in the project:

1. Data Cleaning and Preprocessing
Load the raw dataset from PrimaryDataset-MLS-RentalProperties.csv.
Clean the data by dropping irrelevant columns, handling missing values, and removing duplicates.
Select key columns for analysis such as List Price, Bedrooms, Bathrooms, Living Area, Latitude, and Longitude.

2. Feature Engineering
Calculate price metrics like:
Price per Bedroom
Price per Bathroom
Price per Living Area
Price per Story
Price per Garage Space
Price adjusted for Year Built
Create a Distance Suspiciousness Score by calculating proximity to important locations such as universities, military bases, etc.
Add a flag for listings on the market for more than 30 days.

3. Anomaly Detection
Isolation Forest: A tree-based model used to detect anomalies in numerical data. Listings identified as anomalies are flagged with a -1 score.
Local Outlier Factor (LOF): A nearest-neighbors algorithm that detects outliers based on local density. Similar to Isolation Forest, anomalies are flagged with -1.
Cross-examine the results of both models to identify listings that are flagged by both.

4. Geospatial Suspicion Score
Implement the Haversine formula to calculate the distance between each listing and important locations.
Assign a suspicion score to each listing based on proximity, with listings closer to high-risk areas (e.g., universities, military bases) receiving higher scores.
Visualize these scores on an interactive Folium heatmap.

5. Dimensionality Reduction with PCA
Use Principal Component Analysis (PCA) to reduce the number of features while retaining 95% of the data variance.
Visualize feature contributions to each principal component using heatmaps.
Use scatter plots to visualize anomalies in the reduced-dimensional space.

6. Clustering with DBSCAN
Apply DBSCAN to cluster the PCA-transformed data and identify groups of similar listings.
Visualize the clustering results using a scatter plot, highlighting anomalies and clusters.

7. Keyword-Based Scam Detection
Scan the Features column for suspicious words (e.g., "urgent", "cash only", "no credit check").
Flag listings with scam-related keywords and store this information in a new column, is_suspicious.

8. Visualization
Generate scatter plots to visualize price anomalies and outliers.
Create Venn diagrams to compare results from Isolation Forest and LOF.
Visualize the proximity-based suspicion score on a heatmap using Folium.

Installation Instructions
----------------------------
Prerequisites
To run the code locally, you need the following:

Python 3.6+
Libraries: You can install the required libraries by running:
bash
Copy code
pip install -r requirements.txt
A sample requirements.txt might include:
text
Copy code
pandas
scikit-learn
matplotlib
seaborn
folium
numpy
venn

How to Run the Project
Clone the repository:
bash
Copy code
git clone https://github.com/your-username/your-repo-name.git
Navigate to the project directory:
bash
Copy code
cd your-repo-name

Run the Jupyter notebook or Python script:
If using a Jupyter Notebook:
bash
Copy code
jupyter notebook Apartment_Scam_Detection_Project.ipynb
If using Python:
bash
Copy code
python apartment_scam_detection.py

Key Visualizations
--------------------
Scatter Plots: Visualize price anomalies and living area outliers detected by the Isolation Forest and LOF models.
Heatmaps: Display suspiciousness scores for listings based on proximity to important locations.
Boxplots: Display principal components for reduced-dimensional data.
Venn Diagrams: Compare overlap in anomalies detected by multiple models.

Conclusion
-------------------
This project provides a comprehensive approach to detecting fraudulent rental property listings. By leveraging machine learning algorithms like Isolation Forest, Local Outlier Factor, and DBSCAN, alongside geospatial and textual analysis, it identifies potential scams effectively. The project’s outputs include a final dataset with flagged anomalies and detailed visualizations to help analyze the results.

Future Work
------------------
Incorporate more advanced anomaly detection algorithms like Autoencoders or XGBoost.
Improve the proximity score by using additional geospatial data or other location-based features.
Train supervised models if labeled data becomes available for scam detection.
Contributing
If you’d like to contribute, please fork the repository and submit a pull request. All contributions are welcome!

License
This project is licensed under the MIT License - see the LICENSE file for details.

