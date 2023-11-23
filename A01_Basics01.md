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




