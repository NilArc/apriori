# Apriori Analysis

## Data Used

**Dataset**: credit_standing.csv

## Source of Data

Dataset retrieved from previous activity from Apriori.xlsx.

## Data Information

The Credit Standing dataset contains 425 instances and 13 columns. The primary keys include:

- Checking Account
- Credit History
- Purpose
- Savings Account
- Employment
- Gender
- Marital Status
- Housing
- Job
- Telephone
- Foreign
- Age
- Credit Standing

### Target Variable

- Credit Standing (Bad, Good)

## Problem Statement

The objective is to identify frequent item sets and generate association rules from the credit standing dataset. Specifically, we aim to determine which features are frequently associated with each other and to derive rules that describe these relationships. This involves:
1. Identifying frequent item sets that appear in the dataset with a frequency above a certain threshold.
2. Generating association rules from these item sets, which describe the relationships between features.
3. Measuring these rules by their support and confidence to indicate their frequency and reliability.

## Method

To achieve the goal, the dataset will be prepared and analyzed using the Apriori algorithm. The following steps will be taken:

1. **Load and Read Dataset**: Load the dataset and prepare it for analysis.
2. **Identify Primary Keys**: Determine the primary features to be analyzed.
3. **Filter Items by Support**: Generate a list of frequent items by applying a support threshold.
4. **Generate Unique Item List**: Extract unique values from the dataset.
5. **Calculate Confidence**: Use the support of frequent item sets and their subsets to calculate the confidence of association rules.
6. **Filter Association Rules by Confidence**: Generate a list of interesting and useful rules.

## Algorithm

The Apriori algorithm will be implemented using Python libraries such as Pandas and NumPy. The steps are as follows:

1. **Load Dataset**: Use `pandas.read_csv()` to load the dataset.
2. **Create DataFrame**: Use `pd.DataFrame()` to create a DataFrame for analysis.
3. **Data Cleaning**: Set up column names and clean the data.
4. **Generate Frequent Item Sets**: Use the `groupby()` function to create combinations of features based on the rules.
5. **Calculate Support and Confidence**: Compute the support and confidence of each item set and rule.
6. **Filter Rules**: Filter the rules based on the minimum support and confidence thresholds.

## Solution

To implement the algorithm, we use the Pandas and NumPy modules. The steps include:

1. **Read and Load the Dataset**:
   ```python
   import pandas as pd
   import numpy as np

   data = pd.read_csv('credit_standing.csv')
   ```
2. **Create DataFrame and Clean Data**:
   ```python
   data.columns = ['Checking Account', 'Credit History', 'Purpose', 'Savings Account', 'Employment', 'Gender', 'Marital Status', 'Housing', 'Job', 'Telephone', 'Foreign', 'Age', 'Credit Standing']
   ```
3. **Generate Frequent Item Sets**:
   ```python
   from mlxtend.frequent_patterns import apriori, association_rules

   # Convert categorical data to one-hot encoded format
   one_hot_data = pd.get_dummies(data)

   # Apply the Apriori algorithm to find frequent item sets
   frequent_itemsets = apriori(one_hot_data, min_support=0.1, use_colnames=True)

   # Generate the association rules
   rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=0.6)
   ```
4. **Filter and Print Results**:
   ```python
   print(rules)
   ```

## Evaluation

The effectiveness of the Apriori algorithm is evaluated by comparing the generated association rules and frequent item sets with the expected values calculated using Excel from Apriori.xlsx. The support and confidence values are key metrics for evaluation.

## Data Preparation

### Steps

1. Download the dataset.
2. Load the dataset using Pandas and NumPy modules.
3. Clean the data and set up appropriate column names.

## Results & Discussion

After loading and reading the dataset, the solution was applied to discover frequent item sets and association rules. The results revealed strong correlations between various features, providing insights into the relationships between different attributes in the dataset.

### Key Observations

- The algorithm successfully identified frequent item sets and generated useful association rules.
- Support and confidence metrics helped in filtering the most significant rules.
- The results aligned with the expected outcomes, demonstrating the effectiveness of the Apriori algorithm in finding associations in transactional datasets.

### Conclusion

The Apriori algorithm effectively identified frequent item sets and association rules in the credit standing dataset. The insights gained from these rules can be valuable for understanding customer behavior and making data-driven decisions. The approach demonstrated here can be applied to other transactional datasets to uncover hidden patterns and associations.