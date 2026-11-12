# Python Weather Dashboard

## Presetup

### Step 1: Create Project Directory
Open your terminal and create a folder for your project:
```python
mkdir weather-app
cd weather-app
```
```python

```

### Step 2: Create a Virtual Environment
On macOS/Linux:
```python
python3 -m venv venv
source venv/bin/activate
```
On Windows:
```python
python -m venv venv
venv\Scripts\activate
```
You’ll see `(venv)` at the start of your terminal prompt, confirming it's active.

### Step 3: Install Required Packages
We’ll use the `requests` library to fetch weather data from a free API.
```python
pip install requests matplotlib
```
Save dependencies:
```python
pip freeze > requirements.txt
```
