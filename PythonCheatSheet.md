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

1. Basic Arithmetic Operations

To perform basic arithmetic:

```python
sum = 7 + 3  # Addition
difference = 7 - 3  # Subtraction
product = 7 * 3  # Multiplication
quotient = 7 / 3  # Division
remainder = 7 % 3  # Modulus (Remainder)
power = 7 ** 3  # Exponentiation
```

2. Working with Complex Numbers

To work with complex numbers:

```python
z = complex(2, 3)  # Create a complex number 2 + 3j
real_part = z.real  # Retrieve the real part
imaginary_part = z.imag  # Retrieve the imaginary part
conjugate = z.conjugate()  # Get the conjugate
```

3. Mathematical Functions

Common math functions:

```python
import math
root = math.sqrt(16)  # Square root
logarithm = math.log(100, 10)  # Logarithm base 10 of 100
sine = math.sin(math.pi / 2)  # Sine of 90 degrees (in radians)
```

4. Generating Permutations

Easy way to generate permutations from a given set:

```python
from itertools import permutations
paths = permutations([1, 2, 3])  # Generate all permutations of the list [1, 2, 3]
for path in paths:
    print(path)
```

5. Generating Combinations

Easy way to generate combinations:

```python
from itertools import combinations
combos = combinations([1, 2, 3, 4], 2)  # Generate all 2-element combinations
for combo in combos:
    print(combo)
```

6. Random Number Generation

To get a random number:

```python
import random
num = random.randint(1, 100)  # Generate a random integer between 1 and 100
```

7. Working with Fractions

When you need to work with fractions:

```python
from fractions import Fraction
f = Fraction(3, 4)  # Create a fraction 3/4
print(f + 1)  # Add a fraction and an integer
```

8. Statistical Functions

To get Average, Median, and Standard Deviation:

```python
import statistics
data = [1, 2, 3, 4, 5]
mean = statistics.mean(data)  # Average
median = statistics.median(data)  # Median
stdev = statistics.stdev(data)  # Standard Deviation
```

9. Trigonometric Functions

To work with trigonometry:

```python
import math
angle_rad = math.radians(60)  # Convert 60 degrees to radians
cosine = math.cos(angle_rad)  # Cosine of the angle
```

10. Handling Infinity and NaN

To work with Infinity and NaN:

```python
import math
infinity = math.inf  # Representing infinity
not_a_number = math.nan  # Representing a non-number (NaN)
```

## Working With Databases

1. Establishing a Connection

To create a connection to a Postgres Database:


```python
import psycopg2
connection = psycopg2.connect(
    dbname='your_database',
    user='your_username',
    password='your_password',
    host='your_host'
)
```

2. Creating a Cursor

To create a database cursor, enabling the traversal and manipulation of records:


```python
cursor = connection.cursor()
```

3. Executing a Query

Selecting data from Database:


```python
cursor.execute("SELECT * FROM your_table")
```

4. Fetching Query Results

Fetching data with a cursor:


```python
records = cursor.fetchall()
for record in records:
    print(record)
```

5. Inserting Records

To insert data into tables in a database:


```python
cursor.execute("INSERT INTO your_table (column1, column2) VALUES (%s, %s)", ('value1', 'value2'))
connection.commit()  # Seal the transaction
```

6. Updating Records

To alter the records:


```python
cursor.execute("UPDATE your_table SET column1 = %s WHERE column2 = %s", ('new_value', 'condition_value'))
connection.commit()
```

7. Deleting Records

To delete records from the table:


```python
cursor.execute("DELETE FROM your_table WHERE condition_column = %s", ('condition_value',))
connection.commit()
```

8. Creating a Table

To create a new table, defining its structure:


```python
cursor.execute("""
    CREATE TABLE your_new_table (
        id SERIAL PRIMARY KEY,
        column1 VARCHAR(255),
        column2 INTEGER
    )
""")
connection.commit()
```

9. Dropping a Table

To drop a table:


```python
cursor.execute("DROP TABLE if exists your_table")
connection.commit()
```

10. Using Transactions

To use transactions for atomicity:


