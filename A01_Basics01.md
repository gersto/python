## Aufgabe01

**Angabe**:

Write a Python program to print the following string in a specific format (see the output).

Sample String : "Twinkle, twinkle, little star, How I wonder what you are! Up above the world so high, Like a diamond in the sky. Twinkle, twinkle, little star, How I wonder what you are"

Output :

```
Twinkle, twinkle, little star,
	How I wonder what you are! 
		Up above the world so high,   		
		Like a diamond in the sky. 
Twinkle, twinkle, little star, 
	How I wonder what you are
```

**Solution**:

```python
print("Twinkle, twinkle, little star, \n\tHow I wonder what you are! \n\t\tUp above the world so high, \n\t\tLike a diamond in the sky. \nTwinkle, twinkle, little star, \n\tHow I wonder what you are!")
```

## Aufgabe02

**Angabe**:

Write a Python program to find out what version of Python you are using.

**Solution**:

```python
import sys  # Import the sys module to access system-specific parameters and functions

# Print the Python version to the console
print("Python version")

# Use the sys.version attribute to get the Python version and print it
print(sys.version)

# Print information about the Python version
print("Version info.")

# Use the sys.version_info attribute to get detailed version information and print it
print(sys.version_info)
```

```python
user@machine1:~$ python --version
Python 2.7.17
user@machine1:~$ python -V
Python 2.7.17
user@machine1:~$ python3 --version
Python 3.6.9
user@machine1:~$ python3 -V
Python 3.6.9
```

```python
import platform
print(platform.python_version())
print(platform.python_version_tuple())
```

## Aufgabe03

**Angabe**:

Write a Python program to display the current date and time.

**Solution**:

```python
# Import the 'datetime' module to work with date and time
import datetime

# Get the current date and time
now = datetime.datetime.now()

# Create a datetime object representing the current date and time

# Display a message indicating what is being printed
print("Current date and time : ")

# Print the current date and time in a specific format
print(now.strftime("%Y-%m-%d %H:%M:%S"))

# Use the 'strftime' method to format the datetime object as a string with the desired format
```

## Aufgabe04

**Angabe**:

Write a Python program that calculates the area of a circle based on the radius entered by the user.

**Solution**:

```python
# Import the 'pi' constant from the 'math' module to calculate the area of a circle
from math import pi

# Prompt the user to input the radius of the circle
r = float(input("Input the radius of the circle : "))

# Calculate the area of the circle using the formula: area = π * r^2
area = pi * r ** 2

# Display the result, including the radius and calculated area
print("The area of the circle with radius " + str(r) + " is: " + str(area))
```

## Aufgabe05

**Angabe**:

Write a Python program that accepts the user's first and last name and prints them in reverse order with a space between them.

**Solution**:

```python
# Prompt the user to input their first name and store it in the 'fname' variable
fname = input("Input your First Name : ")

# Prompt the user to input their last name and store it in the 'lname' variable
lname = input("Input your Last Name : ")

# Display a greeting message with the last name followed by the first name
print("Hello  " + lname + " " + fname)
```

## Aufgabe06

**Angabe**:

Write a Python program that accepts a sequence of comma-separated numbers from the user and generates a list and a tuple of those numbers.

Sample data: 3,5,7,23 (no spaces after ,)

**Solution**:

```python
# Prompt the user to input a sequence of comma-separated numbers and store it in the 'values' variable
values = input("Input some comma-separated numbers: ")

# Split the 'values' string into a list using commas as separators and store it in the 'list' variable
list = values.split(",")

# Convert the 'list' into a tuple and store it in the 'tuple' variable
tuple = tuple(list)

# Print the list
print('List : ', list)

# Print the tuple
print('Tuple : ', tuple)
```

## Aufgabe07

**Angabe**:

Write a Python program that accepts a filename from the user and prints the extension of the file.

Sample filename: abc.java 

**Solution**:

```python
# Prompt the user to input a filename and store it in the 'filename' variable
filename = input("Input the Filename: ")

# Split the 'filename' string into a list using the period (.) as a separator and store it in the 'f_extns' variable
f_extns = filename.split(".")

# Print the extension of the file, which is the last element in the 'f_extns' list
print("The extension of the file is : " + repr(f_extns[-1]))
```

## Aufgabe08

**Angabe**:

Write a Python program to display the first and last colors from the following list.

color_list = ["Red","Green","White" ,"Black"]

**Solution**:

```python
# Create a list called 'color_list' containing color names
color_list = ["Red", "Green", "White", "Black"]
# Print the first and last elements of the 'color_list' using string formatting
# The '%s' placeholders are filled with the values of 'color_list[0]' (Red) and 'color_list[-1]' (Black)
print("%s %s" % (color_list[0], color_list[-1]))
```

## Aufgabe09

**Angabe**:

Write a Python program to display the examination schedule. (extract the date from exam_st_date).

exam_st_date = (11, 12, 2014)<br>
Sample Output: The examination will start from : 11 / 12 / 2014

**Solution**:

```python
# Define a tuple called 'exam_st_date' containing the exam start date in the format (day, month, year)
exam_st_date = (11, 12, 2014)

# Print the exam start date using string formatting
# The '%i' placeholders are filled with the values from the 'exam_st_date' tuple
print("The examination will start from : %i / %i / %i" % exam_st_date)
```

## Aufgabe10

**Angabe**:

Write a Python program that accepts an integer (n) and computes the value of n+nn+nnn.

Sample value of n is 5

**Solution**:

```python
# Prompt the user to input an integer and store it in the variable 'a'
a = int(input("Input an integer: "))

# Create new integers 'n1', 'n2', and 'n3' by concatenating 'a' with itself one, two, and three times, respectively
n1 = int("%s" % a)          # Convert 'a' to an integer
n2 = int("%s%s" % (a, a))   # Concatenate 'a' with itself and convert to an integer
n3 = int("%s%s%s" % (a, a, a))  # Concatenate 'a' with itself twice and convert to an integer

# Calculate the sum of 'n1', 'n2', and 'n3' and print the result
print(n1 + n2 + n3)
```


