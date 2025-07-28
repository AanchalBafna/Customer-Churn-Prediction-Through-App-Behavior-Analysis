# Customer-Churn-Prediction-Through-App-Behavior-Analysis

                                   
Objective:

A FinTech company launched a mobile app and provided a 24-hour free trial. The goal of this project is to segment users based on their behavior during the trial using clustering techniques. This helps the company:
- Understand user engagement patterns.
- Identify low-engagement users.
- Offer personalized deals to improve subscription conversion rates.
This is an unsupervised machine learning problem.


Dataset Overview:

1. FineTech_appData.csv - Main dataset with user behavior.
2. top_screens.csv - List of top app screens used to generate binary screen features.

The dataset has 50,000 records and 12 features, including:
- user: Unique ID
- first_open, enrolled_date: Timestamps
- screen_list: Comma-separated screens visited
- numscreens: Number of screens visited
- enrolled: Target flag (1 if enrolled)
- Derived features: difference (time to enroll), flags for top screens, screen group countsop Screens Feature Engineering:

-top_screens.csv contains a list of the most important app screens (features).
- These were used to generate binary variables: if a user visited a top screen, a 1 was assigned, else 0.
- Examples of top screens used:
  - Loan Screens: Loan2, Loan3, Loan4, Loan5
  - Saving Screens: Saving1, Saving2, Saving2Amount, Saving4, Saving5
  - Credit Screens: Credit1, Credit2, Credit3, Credit3Container, Credit3Dashboard
  - CC (Credit Card) Screens: CC1, CC1Category, CC3


Preprocessing & Feature Engineering:

- Converted `first_open` and `enrolled_date` to datetime.
- Created `difference` feature: time to enroll (in hours).
- Users with `difference > 48` were marked as not enrolled.
- Parsed `screen_list` using `top_screens.csv` to generate binary columns for each top screen.
- Grouped screens into features: Savings Count, Credit Count, Loan Count, etc.
- Removed original `screen_list` and redundant columns.
- Standardized numerical features using `StandardScaler`.

Unsupervised Learning Methods:

1. K-Means Clustering:
   - Used the Elbow Method to find optimal K (number of clusters).
   - K=4 was selected for meaningful segmentation.

2. DBSCAN:
   - Applied for comparison to detect noise and density-based clusters.

3. PCA (Principal Component Analysis):
   - Reduced feature dimensions for visualization.
   - Used 2D PCA plots to visualize clusters and identify behavior-based groupings.

Results & Behavioral Insights:

- Clusters revealed meaningful patterns:
  - One group converted quickly (enrolled within hours).
  - One explored many screens but didn’t enroll (curious).
  - One group had very low engagement (few screens, no premium use).
- Final PCA scatterplot clearly highlighted low-engagement cluster for targeting.
- DBSCAN showed some noise users that didn’t belong to major patterns.

Conclusion & Business Impact:

- Effective segmentation of app users was achieved using unsupervised learning.
- The company can:
  - Send special offers to the low-engagement group.
  - Improve onboarding for curious users.
  - Prioritize feature development for highly engaged users.

Files in This Project:
-----------------------
- UML_Project.ipynb       : Jupyter notebook with full analysis and clustering.
- FineTech_appData.csv    : Main dataset with user behavior data.
- top_screens.csv         : List of screens used for feature engineering.
- UML_report.pdf          : Final report document.
- README.txt              : Overview of the project.



MSc Data Science, NMIMS


