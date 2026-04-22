# Backend Development - Essential Python Topics

## Simple Explanation (Hinglish)
Backend developer banne ke liye sirf Python syntax aana kaafi nahi hai. Aapko yeh pata hona chahiye ki real-world applications kaise banate hain, database kaise connect karte hain, API kaise secure karte hain, aur code ko production-ready kaise banate hain. Yeh notes aapko woh saare advanced concepts sikhayenge jo job interviews aur actual work mein kaam aayenge.

---

## 1. Virtual Environments & Package Management

### Simple Explanation (Hinglish)
Maan lo tumhare paas 2 projects hain - Project A ko `requests` ka purana version chahiye aur Project B ko naya version. Agar dono ko same jagah install karoge to conflict ho jayega. Isliye hum har project ke liye alag "sandbox" ya "virtual room" banate hain jise **Virtual Environment** kehte hain.

### Theory (Clear + Structured)
- **Virtual Environment**: Ek isolated Python environment jahan aapke project-specific packages install hote hain without affecting global Python installation.
- **pip**: Python Package Manager - libraries install/uninstall karne ke liye.
- **requirements.txt**: Ek file jo list karti hai ki project ko kaun-kaun si libraries chahiye.

### Examples with Hinglish Comments

```python
# Terminal commands (Python code nahi, par yaad rakhna zaroori hai):

# Step 1: Virtual environment banana
# Windows pe:
python -m venv venv
# Mac/Linux pe:
python3 -m venv venv

# Step 2: Virtual environment activate karna
# Windows (Command Prompt):
venv\Scripts\activate
# Windows (PowerShell):
venv\Scripts\Activate.ps1
# Mac/Linux:
source venv/bin/activate

# Step 3: Ab jo bhi install karoge wo venv ke andar hoga
pip install requests flask
# # Requests aur Flask install ho gaye virtual environment mein

# Step 4: Installed packages ki list save karna
pip freeze > requirements.txt
# # Saare packages ki list requirements.txt mein save ho gayi

# Step 5: Kisi aur computer pe same packages install karna
pip install -r requirements.txt
# # Requirements.txt se saare packages automatically install ho jayenge
```

### Common Mistakes
1. **Virtual environment activate karna bhool jana**: Seedha `pip install` mat karo, pehle `activate` karo.
2. **`venv` folder ko Git pe push karna**: `.gitignore` file mein `venv/` add karo taaki heavy folder upload na ho.

### Interview Notes
1. **Why Virtual Environment?**: Different projects may need different versions of the same library. Virtual environments prevent version conflicts.
2. **What is `pip`?**: `pip` stands for "Pip Installs Packages". It's the standard package manager for Python.

### Practice Questions
**Easy:**
1. Create a virtual environment named `myenv` and activate it.

**Medium:**
1. Install `flask` in your virtual environment and create a `requirements.txt` file.

**Hard:**
1. Set up two different virtual environments with different versions of `requests` library (e.g., 2.25.0 and 2.28.0).

---

## 2. Type Hinting (Modern Python)

### Simple Explanation (Hinglish)
Python dynamically typed hai (variable ka type batane ki zaroorat nahi), lekin bade projects mein yeh confusion create karta hai ki function mein kaunsa data ja raha hai. **Type Hinting** se hum explicitly bata sakte hain ki variable ka type kya hai. Yeh code run nahi rokta, bas readability badhata hai aur IDEs ko help karta hai.

### Theory (Clear + Structured)
- **Type Hints**: Annotations that specify the expected data types of variables, function parameters, and return values.
- Introduced in Python 3.5+ via PEP 484.
- Tools like `mypy` can check type errors before running code.

### Examples with Hinglish Comments

```python
from typing import List, Dict, Optional, Union

# Simple type hint for variables
name: str = "Rahul"
age: int = 25
price: float = 99.99
is_active: bool = True
# # Variables ke saath unka type likh diya - yeh sirf documentation hai

# Function with type hints
def greet_user(username: str, age: int) -> str:
    # username string hai, age integer hai, aur function string return karega
    return f"Hello {username}, you are {age} years old"

# List type hint
fruits: List[str] = ["apple", "banana", "cherry"]
numbers: List[int] = [1, 2, 3, 4, 5]
# # List mein kis type ke elements hain woh specify kiya

# Dictionary type hint
user_data: Dict[str, Union[str, int]] = {
    "name": "Aman",
    "age": 30,
    "city": "Delhi"
}
# # Dict mein keys string hain, values ya to string ya int ho sakti hain

# Optional type hint (None bhi ho sakta hai)
def find_user(user_id: int) -> Optional[str]:
    # Ya to user name return hoga (string), ya None agar user na mile
    if user_id == 1:
        return "Rahul"
    return None

# Complex example with nested types
def process_orders(orders: List[Dict[str, Union[str, float]]]) -> float:
    # Orders ek list hai, jisme dictionaries hain
    # Har dict mein string keys hain aur values ya string ya float
    total = 0.0
    for order in orders:
        total += order.get("amount", 0.0)
    return total

# Testing
print(greet_user("Priya", 28))  # Hello Priya, you are 28 years old
print(find_user(1))  # Rahul
print(find_user(99))  # None
```

