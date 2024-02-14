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

1. Basic GET Request

To fetch data from an API endpoint using a GET request:

```python
import requests
response = requests.get('https://api.example.com/data')
data = response.json()  # Assuming the response is JSON
print(data)
```

2. GET Request with Query Parameters

To send a GET request with query parameters:

```python
import requests
params = {'key1': 'value1', 'key2': 'value2'}
response = requests.get('https://api.example.com/search', params=params)
data = response.json()
print(data)
```

3. Handling HTTP Errors

To handle possible HTTP errors gracefully:

```python
import requests
response = requests.get('https://api.example.com/data')
try:
    response.raise_for_status()  # Raises an HTTPError if the status is 4xx, 5xx
    data = response.json()
    print(data)
except requests.exceptions.HTTPError as err:
    print(f'HTTP Error: {err}')
```

4. Setting Timeout for Requests

To set a timeout for API requests to avoid hanging indefinitely:

```python
import requests
try:
    response = requests.get('https://api.example.com/data', timeout=5)  # Timeout in seconds
    data = response.json()
    print(data)
except requests.exceptions.Timeout:
    print('The request timed out')
```

5. Using Headers in Requests

To include headers in your request (e.g., for authorization):

```python
import requests
headers = {'Authorization': 'Bearer YOUR_ACCESS_TOKEN'}
response = requests.get('https://api.example.com/protected', headers=headers)
data = response.json()
print(data)
```

6. POST Request with JSON Payload

To send data to an API endpoint using a POST request with a JSON payload:

```python
import requests
payload = {'key1': 'value1', 'key2': 'value2'}
headers = {'Content-Type': 'application/json'}
response = requests.post('https://api.example.com/submit', json=payload, headers=headers)
print(response.json())
```

7. Handling Response Encoding

To handle the response encoding properly:

```python
import requests
response = requests.get('https://api.example.com/data')
response.encoding = 'utf-8'  # Set encoding to match the expected response format
data = response.text
print(data)
```

8. Using Sessions with Requests

To use a session object for making multiple requests to the same host, which can improve performance:

```python
import requests
with requests.Session() as session:
    session.headers.update({'Authorization': 'Bearer YOUR_ACCESS_TOKEN'})
    response = session.get('https://api.example.com/data')
    print(response.json())
```

9. Handling Redirects

To handle or disable redirects in requests:

```python
import requests
response = requests.get('https://api.example.com/data', allow_redirects=False)
print(response.status_code)
```

10. Streaming Large Responses

To stream a large response to process it in chunks, rather than loading it all into memory:

```python
import requests
response = requests.get('https://api.example.com/large-data', stream=True)
for chunk in response.iter_content(chunk_size=1024):
    process(chunk)  # Replace 'process' with your actual processing function
```

## Working With Lists

1. Creating a List

To conjure a list into being:

```python
# A list of mystical elements
elements = ['Earth', 'Air', 'Fire', 'Water']
```

2. Appending to a List

To append a new element to the end of a list:

```python
elements.append('Aether')
```

3. Inserting into a List

To insert an element at a specific position in the list:

```python
# Insert 'Spirit' at index 1
elements.insert(1, 'Spirit')
```

4. Removing from a List

To remove an element by value from the list:

```python
elements.remove('Earth')  # Removes the first occurrence of 'Earth'
```

5. Popping an Element from a List

To remove and return an element at a given index (default is the last item):

```python
last_element = elements.pop()  # Removes and returns the last element
```

6. Finding the Index of an Element

To find the index of the first occurrence of an element:

```python
index_of_air = elements.index('Air')
```

7. List Slicing

To slice a list, obtaining a sub-list:

```python
# Get elements from index 1 to 3
sub_elements = elements[1:4]
```

8. List Comprehension

To create a new list by applying an expression to each element of an existing one:

```python
# Create a new list with lengths of each element
lengths = [len(element) for element in elements]
```

9. Sorting a List

To sort a list in ascending order (in-place):

```python
elements.sort()
```

10. Reversing a List

To reverse the elements of a list in-place:

```python
elements.reverse()
```

## Working With Dictionaries

1. Creating a Dictionary

To forge a new dictionary:

```python
# A tome of elements and their symbols
elements = {'Hydrogen': 'H', 'Helium': 'He', 'Lithium': 'Li'}
```

2. Adding or Updating Entries

To add a new entry or update an existing one:

```python
elements['Carbon'] = 'C'  # Adds 'Carbon' or updates its value to 'C'
```

3. Removing an Entry

To banish an entry from the dictionary:

```python
del elements['Lithium']  # Removes the key 'Lithium' and its value
```

4. Checking for Key Existence

To check if a key resides within the dictionary:

```python
if 'Helium' in elements:
    print('Helium is present')
```

5. Iterating Over Keys

To iterate over the keys in the dictionary:

```python
for element in elements:
    print(element)  # Prints each key
```

6. Iterating Over Values

To traverse through the values in the dictionary:

```python
for symbol in elements.values():
    print(symbol)  # Prints each value
```

7. Iterating Over Items

To journey through both keys and values together:

```python
for element, symbol in elements.items():
    print(f'{element}: {symbol}')
```

8. Dictionary Comprehension

To conjure a new dictionary through an incantation over an iterable:

```python
# Squares of numbers from 0 to 4
squares = {x: x**2 for x in range(5)}
```

9. Merging Dictionaries

To merge two or more dictionaries, forming a new alliance of their entries:

