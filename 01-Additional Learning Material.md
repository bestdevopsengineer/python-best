# Object Oriented Programming in Python

## What is a class?
    a class is a user defined data type, where we give a name to the data type
## Attributes
    A variable inside a class is called an attribute.
## Methods
    function that is inside of a class a method
## Objects
    An object is an instance of a particular class.
## Initializer
    If you want to assign some attribute values to your object when you declare it we use an initializer in the class definition
## self
    1-When you add an attribute (variable) in a class you must name it self.attribute_name.
    2-When you add a method (function) to a class, you must have self as the first argument of that function. 

    **the name of the data type (class) must always start with a capital letter **
    
    class My_data_type:  # first letter capitalized
        def init_some_vals(self,val2):  # self is first argument of function
            self.first_var = 1.7        # attributes named self.attribute_name
            self.second_var = val2      # this function doesn't return anything...it just sets some attribute values
        def multiply_vals(self):        # another internal method, but this one does return a value
            return self.first_var*self.second_var

    me = My_data_type()    # declare an object of the class My_data_type
    me.init_some_vals(2.2) # don't give self as an input!!! 
    print(me.first_var)    # access attribute
    print(me.multiply_vals()) # run a method

    1.7
    3.74

    # we can also add attributes to an object outside of the class definition
    

    me.third_var = 231.3
    print(me.third_var)
    -------------------------------------------
    class Pet:
        def __init__(self,animal_type,name,age,weight_lbs,color):  # initializer
            self.animal = animal_type    # assign some attribute values from the input arguments of the initializer
            self.name = name
            self.age = age
            self.weight_lbs = weight_lbs
            self.color = color
            self.weight_kg = self.calc_weight_in_kg()  # automatically run a method...still don't feed self to the call
        
        def calc_weight_in_kg(self):  # remember to give self as an input...even though we don't use it when we call
            return 0.453592*self.weight_lbs
            
        def describe_pet(self):
            print('This pet is a',self.color, self.animal,)
            print('This pet\'s name is',self.name,'and it is',self.age,'years old')
            print('This pet weighs',self.weight_lbs,'pounds, which is',round(self.weight_kg,2),'kilograms')

      # now create 2 objects of the class Pet
        my_cat = Pet('cat','Mittens',3,7,'orange')
        mydog = Pet('dog','Spot',9,18,'brown')
        my_cat.describe_pet()
        print('')  # just so there's some space between the object outputs
        mydog.describe_pet()

        print(my_cat.color)
        print(mydog.age)

        my_cat.weight_lbs = 5
        print(my_cat.weight_lbs)
        print(my_cat.weight_kg)

        # we can also access methods from outside
          print(my_cat.calc_weight_in_kg())
          print(mydog.calc_weight_in_kg())
          print(my_cat.weight_kg)
          my_cat.weight_kg=my_cat.calc_weight_in_kg()
          print(my_cat.weight_kg)