### Common Mistakes
1. **Type hints ko strict validation samajhna**: Type hints runtime pe error nahi fenkte. Wo sirf documentation ke liye hain.
2. **Har jagah type hint lagana**: Chhote scripts mein zaroori nahi, lekin bade projects mein best practice hai.

### Interview Notes
1. **Does Python enforce types?**: No, Python doesn't enforce type hints at runtime. They're for static analysis tools like `mypy`.
2. **Benefits**: Better IDE autocomplete, easier code maintenance, self-documenting code.

### Practice Questions
**Easy:**
1. Add type hints to a function that takes two integers and returns their sum.

**Medium:**
1. Create a function that accepts a list of strings and returns a dictionary with word counts. Add proper type hints.

**Hard:**
1. Write a generic function using `typing.Generic` that can handle multiple data types.

---

## 3. Logging (Professional Debugging)

### Simple Explanation (Hinglish)
`print()` statements se debugging karna amateur tarika hai. Production code mein hum **Logging** use karte hain. Logging se hum different levels set kar sakte hain (INFO, ERROR, WARNING), aur logs ko files mein save kar sakte hain baad mein check karne ke liye.

### Theory (Clear + Structured)
- **Logging Levels**:
  - `DEBUG`: Detailed information for diagnosing problems.
  - `INFO`: Confirmation that things are working as expected.
  - `WARNING`: An indication that something unexpected happened.
  - `ERROR`: Due to a more serious problem, some function has not been performed.
  - `CRITICAL`: A very serious error, indicating inability to continue.
- **Handlers**: Define where logs go (console, file, email, etc.).
- **Formatters**: Define how logs look (timestamp, level, message).

### Examples with Hinglish Comments

```python
import logging

# Basic configuration - sabse pehle setup karo
logging.basicConfig(
    level=logging.DEBUG,  # Sabhi levels ke logs dikhenge
    format='%(asctime)s - %(levelname)s - %(message)s',
    # Format: Time - Level - Message
    filename='app.log',  # Logs is file mein save honge
    filemode='a'  # Append mode (purane logs delete nahi honge)
)

# Different logging levels
logging.debug("Yeh debug message hai - detailed info ke liye")
logging.info("Application start ho gaya")
logging.warning("Kuch unusual ho raha hai par application chal raha hai")
logging.error("Error aa gaya! Koi function fail ho gaya")
logging.critical("Bahot serious error! Application band hone wala hai")

# Real-world example: Function mein logging
def divide_numbers(a, b):
    logging.info(f"Divide function called with a={a}, b={b}")
    
    if b == 0:
        logging.error("Division by zero attempted!")
        return None
    
    result = a / b
    logging.debug(f"Result calculated: {result}")
    return result

# Testing
divide_numbers(10, 2)  # Success case
divide_numbers(10, 0)  # Error case

# Advanced: Multiple loggers for different modules
logger_db = logging.getLogger('database')
logger_api = logging.getLogger('api')

logger_db.info("Database connection established")
logger_api.warning("API rate limit approaching")
```

### Sample `app.log` File Output:
```
2024-01-15 10:30:45,123 - INFO - Application start ho gaya
2024-01-15 10:30:46,456 - INFO - Divide function called with a=10, b=2
2024-01-15 10:30:46,457 - DEBUG - Result calculated: 5.0
2024-01-15 10:30:47,789 - INFO - Divide function called with a=10, b=0
2024-01-15 10:30:47,790 - ERROR - Division by zero attempted!
```

### Common Mistakes
1. **Production mein DEBUG level chhod dena**: Production mein hamesha `INFO` ya `WARNING` level rakho, warna log file bahot badi ho jayegi.
2. **Sensitive data log karna**: Passwords, API keys, ya personal information kabhi mat log karo!

### Interview Notes
1. **Why logging over print()?**: Logging can be disabled/filtered without changing code, logs can be saved to files, and different levels provide context.
2. **Log rotation**: In production, use `RotatingFileHandler` to prevent log files from growing infinitely.

### Practice Questions
**Easy:**
1. Configure logging to write only ERROR and CRITICAL messages to a file.

**Medium:**
1. Create a logger for a web scraper that logs each URL being scraped and any errors encountered.

