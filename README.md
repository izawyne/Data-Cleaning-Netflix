# Data Cleaning for Netflix Dataset
In this notebook, I will perform data cleaning on the Netflix dataset. The goal is to preprocess the data by handling missing values, removing unnecessary columns, standardizing column names, and converting data types where necessary.

This step is crucial to ensure the dataset is clean and ready for further analysis and visualization.

Steps performed
# 1. Importing required libraries
import pandas as pd

# 2. Loading the dataset
data = pd.read_csv('/kaggle/input/netflix-shows/netflix_titles.csv')

# 3. Preliminary dataset exploration
We display the first few rows and the structure of the dataset to understand its composition and check for any missing values.

data.head()

data.info()

data.columns

# 4. Removing unnecessary columns
We decided to remove some columns that would not be useful for analysis.

columns_to_keep = ['show_id', 'type', 'title','country', 'date_added', 'release_year', 'rating', 'duration']

columns_to_drop = ['director','cast','listed_in', 'description']

data.drop(columns=columns_to_drop, inplace=True)

# 5. Updating column names
We standardized the column names to start with uppercase letters.

new_columns_names = [i.capitalize() for i in data.columns]

data.columns = new_columns_names

# 6. Cleaning specific columns
We filled null values in the 'Country' column with 'Unspecified'.

data['Country'] = data['Country'].fillna('Unspecified')

# 7. Dropping remaining null values
We removed rows that still contained null values.

data.dropna(inplace=True)

# 8. Exploring further data transformations
We converted the 'Date_added' column to datetime format, handling possible errors.

data['Date_added'] = pd.to_datetime(data['Date_added'], format='%B %d, %Y', errors='coerce')

# Conclusion
Now, the dataset is clean and ready for further analysis or visualization.

# License
This project is licensed under the MIT License - see the LICENSE file for details.
