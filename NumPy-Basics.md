## Aufgabe1
### Angabe
Write a Numpy program to get the Numpy version and show the Numpy build configuration.

### Lösung
```python
# Importing the NumPy library with an alias 'np'
import numpy as np

# Printing the version of NumPy installed
print(np.__version__)

# Printing the configuration details of NumPy
print(np.show_config())
```

## Aufgabe2
### Angabe
Write a NumPy program to get help with the add function.

### Lösung
```python
# Importing the NumPy library with an alias 'np'
import numpy as np

# Printing information about the np.add function using the np.info() method
print(np.info(np.add))
```
