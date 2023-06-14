# Background
This project is using dataset from kaggle:"Marketing Promotion Campaign Uplift Modelling"
Link: https://www.kaggle.com/datasets/davinwijaya/customer-retention
# Dataset
Marketing Promotion Campaign Dataset with a total of 6,400 customers data.
This dataset show customer's brief information, historical use of discount or BOGO(Buy One Get One) promotion, offer has been made, and the conversion result(buy or not).
# Goal 
The goal of this code is to perform an uplift analysis using XGBoost and visualize the Qini curve for two marketing method: 'Buy One Get One' and 'Discount'. The analysis aims to understand the effectiveness of different marketing method in generating a positive response from customers.
# Analysis Process
1. Data Preprocessing:
   - Imports the necessary libraries and reads the data from a CSV file using `pd.read_csv()`.
   - The target and treatment columns are renamed to 'target' and 'treatment', respectively.
   - The 'treatment' column values are mapped to numerical values (-1 for 'Buy One Get One', 0 for 'No Offer', and 1 for 'Discount').
   - One-hot encoding is applied to convert categorical variables into numerical features.

2. Exploratory Data Analysis:
   - A correlation heatmap is plotted using `sns.heatmap()` to visualize the correlation between different features in the `df_model` DataFrame.

3. Sample Balance Checking:
   - The code prints the counts of each class in the 'treatment' column to check the balance between treatment groups.

4. Adding 'target_class' Column:
   - The 'target_class' column is added to the `df_model` DataFrame based on the combinations of 'treatment' and 'target' values.

5. Train-Test Split:
   - The `X` and `y` variables are defined for the features and target class, respectively.
   - The data is split into training and testing sets using `train_test_split()`.

6. Uplift Model Training and Prediction:
   - An XGBoost classifier (`xgb.XGBClassifier()`) is fitted on the training data by excluding the 'treatment' column.
   - The trained model is then used to predict probabilities (`uplift_proba`) for the test data.
   - The predicted probabilities are stored in the `result` DataFrame, along with the corresponding treatment classes and uplift scores.

7. Uplift Analysis:
   - The `qini_rank()`, `qini_eval()`, and `qini_plot()` functions are defined to calculate and visualize the Qini curve based on the uplift scores.
   - The `qini()` function combines these functions and plots the Qini curve for the 'Buy One Get One' and 'Discount' treatment groups.
   - The resulting Qini curves are displayed using `plt.title()`.
