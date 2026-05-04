<img width="539" height="155" alt="image" src="https://github.com/user-attachments/assets/3c85a417-7e96-446d-990c-acba7d986271" />

# 1.0 Organizing data in appropriate format

## Creating multiple variables to store unique customer id
      cid1 = 'cid-0001'
      cid2 = 'cid-0002'
      cid3 = 'cid-0003'
      cid4 = 'cid-0004'
      cid5 = 'cid-0005'

# 1.1 Storing customer details as variables
    cid = 'cid-0001' #  a variable is created with name cid and a value is stored as cid-0001 in the variable
    print('The Customer ID of the first customer is',cid) # to display the value of the variable or a statement
    The Customer ID of the first customer is cid-0001

# 1.2 Organizing and querying the data

## What is a List? 
    A list in Python is an ordered group of items or elements which are stored in a single variable.
    list_name = [element1, element2,...., element_n]
    cid = ['cid-0001', 'cid-0002', 'cid-0003', 'cid-0004', 'cid-0005']

    credit_score = [650, 723, 581, 462, 773]   # list for storing credit score
    age_of_customer = [25, 28, 38, 41, 62]     # list for storing age of the customer
    debt_status = ['no-debt', 'no-debt', 'no-debt', 'in-debt', 'no-debt']  # list to store the debt status
    no_of_existing_credit_cards = [3, 2, 4, 1, 2] # list to store the number of existing credit cards

## How are Lists indexed?
    ordered and starts from 0 from beginning
<img width="605" height="94" alt="image" src="https://github.com/user-attachments/assets/aa89edc4-cee1-4d60-8313-9eced7c6e6b6" />
    cid.index('cid-0002') -> 1

    
# 2.0 Getting data into a convenient structure

## 2.1 Converting the dictionary into a pandas dataframe
            !pip install numpy==2.0.2 pandas==2.2.2 matplotlib==3.10.0 seaborn==0.13.2 -q --user
            import pandas as pd
            df = pd.DataFrame(df1)
## 2.2 Accessing and analysing the data
            df.head(3)
            df.tail(3)
            df.shape
            df.info()
            df.describe()

# Understanding the structure of the data
            # Installing the libraries with the specified version.
            !pip install numpy==2.0.2 pandas==2.2.2 matplotlib==3.10.0 seaborn==0.13.2 -q --user
            # import libraries for data manipulation
            import numpy as np
            import pandas as pd
            
            # import libraries for data visualization
            import matplotlib.pyplot as plt
            import seaborn as sns

            from google.colab import drive
            drive.mount('/content/drive')

            # read the data
            df = pd.read_csv('foodhub_order.csv')
            # returns the first 5 rows
            df.head()

            # check the shape of the dataset
            df.shape

            # use info() to print a concise summary of the DataFrame
            df.info()

            # Checking for missing values
            df.isnull().sum()

            # get the summary statistics of the numerical data
            df.describe()

            # How many orders are not rated?
            df['rating'].value_counts()

            # check the unique values
            df['day_of_the_week'].value_counts()

# Exploratory Data Analysis (EDA)

## Univariate Analysis
            # check unique order ID
            df['order_id'].nunique()

            # check unique customer ID
            df['customer_id'].nunique()

            # number of orders that get served by the restaurants.
            df['restaurant_name'].value_counts()

            # check unique cuisine type
            df['cuisine_type'].nunique()

            # Get top 5 restaurants with highest number of orders
            df['restaurant_name'].value_counts()[:5]

            # Get most popular cuisine on weekends
            df_weekend = df[df['day_of_the_week'] == 'Weekend']
            df_weekend['cuisine_type'].value_counts()

            # Get orders that cost above 20 dollars
            df_greater_than_20 = df[df['cost_of_the_order'] > 20]

            # get the mean delivery time
            print('The mean delivery time for this dataset is', round(df['delivery_time'].mean(), 2), 'minutes')

            # Get the counts of  each customer_id
            df['customer_id'].value_counts().head()

            

### countplot
            plt.figure(figsize = (15,5))
            sns.countplot(data = df, x = 'cuisine_type');
<img width="1293" height="500" alt="image" src="https://github.com/user-attachments/assets/cd5c66a4-a7a1-48a7-85d4-8c7a652b7b09" />

### histplot
            sns.histplot(data=df,x='cost_of_the_order')
            plt.show()
