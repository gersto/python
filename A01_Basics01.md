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