**Hard:**
1. Implement log rotation so that when a log file reaches 5MB, it creates a new file automatically.

---

## 4. Database Integration with SQLite

### Simple Explanation (Hinglish)
Backend developer ka main kaam hota hai data ko store karna aur retrieve karna. **SQLite** ek lightweight database hai jo Python ke saath built-in aati hai. Isme server ki zaroorat nahi hoti, seedha file mein data store hota hai. Seekhne ke liye perfect hai!

### Theory (Clear + Structured)
- **SQLite**: Serverless, self-contained SQL database engine.
- **CRUD Operations**: Create, Read, Update, Delete - basic database operations.
- **Cursor**: Object used to execute SQL queries.
- **Connection**: Object representing the database connection.

### Examples with Hinglish Comments

```python
import sqlite3

# Step 1: Database connection banana (file automatically ban jayegi)
conn = sqlite3.connect('my_database.db')
# # Agar file nahi thi to nayi ban jayegi, warna existing open ho jayegi

cursor = conn.cursor()
# # Cursor se hum queries execute karenge

# Step 2: Table banana
cursor.execute('''
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT UNIQUE NOT NULL,
        age INTEGER,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    )
''')
# # Users table bana diya with columns: id, name, email, age, created_at

conn.commit()
# # Changes ko permanently save karna zaroori hai

# Step 3: Data insert karna (CREATE)
def add_user(name, email, age):
    try:
        cursor.execute('''
            INSERT INTO users (name, email, age) 
            VALUES (?, ?, ?)
        ''', (name, email, age))
        # # ? placeholders hain SQL injection se bachne ke liye
        conn.commit()
        print(f"User {name} added successfully!")
    except sqlite3.IntegrityError:
        print(f"Email {email} already exists!")

add_user("Rahul", "rahul@example.com", 25)
add_user("Priya", "priya@example.com", 28)
add_user("Aman", "aman@example.com", 30)

# Step 4: Data read karna (READ)
cursor.execute('SELECT * FROM users')
all_users = cursor.fetchall()
# # Saare users fetch kar liye list mein

print("\nAll Users:")
for user in all_users:
    print(f"ID: {user[0]}, Name: {user[1]}, Email: {user[2]}, Age: {user[3]}")

# Specific user dhundhna
cursor.execute('SELECT * FROM users WHERE age > ?', (26,))
older_users = cursor.fetchall()
print("\nUsers older than 26:")
for user in older_users:
    print(f"{user[1]} is {user[3]} years old")

# Step 5: Data update karna (UPDATE)
cursor.execute('''
    UPDATE users 
    SET age = ? 
    WHERE email = ?
''', (29, "priya@example.com"))
conn.commit()
print("\nPriya's age updated to 29")

# Step 6: Data delete karna (DELETE)
cursor.execute('DELETE FROM users WHERE name = ?', ("Aman",))
conn.commit()
print("Aman deleted from database")

# Step 7: Connection close karna
conn.close()
```

### SQL Injection Prevention
```python
# GALAT TARIKA (SQL Injection vulnerable):
# cursor.execute(f"SELECT * FROM users WHERE email = '{email}'")

# SAHI TARIKA (Parameterized query):
cursor.execute("SELECT * FROM users WHERE email = ?", (email,))
# # Humesha ? placeholder use karo user input ke saath
```

### Common Mistakes
1. **`commit()` bhool jana**: Insert/Update/Delete ke baad `commit()` nahi kiya to changes save nahi honge!
2. **Connection close nahi karna**: Hamesha `conn.close()` karo ya `with` statement use karo.
3. **SQL Injection**: User input ko directly query mein mat daalo, hamesha parameterized queries use karo.

### Interview Notes
1. **What is ACID?**: Atomicity, Consistency, Isolation, Durability - properties that guarantee reliable database transactions.
2. **SQLite vs MySQL/PostgreSQL**: SQLite is file-based (good for small apps/testing), while MySQL/PostgreSQL are server-based (good for production).

### Practice Questions
**Easy:**
1. Create a database with a `products` table having columns: id, name, price, quantity.

**Medium:**
1. Write functions to add, view, update, and delete products from the database.

**Hard:**
1. Create two tables `customers` and `orders` with a foreign key relationship. Write a query to get all orders for a specific customer.

---

## 5. AsyncIO Basics (Asynchronous Programming)

### Simple Explanation (Hinglish)
Normal Python code line-by-line chalta hai (synchronous). Agar ek line mein 5 second ka wait hai, to poora code ruk jata hai. **AsyncIO** se hum multiple tasks ko "concurrently" chala sakte hain. Jaise ek waiter ek table se order leta hai, kitchen ko deta hai, aur dusre table pe chala jata hai - wait nahi karta!