```python
alchemists = {'Paracelsus': 'Mercury'}
philosophers = {'Plato': 'Aether'}
merged = {**alchemists, **philosophers}  # Python 3.5+
```

10. Getting a Value with Default

To retrieve a value safely, providing a default for absent keys:

```python
element = elements.get('Neon', 'Unknown')  # Returns 'Unknown' if 'Neon' is not found
```

## Working With The Operating System

1. Navigating File Paths

To craft and dissect paths, ensuring compatibility across realms (operating systems):


```python
import os
# Craft a path compatible with the underlying OS
path = os.path.join('mystic', 'forest', 'artifact.txt')
# Retrieve the tome's directory
directory = os.path.dirname(path)
# Unveil the artifact's name
artifact_name = os.path.basename(path)
```

2. Listing Directory Contents

To reveal all entities within a mystical directory:


```python
import os
contents = os.listdir('enchanted_grove')
print(contents)
```

3. Creating Directories

To conjure new directories within the fabric of the filesystem:


```python
import os
# create a single directory
os.mkdir('alchemy_lab')
# create a hierarchy of directories
os.makedirs('alchemy_lab/potions/elixirs')
```

4. Removing Files and Directories

To erase files or directories, banishing their essence:


```python
import os
# remove a file
os.remove('unnecessary_scroll.txt')
# remove an empty directory
os.rmdir('abandoned_hut')
# remove a directory and its contents
import shutil
shutil.rmtree('cursed_cavern')
```

5. Executing Shell Commands

To invoke the shell’s ancient powers directly from Python:


```python
import subprocess
# Invoke the 'echo' incantation
result = subprocess.run(['echo', 'Revealing the arcane'], capture_output=True, text=True)
print(result.stdout)
```

6. Working with Environment Variables

To read and inscribe upon the ethereal environment variables:


```python
import os
# Read the 'PATH' variable
path = os.environ.get('PATH')
# Create a new environment variable
os.environ['MAGIC'] = 'Arcane'
```

7. Changing the Current Working Directory

To shift your presence to another directory within the filesystem:


```python
import os
# Traverse to the 'arcane_library' directory
os.chdir('arcane_library')
```

8. Path Existence and Type

To discern the existence of paths and their nature — be they file or directory:


```python
import os
# Check if a path exists
exists = os.path.exists('mysterious_ruins')
# Ascertain if the path is a directory
is_directory = os.path.isdir('mysterious_ruins')
# Determine if the path is a file
is_file = os.path.isfile('ancient_manuscript.txt')
```

9. Working with Temporary Files

To summon temporary files and directories, fleeting and ephemeral:


```python
import tempfile
# Create a temporary file
temp_file = tempfile.NamedTemporaryFile(delete=False)
print(temp_file.name)
# Erect a temporary directory
temp_dir = tempfile.TemporaryDirectory()
print(temp_dir.name)
```

10. Getting System Information

To unveil information about the host system, its name, and the enchantments it supports:


```python
import os
import platform
# Discover the operating system
os_name = os.name  # 'posix', 'nt', 'java'
# Unearth detailed system information
system_info = platform.system()  # 'Linux', 'Windows', 'Darwin'
```

## Working With CLI — STDIN, STDOUT, STDERR

1. Reading User Input

Getting input from STDIN:

```python
user_input = input("Impart your wisdom: ")
print(f"You shared: {user_input}")
```

2. Printing to STDOUT

To print messages to the console:

```python
print("Behold, the message of the ancients!")
```

3. Formatted Printing

To weave variables into your messages with grace and precision:

```python
name = "Merlin"
age = 300
print(f"{name}, of {age} years, speaks of forgotten lore.")
```

4. Reading Lines from STDIN

Trim whitespaces line by line from STDIN:

```python
import sys
for line in sys.stdin:
    print(f"Echo from the void: {line.strip()}")
```

5. Writing to STDERR

To send message to STDERR:

```python
import sys
sys.stderr.write("Beware! The path is fraught with peril.\n")
```

6. Redirecting STDOUT

To redirect the STDOUT:

```python
import sys
original_stdout = sys.stdout  # Preserve the original STDOUT
with open('mystic_log.txt', 'w') as f:
    sys.stdout = f  # Redirect STDOUT to a file
    print("This message is inscribed within the mystic_log.txt.")
sys.stdout = original_stdout  # Restore STDOUT to its original glory
```

7. Redirecting STDERR

Redirecting STDERR:

```python
import sys
with open('warnings.txt', 'w') as f:
    sys.stderr = f  # Redirect STDERR
    print("This warning is sealed within warnings.txt.", file=sys.stderr)
```

8. Prompting for Passwords

To prompt for passwords:

```python
import getpass
secret_spell = getpass.getpass("Whisper the secret spell: ")
```

9. Command Line Arguments

Working with and parsing command line arguments:

```python
import sys
# The script's name is the first argument, followed by those passed by the invoker
script, first_arg, second_arg = sys.argv
print(f"Invoked with the sacred tokens: {first_arg} and {second_arg}")
```

10. Using Argparse for Complex CLI Interactions

Adding descriptions and options/arguments:

```python
import argparse
parser = argparse.ArgumentParser(description="Invoke the ancient scripts.")
parser.add_argument('spell', help="The spell to cast")
parser.add_argument('--power', type=int, help="The power level of the spell")
args = parser.parse_args()
print(f"Casting {args.spell} with power {args.power}")
```

## Working With Mathematical Operations and Permutations

