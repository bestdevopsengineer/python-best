# python
### What is default file extension of Jupyter Notebook?
  .ipynb
### What is default file extension of Jupyter Notebook?
  colaboratory
### Identify the advantage of Google Colaboratory among the following
  Google Colaboratory consists of many pre-installed libraries
  It becomes easy to share the work using Google Colaboratory
  Google Colaboratory uses the cloud for computation

# colab 
### Which of the following cell can execute Python code?
  code cells
### # at the start of text cell is used to create different levels of headers such as header, sub-header, sub-sub-header etc
  True

# variables
  price = 900
  print('The price of the mobile is $',price,sep='')
  -> The price of the mobile is $900
  brand = 'Apple'
  print('The brand of the mobile is',brand)
  ->The brand of the mobile is Apple
  is_billed = True
  print(is_billed)
  -> True
  discount = price * 0.045
  discounted_price = price - discount
  -> The discounted price of the iPhone is 859.5

# TYPES
  type(price) ->  int
  type(brand) -> str
  type(is_billed) -> bool
  type(discounted_price) -> float

# 1.2 Data Structures 
     
  LIST : Lists are great for storing data for a single attribute
  
    min(price_list) , max(price_list) , ram_list[2]=8 , 
    price_list[0:3]=[900, 899, 600], brand_list[-1]=Apple ,
    brand_list.pop()=['Apple', 'Samsung', 'LG']
    brand_list.append('Motorola')=['Apple', 'Samsung', 'LG', 'Motorola']
      
    brand_list = ['Apple', 'Samsung', 'LG', 'Apple']
    ram_list = [4, 12, 8, 8]
    storage_list = [128, 128, 64, 128]
    price_list = [900, 899, 600, 1000]
    
  TUPLE: we cannot change the elements of a tuple once it is assigned.

    storage = (32,64,128,256)
    

  DICTIONARY: are great for storing data values in key:value pairs for a many attribute
    keys() and values() are methods of a dictionary to extract the lists of dictionary keys and dictionary values respectively.
    
    ###creating a dictionary
    attributes = {
    'Brand':'Apple',
    'RAM (in GB)':4,
    'Storage (in GB)':128,
    'Price (in $)':800
    }
    print(attributes['Price (in $)']) -> 800
    
    attributes.update({'Price (in $)':900})
    
    ####creating a dictionary for storing data.
    products = {
    'Brand':brand_list,
    'RAM (in GB)':ram_list,
    'Storage (in GB)':storage_list,
    'Price (in $)':price_list
    }
    print(products)
    {'Brand': ['Apple', 'Samsung', 'LG', 'Motorola'], 'RAM (in GB)': [4, 12, 8, 8], 'Storage (in GB)': [128, 128, 64, 128], 'Price (in $)': [900, 899, 600, 1000]}

    keys = products.keys()
    print('The keys of the dictionary are :\n',keys)
    The keys of the dictionary are :
      dict_keys(['Brand', 'RAM (in GB)', 'Storage (in GB)', 'Price (in $)'])

    values = products.values()
    print('The values of the dictionary are :\n', values)
    The values of the dictionary are :
       dict_values([['Apple', 'Samsung', 'LG', 'Motorola'], [4, 12, 8, 8], [128, 128, 64, 128], [900, 899, 600, 1000]])

    products['RAM (in GB)'][1] -> 12

# 1.3 Conditional Statements
        
      if (test expression):
        Body of if
      else:
          Body of else

        if (test expression):
            Body of if
        elif (test expression):
            Body of elif
        else:
            Body of else


        Memory = int(input('Enter the memory: '))

        if Memory == 32:
          print('The price of the phone is $600')
        elif Memory == 64:
          print('The price of the phone is $700')
        elif Memory ==128:
          print('The price of the phone is $900')
        else:
          print('Please enter a valid memory requirement')

# 1.4 Looping Statements
    print(range(6)) ->         range(0, 6)
    print(list(range(6))) ->   [0, 1, 2, 3, 4, 5]
    print(list(range(2,6))) -> [2, 3, 4, 5]
    print(list(range(6, 14, 2))) -> [6, 8, 10, 12]

    for iterator_var in sequence:
    statements(s)

    while condition:
    statements(s)