### Theory (Clear + Structured)
- **async/await**: Keywords for defining and using coroutines.
- **Coroutine**: A function that can pause its execution and resume later.
- **Event Loop**: Manages and executes asynchronous tasks.
- **Use Cases**: Web scraping, API calls, file I/O, database queries.

### Examples with Hinglish Comments

```python
import asyncio
import time

# Normal synchronous function (slow)
def fetch_data_sync(task_name, delay):
    print(f"Started {task_name}")
    time.sleep(delay)  # Poora program ruk jata hai
    print(f"Finished {task_name}")
    return f"Data from {task_name}"

# Asynchronous function (fast)
async def fetch_data_async(task_name, delay):
    print(f"Started {task_name}")
    await asyncio.sleep(delay)  # Sirf yeh task rukega, baaki chalte rahenge
    print(f"Finished {task_name}")
    return f"Data from {task_name}"

# Synchronous execution (total time: 1+2+3 = 6 seconds)
start = time.time()
fetch_data_sync("Task 1", 1)
fetch_data_sync("Task 2", 2)
fetch_data_sync("Task 3", 3)
print(f"Synchronous total time: {time.time() - start:.2f} seconds\n")

# Asynchronous execution (total time: ~3 seconds - sab parallel chale!)
async def main():
    # Saare tasks ek saath start honge
    results = await asyncio.gather(
        fetch_data_async("Task 1", 1),
        fetch_data_async("Task 2", 2),
        fetch_data_async("Task 3", 3)
    )
    # gather() sab tasks complete hone ka wait karega
    print(f"\nResults: {results}")

start = time.time()
asyncio.run(main())
print(f"Asynchronous total time: {time.time() - start:.2f} seconds")

# Real-world example: Multiple API calls
async def fetch_user_data(user_id):
    print(f"Fetching data for user {user_id}...")
    await asyncio.sleep(1)  # Simulating API call
    return {"id": user_id, "name": f"User {user_id}"}

async def fetch_all_users():
    user_ids = [1, 2, 3, 4, 5]
    # Saare API calls parallel mein honge
    tasks = [fetch_user_data(uid) for uid in user_ids]
    users = await asyncio.gather(*tasks)
    return users

# Running the async function
all_users = asyncio.run(fetch_all_users())
print(f"\nFetched {len(all_users)} users concurrently!")
```

### Common Mistakes
1. **`await` bhool jana**: Async function ko call karte waqt `await` lagana zaroori hai.
2. **Blocking calls in async code**: `time.sleep()` mat use karo, `await asyncio.sleep()` use karo.
3. **Overusing async**: CPU-intensive tasks ke liye async faydemand nahi hai, sirf I/O bound tasks ke liye use karo.

### Interview Notes
1. **When to use AsyncIO?**: Use for I/O-bound tasks (network requests, file operations, database queries). Not for CPU-bound tasks.
2. **GIL (Global Interpreter Lock)**: Python's GIL prevents true parallelism in threads, but async works around this for I/O operations.

### Practice Questions
**Easy:**
1. Create an async function that prints numbers from 1 to 5 with 1-second delay.

**Medium:**
1. Write an async program that fetches data from 3 different "fake APIs" (use asyncio.sleep) concurrently.

**Hard:**
1. Create an async web scraper that scrapes multiple URLs simultaneously without blocking.

---

## 6. Environment Variables & Security

### Simple Explanation (Hinglish)
Code mein passwords, API keys, ya database URLs hard-code karna bahot dangerous hai! Agar code GitHub pe daala to sab kuch leak ho jayega. **Environment Variables** se hum sensitive data ko alag `.env` file mein rakhte hain jo Git pe upload nahi hoti.

### Theory (Clear + Structured)
- **Environment Variables**: Dynamic values that can affect the way running processes behave on a computer.
- **`.env` file**: A text file containing key-value pairs for configuration.
- **`python-dotenv`**: Library to load `.env` files in Python.
- **Best Practice**: Never commit `.env` files to version control.

### Examples with Hinglish Comments

```python
# Pehle install karo: pip install python-dotenv

from dotenv import load_dotenv
import os

# .env file se variables load karna
load_dotenv()

# Ab environment variables access kar sakte ho
DATABASE_URL = os.getenv("DATABASE_URL")
# # DATABASE_URL variable .env file se utha liya

API_KEY = os.getenv("API_KEY")
SECRET_KEY = os.getenv("SECRET_KEY")
DEBUG_MODE = os.getenv("DEBUG_MODE", "False")
# # Second argument default value hai agar variable na mile

print(f"Database: {DATABASE_URL}")
print(f"API Key: {API_KEY}")
print(f"Debug Mode: {DEBUG_MODE}")

# Safe credential handling example
def connect_to_database():
    db_url = os.getenv("DATABASE_URL")
    if not db_url:
        raise ValueError("DATABASE_URL not found in environment variables!")
    
    # Connection code here...
    print(f"Connecting to {db_url}...")
    return "Connected!"

# Testing
try:
    connect_to_database()
except ValueError as e:
    print(f"Error: {e}")
```