```python
try:
    cursor.execute("your first transactional query")
    cursor.execute("your second transactional query")
    connection.commit()  # Commit if all is well
except Exception as e:
    connection.rollback()  # Rollback in case of any issue
    print(f"An error occurred: {e}")
```

## Working With Async IO (Asyncrounous Programming)

1. Defining an Asynchronous Function

To declare an async function:


```python
import asyncio
async def fetch_data():
    print("Fetching data...")
    await asyncio.sleep(2)  # Simulate an I/O operation
    print("Data retrieved.")
```

2. Running an Asynchronous Function

To invoke an asynchronous function and await them:


```python
async def main():
    await fetch_data()
asyncio.run(main())
```

3. Awaiting Multiple Coroutines

To invoke multiple async functions and await all:


```python
async def main():
    task1 = fetch_data()
    task2 = fetch_data()
    await asyncio.gather(task1, task2)
asyncio.run(main())
```

4. Creating Tasks

To dispatch tasks:


```python
async def main():
    task1 = asyncio.create_task(fetch_data())
    task2 = asyncio.create_task(fetch_data())
    await task1
    await task2
asyncio.run(main())
```

5. Asynchronous Iteration

To traverse through asynchronously, allowing time for other functions in between:


```python
async def fetch_item(item):
    await asyncio.sleep(1)  # Simulate an I/O operation
    print(f"Fetched {item}")
async def main():
    items = ['potion', 'scroll', 'wand']
    for item in items:
        await fetch_item(item)
asyncio.run(main())
```

6. Using Asynchronous Context Managers

To ensure resources are managed within the bounds of an asynchronous function:


```python
async def async_context_manager():
    print("Entering context")
    await asyncio.sleep(1)
    print("Exiting context")
async def main():
    async with async_context_manager():
        print("Within context")
asyncio.run(main())
```

7. Handling Exceptions in Asynchronous Code

To gracefully catch and manage the errors with async functions:


```python
async def risky_spell():
    await asyncio.sleep(1)
    raise ValueError("The spell backfired!")
async def main():
    try:
        await risky_spell()
    except ValueError as e:
        print(f"Caught an error: {e}")
asyncio.run(main())
```

8. Asynchronous Generators

To create async generators, each arriving in its own time:


```python
async def fetch_items():
    items = ['crystal', 'amulet', 'dagger']
    for item in items:
        await asyncio.sleep(1)
        yield item
async def main():
    async for item in fetch_items():
        print(f"Found {item}")
asyncio.run(main())
```

9. Using Semaphores

To limit the number of concurrent tasks:


```python
async def guarded_spell(semaphore, item):
    async with semaphore:
        print(f"Processing {item}")
        await asyncio.sleep(1)
async def main():
    semaphore = asyncio.Semaphore(2)  # Allow 2 concurrent tasks
    await asyncio.gather(*(guarded_spell(semaphore, i) for i in range(5)))
asyncio.run(main())
```

10. Event Loops

To directly engage with the asynchronous loop, customizing the flow of execution:


```python
async def perform_spell():
    print("Casting spell...")
    await asyncio.sleep(1)
    print("Spell cast.")
loop = asyncio.get_event_loop()
try:
    loop.run_until_complete(perform_spell())
finally:
    loop.close()
```

## Working With Networks, Sockets, and Network Interfaces

1. Creating a Socket

To create a socket for network communication:

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

2. Connecting to a Remote Server

To establish a link with a remote server through the socket:

```python
s.connect(('example.com', 80))  # Connect to example.com on port 80
```

3. Sending Data

To dispatch data through the network to a connected entity:

```python
s.sendall(b'Hello, server')
```

4. Receiving Data

To receive data from the network:

```python
data = s.recv(1024)  # Receive up to 1024 bytes
print('Received', repr(data))
```

5. Closing a Socket

To gracefully close the socket, severing the network link:

```python
s.close()
```

6. Creating a Listening Socket

To open a socket that listens for incoming connections:

```python
serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
serversocket.bind(('localhost', 8080))  # Bind to localhost on port 8080
serversocket.listen()  # Listen for incoming connections
```

7. Accepting Connections

To accept and establish a network link:

```python
clientsocket, address = serversocket.accept()
print(f"Connection from {address} has been established.")
```

8. Non-blocking Socket Operations

To set a socket’s mode to non-blocking:

```python
s.setblocking(False)
```

9. Working with UDP Sockets

To create a socket for UDP, a protocol for quicker, but less reliable communication:

```python
udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
udp_socket.bind(('localhost', 8081))  # Bind UDP socket to localhost on port 8081
```

10. Enumerating Network Interfaces

To discover the names and addresses of the machine’s network interfaces:

```python
import socket
import netifaces
for interface in netifaces.interfaces():
    addr = netifaces.ifaddresses(interface).get(netifaces.AF_INET)
    if addr:
        print(f"Interface: {interface}, Address: {addr[0]['addr']}")
```

## Working With Pandas Library (Dataframes)

1. Creating a DataFrame

To create a DataFrame with your own columns and data:

```python
import pandas as pd
data = {
    'Element': ['Earth', 'Water', 'Fire', 'Air'],
    'Symbol': ['🜃', '🜄', '🜂', '🜁']
}
df = pd.DataFrame(data)
```

2. Reading Data from a CSV File

To read data from a CSV file, transforming it into a DataFrame:

```python
df = pd.read_csv('elements.csv')
```

3. Inspecting the First Few Rows

To get first rows from dataframe:

```python
print(df.head())
```

4. Selecting Columns

To select specific columns from dataframe:

```python
symbols = df['Symbol']
```

5. Filtering Rows

To sift through the DataFrame, selecting rows that meet your criteria:

```python
fire_elements = df[df['Element'] == 'Fire']
```

6. Creating New Columns

To create new columns in DataFrame derived from the data within:

```python
df['Length'] = df['Element'].apply(len)
```

7. Grouping and Aggregating Data

To gather your data into groups and extract new data through aggregation:

```python
element_groups = df.groupby('Element').agg({'Length': 'mean'})
```

8. Merging DataFrames

To weave together two DataFrames, joining them by a shared key:

```python
df2 = pd.DataFrame({'Element': ['Earth', 'Fire'], 'Quality': ['Solid', 'Plasma']})
merged_df = pd.merge(df, df2, on='Element')
```

9. Handling Missing Data

To clean your DataFrame, filling the voids where data is absent:

```python
df.fillna(value='Unknown', inplace=True)
```

10. Pivoting and Reshaping Data

To transmute the shape of your DataFrame, revealing hidden patterns and structures with a pivot operation:

```python
pivoted_df = df.pivot(index='Element', columns='Symbol', values='Length')
```

## Working With Numpy Library (Arrays)

1. Creating a NumPy Array

To create an array:

```python
import numpy as np
array = np.array([1, 2, 3, 4, 5])
```

2. Array of Zeros or Ones

To create an array filled with zeros:

```python
zeros = np.zeros((3, 3))  # A 3x3 array of zeros
ones = np.ones((2, 4))  # A 2x4 array of ones
```

3. Creating a Range of Numbers

To create a sequence of numbers:

```python
range_array = np.arange(10, 50, 5)  # From 10 to 50, step by 5
```

4. Creating a Linearly Spaced Array

To create a series of values, evenly spaced between two bounds:

```python
linear_spaced = np.linspace(0, 1, 5)  # 5 values from 0 to 1
```

5. Reshaping an Array

To transmute the shape of an array, altering its dimensions:

```python
reshaped = np.arange(9).reshape(3, 3)  # Reshape a 1D array into a 3x3 2D array
```

6. Basic Array Operations

To perform elemental manipulations upon the arrays:

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
sum = a + b  # Element-wise addition
difference = b - a  # Element-wise subtraction
product = a * b  # Element-wise multiplication
```

7. Matrix Multiplication

Basic dot product Operation:

```python
result = np.dot(a.reshape(1, 3), b.reshape(3, 1))  # Dot product of a and b
```

8. Accessing Array Elements

Accessing array elements with useful syntax:

```python
element = a[2]  # Retrieve the third element of array 'a'
row = reshaped[1, :]  # Retrieve the second row of 'reshaped'
```

9. Boolean Indexing

To filter the elements of an array through the sieve of conditionals:

```python
filtered = a[a > 2]  # Elements of 'a' greater than 2
```

10. Aggregations and Statistics

Statistical operations on np arrays:

```python
mean = np.mean(a)
maximum = np.max(a)
sum = np.sum(a)
```

## Working With Matplotlib Library (Data Visualization)

1. Creating a Basic Plot

To create a plot visualization:

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]
plt.plot(x, y)
plt.show()
```

