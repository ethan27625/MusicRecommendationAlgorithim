# Audio Recommendation Algorithm

## Overview
This project builds an unsupervised music recommendation system using KMeans clustering. The goal is to analyze a dataset of songs from 1950 to 2019, discover meaningful clusters based on lyrical features, and use those clusters to recommend new songs to a hypothetical user.

This project was built as part of a data analytics fellowship simulating a data scientist role at a music platform startup that just secured Series B financing.

## Dataset
The dataset contains 28,362 songs with lyrical and metadata features pulled from a 2020 research paper titled "Music Dataset: Lyrics and Metadata from 1950 to 2019." Features include 15 topic scores (0 to 1 scale) measuring themes like violence, sadness, romantic, obscene, and others, along with song metadata like artist, genre, and release date.

A separate test dataset of 10 songs represents a hypothetical user's listening history used for generating recommendations.

Note: The dataset is not included in this repository and is listed in the .gitignore file.

## Project StructureMusicRecommendationAlgorithm

├── data/music_rec/          # Dataset files (gitignored)
├── EDA.ipynb                # Exploratory Data Analysis
├── cleaning.ipynb           # Data Cleaning and Preprocessing
├── modeling.ipynb            # KMeans Clustering and Recommendations
├── Report.ipynb             # Report answering 5 project questions
├── README.md
└── .gitignore

## Notebooks

### 1. EDA (EDA.ipynb)
- Univariate, bivariate, and multivariate exploratory analysis
- Genre and topic distributions
- Topic score distributions showing heavy right skew
- Correlation heatmap revealing no feature pairs above |r| > 0.5
- Kruskal-Wallis tests confirming all topic scores differ significantly across genres
- Key finding: release_date and age have a perfect -1.0 correlation

### 2. Data Cleaning (cleaning.ipynb)
- Dropped 7 columns (Unnamed: 0, artist_name, track_name, lyrics, topic, genre, release_date)
- No null values or outliers to remove
- Verified no multicollinearity issues in remaining features
- Scaled all features using StandardScaler for KMeans
- PCA analysis for dimensionality visualization
- Final feature set: 17 numeric columns

### 3. Modeling (modeling.ipynb)
- Tested KMeans with k from 2 to 10
- Used elbow method and silhouette scores to find optimal k
- Selected k=10 with silhouette score of 0.1813
- Analyzed clusters through feature heatmaps, genre breakdowns, and sample songs
- Applied model to test dataset of 10 user songs
- Generated recommendations from the user's most common cluster (Cluster 1)

### 4. Report (Report.ipynb)
- Answers the 5 required project questions covering EDA insights, column decisions, optimal clusters, cluster descriptions, and song recommendations

## Key Results
- **Optimal Clusters:** 10 clusters identified using silhouette score analysis
- **Cluster Highlights:** Clusters captured meaningful patterns like violence-heavy songs (Cluster 1), sadness/heartbreak songs (Cluster 3), long explicit hip hop songs (Cluster 7), and older romantic songs (Cluster 4)
- **Recommendations:** Based on the test user's listening history, 10 songs were recommended from Cluster 1 (violence-themed) which was the user's most common cluster

## Technologies Used
- Python 3.11
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn (KMeans, StandardScaler, PCA, silhouette_score)

## Author
Ethan