### Sample `.env` File:
```bash
# .env file (ISE GIT PE MAT DALNA!)
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
API_KEY=sk-1234567890abcdef
SECRET_KEY=my-super-secret-key-123
DEBUG_MODE=True
EMAIL_PASSWORD=email_password_here
```

### Sample `.gitignore` File:
```bash
# .gitignore mein yeh add karo
.env
venv/
__pycache__/
*.log
```

### Common Mistakes
1. **`.env` file ko Git pe push karna**: Hamesha `.gitignore` mein `.env` add karo.
2. **Default values na dena**: `os.getenv("KEY", "default")` use karo taaki error na aaye.
3. **Production mein .env rely karna**: Production mein environment variables directly server pe set karo.

### Interview Notes
1. **Why not hardcode secrets?**: Hardcoded secrets can be exposed through version control, decompilation, or accidental sharing.
2. **12-Factor App**: Methodology that recommends storing config in environment variables.

### Practice Questions
**Easy:**
1. Create a `.env` file with a variable `APP_NAME` and print it in Python.

**Medium:**
1. Build a script that reads API credentials from `.env` and makes a request to an API.

**Hard:**
1. Create a configuration class that loads all settings from environment variables with proper validation.

---

## 7. Web Scraping with BeautifulSoup

### Simple Explanation (Hinglish)
Internet se automatically data extract karne ko **Web Scraping** kehte hain. Jaise Amazon se product prices nikalna, ya news websites se headlines collect karna. **BeautifulSoup** HTML ko parse karne mein help karta hai.

### Theory (Clear + Structured)
- **BeautifulSoup**: Library for parsing HTML and XML documents.
- **requests**: Library for making HTTP requests.
- **HTML Tags**: Elements like `<div>`, `<a>`, `<p>` that structure web pages.
- **Selectors**: Methods to find elements (`find()`, `find_all()`, CSS selectors).

### Examples with Hinglish Comments

```python
# Pehle install karo: pip install requests beautifulsoup4

import requests
from bs4 import BeautifulSoup

# Website se HTML fetch karna
url = "https://books.toscrape.com/"
response = requests.get(url)

# Check if request successful
if response.status_code == 200:
    print("Website successfully fetched!")
else:
    print(f"Failed to fetch website. Status code: {response.status_code}")

# HTML parse karna
soup = BeautifulSoup(response.text, 'html.parser')
# # 'html.parser' built-in parser hai

# Saare book titles nikalna
book_titles = soup.find_all('h3')
# # Saare <h3> tags dhundh liye

print("\nBook Titles:")
for i, title in enumerate(book_titles[:5], 1):
    # Text extract karna
    book_name = title.a['title']
    print(f"{i}. {book_name}")

# Price nikalna
prices = soup.find_all('p', class_='price_color')
# # class_='price_color' wale <p> tags dhundho

print("\nPrices:")
for price in prices[:5]:
    print(price.text)

# Advanced: Specific element dhundhna
first_book = soup.find('article', class_='product_pod')
if first_book:
    title = first_book.h3.a['title']
    price = first_book.find('p', class_='price_color').text
    print(f"\nFirst Book: {title} - {price}")

# All links nikalna
links = soup.find_all('a')
print(f"\nTotal links on page: {len(links)}")

# Real-world example: Scraping with error handling
def scrape_books(url):
    try:
        response = requests.get(url, timeout=10)
        response.raise_for_status()  # Raise error for bad status
        
        soup = BeautifulSoup(response.text, 'html.parser')
        books = []
        
        for article in soup.find_all('article', class_='product_pod'):
            title = article.h3.a['title']
            price = article.find('p', class_='price_color').text
            books.append({'title': title, 'price': price})
        
        return books
    
    except requests.exceptions.RequestException as e:
        print(f"Error fetching data: {e}")
        return []

# Testing
scraped_books = scrape_books("https://books.toscrape.com/")
print(f"\nScraped {len(scraped_books)} books successfully!")
```

### Common Mistakes
1. **Website ka robots.txt check na karna**: Hamesha `/robots.txt` check karo ki scraping allowed hai ya nahi.
2. **Rate limiting**: Bahot tezi se requests mat bhejo, warna IP ban ho sakti hai. `time.sleep()` use karo.
3. **HTML structure change**: Websites apna structure change kar sakti hain, isliye error handling zaroori hai.

