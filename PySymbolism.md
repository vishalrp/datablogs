### Symbol'ism (6 symbols used in Python)!

Python is considered one of the most readable languages because the syntax was designed by the creators to make it easy to read! Best coding practices like indenting your code are not optional but required by the language. Often times the code to do something is exactly how you would say it.

However, all the symbols and syntax can still be confusing, so let's explore that a little in this post.

#### 1. When is # (called hash) used?
To comment your code– any line starting with # is ignored by Python during execution.

#### 2. Where are { } (also called braces or curly-braces or curly-brackets) used?
In python we use them in 2 places:

```python
# Defining dictionary {key1: value1, key2: value2}

city_data = {'city': 'London', 'temp': 28}
empty_dict = {}

# Defining sets

all_cities = {'London', 'Irvine', 'Los Angeles'}
empty_set = set()
```

#### 3. Where are [ ] (also called brackets or square-brackets) used?

```python
# Used to define lists

city_list = ['London', 'Irvine', 'Los Angeles']

# Used along with a variable to mean "lookup" or "index"
```

```python
# INDEXING A LIST USES []
city_list[0] # this refers to 'London' 

# SLICING A LIST USES []
city_list[0:2] 
# starting at 0 till before index 2
# output will be ['London', 'Irvine']

city_list[0:-1] 
# this says start at 0 and go till -1 index, i.e. ignore last item 
# this will also output ['London', 'Irvine']

Note how [0] returns the item, while [0:2] returns a list (called a slice of the list)
# LOOKUP IN A DICTIONARY USES []
city_data = {'city': 'London', 'temp': 28}

city_data['temp'] 
# this returns temperature from the dictionary city_data.
# LOOKUP THINGS IN PANDAS USES []
df = pd.DataFrame({'city': ['Irvine', 'London', 'Los Angeles'],
                   'temp': [70, 40, 60]})

df['city'] 
# look up the city column


df.loc[:, 'temp'] 
# using the loc, look up all rows (:) and column temp

df.iloc[0, 0:2]
# using the iloc, look up row 0, column 0->2 (i.e. column 0,1) 
```

#### 4. Where are ( ) (called parens or parenthesis) used?
```python
# IN PYTHON THE MOST COMMON USE OF () IS TO CALL A FUNCTION WHEN YOU HAVE A FUNCTION YOU NEED () TO CALL IT.
print('Hello')
# calling the function print, with 'Hello' as the input.

df['temp'].mean()
# calling the function mean, on the column 'temp'.

import matplotlib.pyplot as plt
plt.plot([1,2,3,4])
plt.ylabel('some numbers')
plt.show()

# plot the list [1,2,3,4], label y axis, and then show the plot. 
# All function calls!

response = requests.get(url)
# get is a function inside requests that we are calling.
YOU ALSO USE ( ) WHEN DEFINING A TUPLE–
point = (2, 4)
# tuple defining "point" with 2 and 4 and the values in the tuple.
```

#### 5. When is . (dot) used?
In Python . is used to refer to variables or functions attached to a python object.

```python

response = requests.get(url)
response.url
response.status_code
reader = csv.reader(f)
some_string.title()
It is also used to refer to modules and submodules.

from scipy.stats import sem
# scipy is called the python module and stats is a sub-module. 
# We are importing the function sem from within that.

import matplotlib.pyplot as plt
# From matplotlib module we are importing pyplot and 
# for convenience we are giving it an alias plt.
```

#### 6. Finally, when is : (called colon) used?
IN PYTHON : CAN MEAN 3 THINGS
- To define the start of a new code-block. For instance code that goes inside for loop, or if condition, or inside a with block.
- Used when defining a dictionary– {key: value}
- Used when defining a range or a slice- cities[0:2]

EXAMPLES FOR 1
```python
for i in range(5):
	print(i)

with open(filepath) as f:
	...

if x > 10:
	...
	
while i < 5:
	...
```

EXAMPLES FOR 2 AND 3 COVERED EARLIER IN THE POST.
Hope you enjoyed Python Symbol'ism!
