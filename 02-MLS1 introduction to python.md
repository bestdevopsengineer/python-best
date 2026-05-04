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