### Interview Notes
1. **Legal aspects**: Always check `robots.txt` and terms of service before scraping.
2. **Alternatives**: Some websites offer official APIs - prefer those over scraping.

### Practice Questions
**Easy:**
1. Scrape all headings (h1, h2, h3) from any news website.

**Medium:**
1. Scrape product names and prices from an e-commerce demo site.

**Hard:**
1. Build a scraper that paginates through multiple pages and saves data to CSV.

---

## 8. Testing with pytest

### Simple Explanation (Hinglish)
Code likhna kaafi nahi, yeh ensure karna bhi zaroori hai ki code sahi kaam kar raha hai. **Testing** se hum automatically check kar sakte hain ki hamara code break to nahi ho raha. **pytest** Python ka most popular testing framework hai.

### Theory (Clear + Structured)
- **Unit Testing**: Testing individual functions/components in isolation.
- **Test Cases**: Specific scenarios to test (normal input, edge cases, errors).
- **Assertions**: Statements that check if a condition is true.
- **Fixtures**: Reusable setup code for tests.

### Examples with Hinglish Comments

```python
# Pehle install karo: pip install pytest

# File: calculator.py
def add(a, b):
    return a + b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero!")
    return a / b

def is_even(n):
    return n % 2 == 0

# File: test_calculator.py (TEST FILE)
import pytest
from calculator import add, divide, is_even

# Test functions must start with 'test_'
def test_add_positive_numbers():
    assert add(2, 3) == 5
    # # Check karo ki 2+3=5 hai

def test_add_negative_numbers():
    assert add(-1, -1) == -2

def test_add_mixed_numbers():
    assert add(-1, 1) == 0

def test_divide_normal():
    assert divide(10, 2) == 5

def test_divide_by_zero():
    # # Check karo ki error raise ho raha hai
    with pytest.raises(ValueError):
        divide(10, 0)

def test_is_even():
    assert is_even(4) == True
    assert is_even(7) == False

# Parametrized tests (ek test multiple inputs ke liye)
@pytest.mark.parametrize("a, b, expected", [
    (1, 2, 3),
    (5, 5, 10),
    (-1, 1, 0),
    (0, 0, 0),
])
def test_add_multiple_cases(a, b, expected):
    assert add(a, b) == expected
    # # Yeh test 4 baar chalega different inputs ke saath

# Fixtures - reusable setup
@pytest.fixture
def sample_data():
    return {"name": "Rahul", "age": 25}

def test_fixture_usage(sample_data):
    assert sample_data["name"] == "Rahul"
    assert sample_data["age"] == 25
```

### Running Tests
```bash
# Terminal mein run karo:
pytest
# # Saare tests run ho jayenge

pytest -v
# # Verbose mode - detailed output

pytest test_calculator.py::test_add_positive_numbers
# # Sirf ek specific test run karo

pytest --cov=calculator
# # Code coverage dekho (kitna code test ho raha hai)
```

### Common Mistakes
1. **Tests na likhna**: Production code mein kam se kam 70-80% code covered hona chahiye tests se.
2. **Complex tests**: Tests simple aur readable hone chahiye.
3. **Testing implementation instead of behavior**: Test karo ki function kya karta hai, na ki kaise karta hai.

### Interview Notes
1. **TDD (Test Driven Development)**: Pehle test likho, fir code likho jo test pass kare.
2. **CI/CD**: Tests automatically run hote hain jab code push karte ho (GitHub Actions, Jenkins).

### Practice Questions
**Easy:**
1. Write tests for a function that checks if a number is prime.

**Medium:**
2. Create tests for a function that validates email addresses.

**Hard:**
3. Write parametrized tests for a sorting function with multiple edge cases.

---

## 9. Git & GitHub Basics

### Simple Explanation (Hinglish)
**Git** ek version control system hai jo track karta hai ki code mein kya changes hue hain. **GitHub** ek online platform hai jahan hum apna Git code store aur share karte hain. Team mein kaam karne ke liye yeh essential hai!

### Theory (Clear + Structured)
- **Repository (Repo)**: Project folder jahan Git tracking hoti hai.
- **Commit**: Ek snapshot of changes at a point in time.
- **Branch**: Parallel version of code for developing features.
- **Merge**: Combining changes from different branches.
- **Pull Request (PR)**: Request to merge changes into main branch.

### Essential Git Commands