<img width="628" height="435" alt="image" src="https://github.com/user-attachments/assets/f57c0f3a-8b96-436b-b642-cc6cf979eaeb" />

### boxplot
            sns.boxplot(data=df,x='cost_of_the_order')
            plt.show()
<img width="582" height="430" alt="image" src="https://github.com/user-attachments/assets/986755a6-d753-49a5-a033-ee1bcf838d65" />

## Multivariate Analysis
            # Relationship between cost of the order and cuisine type
            plt.figure(figsize=(15,7))
            sns.boxplot(x = "cuisine_type", y = "cost_of_the_order", data = df, palette = 'PuBu', hue = "cuisine_type")
            plt.xticks(rotation = 60)
            plt.show()
<img width="1230" height="682" alt="image" src="https://github.com/user-attachments/assets/ec804c27-9ced-47f7-8b50-7172761087e3" />

            # Revenue generated by the restaurants
            plt.figure(figsize = (15, 7))
            df.groupby(['restaurant_name'])['cost_of_the_order'].sum().sort_values(ascending = False).head(14)

            # Relationship between rating and delivery time
            plt.figure(figsize=(15, 7))
            sns.pointplot(x = 'rating', y = 'delivery_time', data = df)
            plt.show()

<img width="1275" height="600" alt="image" src="https://github.com/user-attachments/assets/c123af86-2567-4bf8-aab3-2321fde60fb2" />

## Correlation among variables
            # plot the heatmap
            col_list = ['cost_of_the_order', 'food_preparation_time', 'delivery_time']
            plt.figure(figsize=(15, 7))
            sns.heatmap(df[col_list].corr(), annot=True, vmin=-1, vmax=1, fmt=".2f", cmap="Spectral")
            plt.show()

            <img width="1144" height="596" alt="image" src="https://github.com/user-attachments/assets/83a596f5-605f-45d3-869b-3639e6419802" />

            # filter the rated restaurants
            df_rated = df[df['rating'] != 'Not given'].copy()
            # convert rating column from object to integer
            df_rated['rating'] = df_rated['rating'].astype('int')
            # create a dataframe that contains the restaurant names with their rating counts
            df_rating_count = df_rated.groupby(['restaurant_name'])['rating'].count().sort_values(ascending = False).reset_index()
            df_rating_count.head()

            # get the restaurant names that have rating count more than 50
            rest_names = df_rating_count[df_rating_count['rating'] > 50]['restaurant_name']
            # filter to get the data of restaurants that have rating count more than 50
            df_mean_4 = df_rated[df_rated['restaurant_name'].isin(rest_names)].copy()
            # find the mean rating of the restaurants
            df_mean_4_rating = df_mean_4.groupby(df_mean_4['restaurant_name'])['rating'].mean().sort_values(ascending = False).reset_index()
            # filter for average rating greater than 4
            df_avg_rating_greater_than_4 = df_mean_4_rating[df_mean_4_rating['rating'] > 4].sort_values(by='rating', ascending=False).reset_index(drop=True)
            df_avg_rating_greater_than_4

            #function to determine the net revenue
            def compute_rev(x):
                if x > 20:
                    return x*0.25
                elif x > 5:
                    return x*0.15
                else:
                    return x*0
            
            df['Revenue'] = df['cost_of_the_order'].apply(compute_rev)
            df.head()

            # get the total revenue and print it
            total_rev = df['Revenue'].sum()
            print('The net revenue is around', round(total_rev, 2), 'dollars')

            # add a new column to the dataframe df to store the total delivery time
            df['total_time'] = df['food_preparation_time'] + df['delivery_time']
            
            # find the percentage of orders that have more than 60 minutes of total delivery time
            print ('The percentage of orders that have more than 60 minutes of total delivery time is',
                   round(df[df['total_time'] > 60].shape[0] / df.shape[0] * 100, 2),'%')

            # get the mean delivery time on weekdays and print it
            print('The mean delivery time on weekdays is around',
                  round(df[df['day_of_the_week'] == 'Weekday']['delivery_time'].mean()),
                 'minutes')
            
            # get the mean delivery time on weekends and print it
            print('The mean delivery time on weekends is around',
                  round(df[df['day_of_the_week'] == 'Weekend']['delivery_time'].mean()),
                 'minutes')