2. Adding Titles and Labels

To create names for axes and title your plot to give better context:

```python
plt.plot(x, y)
plt.title('Growth Over Time')
plt.xlabel('Time')
plt.ylabel('Growth')
plt.show()
```

3. Creating a Scatter Plot

Creating a scatter plot:

```python
plt.scatter(x, y)
plt.show()
```

4. Customizing Line Styles and Markers

To add symbols into your plot, enriching its usefulness:

```python
plt.plot(x, y, linestyle='--', marker='o', color='b')
plt.show()
```

5. Creating Multiple Plots on the Same Axes

Creating Multiple Plots on the Same Axes:

```python
z = [2, 3, 4, 5, 6]
plt.plot(x, y)
plt.plot(x, z)
plt.show()
```

6. Creating Subplots

To create subplots:

```python
fig, ax = plt.subplots(2, 1)  # 2 rows, 1 column
ax[0].plot(x, y)
ax[1].plot(x, z)
plt.show()
```

7. Creating a Histogram

To create a histogram:

```python
data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
plt.hist(data, bins=4)
plt.show()
```

8. Adding a Legend

To create a legend for the plot:

```python
plt.plot(x, y, label='Growth')
plt.plot(x, z, label='Decay')
plt.legend()
plt.show()
```

9. Customizing Ticks

To create your own marks upon the axes, defining the scale of your values:

```python
plt.plot(x, y)
plt.xticks([1, 2, 3, 4, 5], ['One', 'Two', 'Three', 'Four', 'Five'])
plt.yticks([0, 5, 10, 15, 20, 25], ['0', '5', '10', '15', '20', '25+'])
plt.show()
```

10. Saving Figures

To save the plot as a .png:

```python
plt.plot(x, y)
plt.savefig('growth_over_time.png')
```

## Working With Scikit-Learn Library (Machine Learning)

1. Loading a Dataset

To work with datasets for your ML experiments

```python
from sklearn import datasets
iris = datasets.load_iris()
X, y = iris.data, iris.target
```

2. Splitting Data into Training and Test Sets

To divide your data, dedicating portions to training and evaluation:

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```

3. Training a Model

Training a ML Model using RandomForestClassifier:

```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier()
model.fit(X_train, y_train)
```

4. Making Predictions

To access the model predictions:

```python
predictions = model.predict(X_test)
```

5. Evaluating Model Performance

To evaluate your model, measuring its accuracy in prediction:

```python
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, predictions)
print(f"Model accuracy: {accuracy}")
```

6. Using Cross-Validation

To use Cross-Validation:

```python
from sklearn.model_selection import cross_val_score
scores = cross_val_score(model, X, y, cv=5)
print(f"Cross-validation scores: {scores}")
```

7. Feature Scaling

To create the appropriate scales of your features, allowing the model to learn more effectively:

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

8. Parameter Tuning with Grid Search

To refine your model’s parameters, seeking the optimal combination:

```python
from sklearn.model_selection import GridSearchCV
param_grid = {'n_estimators': [10, 50, 100], 'max_depth': [None, 10, 20]}
grid_search = GridSearchCV(model, param_grid, cv=5)
grid_search.fit(X_train, y_train)
```

9. Pipeline Creation

To streamline your data processing and modeling steps, crafting a seamless flow:

```python
from sklearn.pipeline import Pipeline
pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('classifier', RandomForestClassifier())
])
pipeline.fit(X_train, y_train)
```

10. Saving and Loading a Model

To preserve your model:

```python
import joblib
# Saving the model
joblib.dump(model, 'model.joblib')
# Loading the model
loaded_model = joblib.load('model.joblib')
```

## Working With Plotly Library (Interactive Data Visualization)