```bash
# Initial Setup (pehli baar)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Repository initialize karna
git init
# # Current folder ko Git repo bana do

# Changes stage karna
git add .
# # Saare changes stage kar do

git add filename.py
# # Sirf ek file stage karo

# Commit karna (save karna)
git commit -m "Added login functionality"
# # Message ke saath commit karo

# Remote repository connect karna
git remote add origin https://github.com/username/repo.git
git push -u origin main
# # Code GitHub pe push karo

# Branch banana aur switch karna
git branch feature-login
# # Nayi branch banao
git checkout feature-login
# # Us branch pe switch karo
git checkout -b feature-payment
# # Branch banao aur switch karo (shortcut)

# Changes merge karna
git checkout main
git merge feature-login
# # feature-login ko main mein merge karo

# Latest changes pull karna
git pull origin main
# # GitHub se latest code lao

# Status dekhna
git status
# # Kaunsi files modified hain

git log
# # Saare commits dekho

git diff
# # Changes dekho before staging
```

### Common `.gitignore` Entries
```bash
# Python
__pycache__/
*.py[cod]
*.so
.Python
venv/
env/
.env
*.egg-info/
dist/
build/

# IDEs
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
*.log
```

### Common Mistakes
1. **Sensitive data commit karna**: `.env`, passwords, API keys kabhi commit mat karna!
2. **Chhote commits**: Har chhote change pe commit karo descriptive message ke saath.
3. **Main branch pe direct push**: Hamesha branch banao, PR bhejo, review lo, fir merge karo.

### Interview Notes
1. **Git Flow**: Popular branching strategy with main, develop, feature, release, and hotfix branches.
2. **Resolve Merge Conflicts**: Jab do log same file edit karte hain, conflicts resolve karna seekho.

### Practice Questions
**Easy:**
1. Initialize a Git repo, make a commit, and push to GitHub.

**Medium:**
1. Create a feature branch, make changes, and create a Pull Request.

**Hard:**
1. Practice resolving a merge conflict between two branches.

---

## 10. Building REST APIs with Flask

### Simple Explanation (Hinglish)
**REST API** wo interface hai jisse frontend (React, Mobile App) backend se baat karta hai. **Flask** ek lightweight Python framework hai APIs banane ke liye. JSON format mein data exchange hota hai.

### Theory (Clear + Structured)
- **HTTP Methods**: GET (read), POST (create), PUT/PATCH (update), DELETE (delete).
- **Endpoints**: URLs jahan API requests bheji jati hain.
- **JSON**: Data exchange format (JavaScript Object Notation).
- **Status Codes**: 200 (OK), 201 (Created), 400 (Bad Request), 404 (Not Found), 500 (Server Error).

### Examples with Hinglish Comments

```python
# Pehle install karo: pip install flask

from flask import Flask, request, jsonify
from datetime import datetime

app = Flask(__name__)

# In-memory database (temporary storage)
users = [
    {"id": 1, "name": "Rahul", "email": "rahul@example.com"},
    {"id": 2, "name": "Priya", "email": "priya@example.com"}
]

# Root endpoint
@app.route('/')
def home():
    return jsonify({"message": "Welcome to the API!"})
    # # JSON response bhejo

# GET - Saare users fetch karna
@app.route('/users', methods=['GET'])
def get_users():
    return jsonify({
        "success": True,
        "count": len(users),
        "data": users
    }), 200
    # # 200 status code ke saath response

# GET - Ek user fetch karna
@app.route('/users/<int:user_id>', methods=['GET'])
def get_user(user_id):
    user = next((u for u in users if u['id'] == user_id), None)
    
    if user is None:
        return jsonify({"error": "User not found"}), 404
        # # 404 agar user na mile
    
    return jsonify({"success": True, "data": user}), 200

# POST - Naya user banana
@app.route('/users', methods=['POST'])
def create_user():
    data = request.get_json()
    # # Request body se JSON data nikalo
    
    # Validation
    if not data or 'name' not in data or 'email' not in data:
        return jsonify({"error": "Name and email are required"}), 400
    
    # New user create karna
    new_user = {
        "id": len(users) + 1,
        "name": data['name'],
        "email": data['email'],
        "created_at": datetime.now().isoformat()
    }
    
    users.append(new_user)
    
    return jsonify({
        "success": True,
        "message": "User created successfully",
        "data": new_user
    }), 201
    # # 201 Created status code

# PUT - User update karna
@app.route('/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    user = next((u for u in users if u['id'] == user_id), None)
    
    if user is None:
        return jsonify({"error": "User not found"}), 404
    
    data = request.get_json()
    
    # Update fields
    if 'name' in data:
        user['name'] = data['name']
    if 'email' in data:
        user['email'] = data['email']
    
    return jsonify({
        "success": True,
        "message": "User updated",
        "data": user
    }), 200

# DELETE - User delete karna
@app.route('/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    global users
    user = next((u for u in users if u['id'] == user_id), None)
    
    if user is None:
        return jsonify({"error": "User not found"}), 404
    
    users = [u for u in users if u['id'] != user_id]
    
    return jsonify({
        "success": True,
        "message": "User deleted successfully"
    }), 200

# Error handlers
@app.errorhandler(404)
def not_found(error):
    return jsonify({"error": "Endpoint not found"}), 404

@app.errorhandler(500)
def internal_error(error):
    return jsonify({"error": "Internal server error"}), 500

# Run the server
if __name__ == '__main__':
    app.run(debug=True, port=5000)
    # # debug=True se auto-reload hota hai changes pe
```