# 1.5 List Comprehensions
    discounted_price_list=[]

  for x in price_list:
    discounted_price = x - (x*(5/100))
    discounted_price_list.append(discounted_price)
    print(discounted_price_list)

    or

    discounted_price_list = [x - (x*(5/100)) for x in price_list]
    print(discounted_price_list)

    budget = int(input('Enter your budget(in dollars): '))
    within_budget = ['Yes' if x <= budget else 'No' for x in discounted_price_list]
    print(within_budget)
    ['No', 'No', 'Yes', 'No']

# 1.6 Functions in Python : 
    a- def display_iphone_attributes():
          price = 900
          ram = 4
          storage = 128
          print('The Apple iPhone has ', ram, ' GB RAM and ', storage, ' GB internal storage and it costs $', price, sep='')

          display_iphone_attributes()
            -> The Apple iPhone has 4 GB RAM and 128 GB internal storage and it costs $900

    b- def display_phone_attributes(brand, price, ram, storage):      positional arguments.
          print('The ', brand, ' phone has ', ram, ' GB RAM and ', storage,' GB internal storage and it costs $',price,sep='')

       display_phone_attributes('samsung', 899, 12, 128)

    c- def dis_price(discount):
          price = 900
          discounted_price = price - price * (discount / 100)
          return discounted_price

    d- lambda functions
        dis_price_lambda = lambda discount : 900 - ( 900 * (discount / 100) )
    
        dis_price_lambda(10) -> 810.0

# 1.7 *args and **kwargs
    *args lets a function take any number of positional arguments  
    (like f(1, 2, 3, 4)).
    
    def add(*args):
      return sum(args)

    add(1, 2)
    add(1, 2, 3, 4, 5)


    **kwargs lets a function take any number of keyword arguments  
    (like f(a=1, b=2, c=3)).
    def greet(name, age):
      print(name, age)

    def greet(**kwargs):
      print(kwargs)

    greet(name="Aristide", age=25, city="Paris")




    They remove the “fixed number of parameters” limitation.
    
     e- def total_amount(price1, price2, price3, price4, price5):
           total = price1 + price2 + price3 + price4 + price5
           return total

        Python allows us flexibility in terms of the number of arguments passed to a function by using *args.
       f- def total_amount(*args):
             total = 0
             for arg in args:
                total += arg
             return total

        We can also use any other text in place of args.
        g- def total_amount(*prices):
             total = 0
             for arg in args:
                total += arg
             return total

          h- def total_discounted_amount(*prices, discount=0.0):    keyword argument:**which is declared using both a name and a default value.**
                total = 0
                for price in prices:
                  total += price
        
                total_discounted_price = total - discount*total
                return total_discounted_price

                print('Total discounted order amount:', total_discounted_amount(700, 599, 650, 900, 820, 630, 520, 799, 999, 840))

            **Note: In Python, keyword arguments should be declared after the positional arguments.**
            i- def total_discounted_amount(*prices,discount=0.0):
                  total = 0
                  for price in prices:
                    total += price
                  total_discounted_price = total - discount*total
                  return total_discounted_price

              j- def customer_net_spend(*prices, discount=0.0, **kwargs):
                    total = 0
                    for price in prices:
                      total += price
                    total_discounted_price = total - discount*total
                    net_spend = total_discounted_price - kwargs['cashback']
                    return net_spend

                 additionals = {'cashback': 5}
                 print('Customer net spend (during last day of festive season):', customer_net_spend(700, 599, 650, discount=0.05, **additionals))   

              k- def order_summary(*prices, **additionals):
                    total = 0
                    for price in prices:
                      total += price
                    net_spend = total - additionals['discount']*total - additionals['cashback']
                    if total >= 10000:
                        reward_points = 300
                    elif total >= 5000:
                        reward_points = 200
                    elif total >= 2000:
                        reward_points = 100
                    else:
                        reward_points = 0

                      return total, net_spend, reward_points

                  additionals = {'discount':0.05, 'cashback': 5}
                  ta, ns, rp = order_summary(700, 599, 750, **additionals)
                  print('Customer Order Summary:\n', '\nTotal Amount:', ta, '\nTotal Discounted Amount:', ns, '\nReward Points Earned:', rp)
