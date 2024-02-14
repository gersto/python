## Working With Files
1. Reading a File

To read the entire content of a file:

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

2. Writing to a File

To write text to a file, overwriting existing content:

```python
with open('example.txt', 'w') as file:
    file.write('Hello, Python!')
```

3. Appending to a File

To add text to the end of an existing file:

```python
with open('example.txt', 'a') as file:
    file.write('\nAppend this line.')
```

4. Reading Lines into a List

To read a file line by line into a list:

```python
with open('example.txt', 'r') as file:
    lines = file.readlines()
    print(lines)
```

5. Iterating Over Each Line in a File

To process each line in a file:

```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())
```

6. Checking If a File Exists

To check if a file exists before performing file operations:

```python
import os
if os.path.exists('example.txt'):
    print('File exists.')
else:
    print('File does not exist.')
```

7. Writing Lists to a File

To write each element of a list to a new line in a file:

```python
lines = ['First line', 'Second line', 'Third line']
with open('example.txt', 'w') as file:
    for line in lines:
        file.write(f'{line}\n')
```

8. Using With Blocks for Multiple Files

To work with multiple files simultaneously using with blocks:

```python
with open('source.txt', 'r') as source, open('destination.txt', 'w') as destination:
    content = source.read()
    destination.write(content)
```

9. Deleting a File

To safely delete a file if it exists:

```python
import os
if os.path.exists('example.txt'):
    os.remove('example.txt')
    print('File deleted.')
else:
    print('File does not exist.')
```

10. Reading and Writing Binary Files

To read from and write to a file in binary mode (useful for images, videos, etc.):

```python
# Reading a binary file
with open('image.jpg', 'rb') as file:
    content = file.read()
# Writing to a binary file
with open('copy.jpg', 'wb') as file:
    file.write(content)
```

## Working With Simple HTTP APIs