### Testing API with curl
```bash
# Saare users fetch karo
curl http://localhost:5000/users

# Ek user fetch karo
curl http://localhost:5000/users/1

# Naya user banao
curl -X POST http://localhost:5000/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Aman", "email": "aman@example.com"}'

# User update karo
curl -X PUT http://localhost:5000/users/1 \
  -H "Content-Type: application/json" \
  -d '{"name": "Rahul Kumar"}'

# User delete karo
curl -X DELETE http://localhost:5000/users/1
```

### Common Mistakes
1. **Validation na karna**: User input ko hamesha validate karo.
2. **Error handling na karna**: Proper error messages aur status codes bhejo.
3. **Sensitive data expose karna**: Passwords aur sensitive info response mein mat bhejo.

### Interview Notes
1. **REST Principles**: Statelessness, Client-Server architecture, Uniform Interface.
2. **Authentication**: JWT tokens, OAuth, API keys for securing endpoints.

### Practice Questions
**Easy:**
1. Create a simple API with one endpoint that returns "Hello World".

**Medium:**
1. Build a CRUD API for a "Products" resource with name, price, and description.

**Hard:**
1. Add authentication to your API using JWT tokens.

---

## Career Roadmap & Next Steps

### What You've Learned So Far:
✅ Python Basics (Variables, Data Types, Operators)
✅ Control Flow (If-Else, Loops)
✅ Data Structures (Lists, Tuples, Sets, Dictionaries)
✅ Functions (Arguments, Recursion, Lambda)
✅ OOP (Classes, Objects, Inheritance, Polymorphism)
✅ File Handling & Exception Handling
✅ Modules & Packages
✅ Advanced Python (Decorators, Generators, Context Managers)
✅ Regular Expressions
✅ DSA Basics (Arrays, Stacks, Queues, Linked Lists, Trees)
✅ Libraries (NumPy, Pandas, Requests)
✅ **NEW**: Virtual Environments & Type Hinting
✅ **NEW**: Logging & Debugging
✅ **NEW**: Database Integration (SQLite)
✅ **NEW**: AsyncIO Basics
✅ **NEW**: Environment Variables & Security
✅ **NEW**: Web Scraping
✅ **NEW**: Testing with pytest
✅ **NEW**: Git & GitHub
✅ **NEW**: Building REST APIs

### Next Steps for Backend Development:

1. **Learn a Web Framework**:
   - **Flask** (Lightweight, beginner-friendly)
   - **Django** (Full-featured, batteries-included)
   - **FastAPI** (Modern, async support, auto-docs)

2. **Database Mastery**:
   - PostgreSQL or MySQL (Production databases)
   - SQLAlchemy (ORM for Python)
   - Database design & normalization

3. **Authentication & Authorization**:
   - JWT Tokens
   - OAuth 2.0
   - Session management

4. **Deployment**:
   - Docker & Containerization
   - Cloud platforms (AWS, GCP, Azure)
   - CI/CD pipelines

5. **System Design Basics**:
   - Load balancing
   - Caching (Redis)
   - Message queues (RabbitMQ, Kafka)

### Project Ideas for Your Portfolio:

1. **E-commerce API**: Full CRUD with authentication, cart, orders
2. **Blog Platform**: Users, posts, comments, likes
3. **Task Management App**: Like Trello clone
4. **Weather Dashboard**: Fetch from API, display with charts
5. **Real-time Chat**: Using WebSockets
6. **URL Shortener**: Like bit.ly clone
7. **Expense Tracker**: With data visualization
8. **Job Board**: Post jobs, apply, filter

### Final Advice:
- **Build Projects**: Theory se zyada practical kaam aata hai
- **Contribute to Open Source**: GitHub pe active raho
- **Practice DSA**: LeetCode, HackerRank pe regular practice
- **Network**: LinkedIn pe connect karo, tech meetups attend karo
- **Keep Learning**: Technology roz badalti hai, updated raho

---

> **Congratulations!** 🎉  
> Ab aapke paas ek complete Python + Backend Development roadmap hai.  
> **Yaad rakhna**: Consistency is key. Roz thoda thoda code karo, projects banao, aur kabhi mat rukna!  
> **Happy Coding!** 🚀
