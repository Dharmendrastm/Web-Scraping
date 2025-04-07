# 🔧 Python Libraries for Web Scraping (Basic to Advanced)

| 📦 Library Name     | 📄 Kaam Kya Hai? |
|----------------------|------------------|
| `requests`           | Webpage ka HTML content fetch karta hai |
| `beautifulsoup4`     | HTML ko parse karke data extract karne me help karta hai |
| `lxml` *(optional)*  | Fast HTML parser (BeautifulSoup ke sath use hota hai) |
| `csv`                | Data ko CSV file me save karne ke liye |
| `pandas` *(optional)*| Data ko clean aur save karne ke liye (advanced analysis) |
| `scrapy`             | Ek powerful scraping framework (large scale projects ke liye) |
| `selenium`           | JavaScript-heavy pages ko scrape karne ke liye (browser automation) |
| `fake_useragent`     | Request headers me fake user-agent lagane ke liye |
| `time` / `random`    | Request me delay dene ke liye (site block na kare isliye) |

---

### ✅ Beginner ke liye Required:

Bas yeh 3 kaafi hain:
```bash
pip install requests beautifulsoup4 lxml
```

Aur agar tu data file me store karega:
```python
import csv  # (built-in hota hai, install nahi karna)
```

---

### 🔥 Advanced ke liye (jab tu pro ban jaaye):
- `scrapy` → for full websites
- `selenium` → for login/scroll wala data
- `pandas` → for data cleaning / exporting Excel

---

### 💡 Tip:
Tu shuru me `requests + BeautifulSoup` se hi kaam kare — 90% sites scrape ho jaati hain inhi se ✅


Bhai, ekdum sahi demand hai! 💯  
Main tujhe har **popular web scraping library** ka **basic example code** de raha hoon — taaki tujhe samajh aa jaye ki kaise kaam karta hai ✅

---

## 💻 1. `requests` + `beautifulsoup4`  
➡️ Most used combo for simple web scraping

```python
import requests
from bs4 import BeautifulSoup

url = "https://quotes.toscrape.com/"
res = requests.get(url)
soup = BeautifulSoup(res.text, "html.parser")

print("Page Title:", soup.title.string)

# First quote and author
quote = soup.find("span", class_="text").text
author = soup.find("small", class_="author").text
print(f"{quote} — {author}")
```

---

## 💻 2. `csv` (file me data save karne ke liye)

```python
import csv

data = [["Name", "Age"], ["Dharmendra", 21], ["Amit", 23]]

with open("data.csv", "w", newline="", encoding="utf-8") as f:
    writer = csv.writer(f)
    writer.writerows(data)

print("CSV file saved ✅")
```

---

## 💻 3. `lxml` (BeautifulSoup ke sath fast parsing)

```python
from bs4 import BeautifulSoup
import requests

res = requests.get("https://quotes.toscrape.com/")
soup = BeautifulSoup(res.text, "lxml")  # use "lxml" instead of "html.parser"

print("Title:", soup.title.string)
```

---

## 💻 4. `pandas` (data analysis + saving Excel/CSV)

```python
import pandas as pd

data = {
    "Name": ["Dharmendra", "Amit"],
    "Age": [21, 23]
}

df = pd.DataFrame(data)
df.to_csv("people.csv", index=False)
print("Saved using pandas ✅")
```

---

## 💻 5. `fake_useragent` (Anti-blocking technique)

```python
import requests
from fake_useragent import UserAgent

ua = UserAgent()
headers = {'User-Agent': ua.random}

res = requests.get("https://httpbin.org/headers", headers=headers)
print(res.text)
```

---

## 💻 6. `time` & `random` (delay add karne ke liye)

```python
import time
import random

for i in range(5):
    print(f"Scraping page {i+1}...")
    time.sleep(random.uniform(1, 3))  # wait 1-3 seconds randomly
```

---

## 💻 7. `selenium` (dynamic JavaScript pages ke liye)

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from bs4 import BeautifulSoup

driver = webdriver.Chrome()
driver.get("https://quotes.toscrape.com/js/")

soup = BeautifulSoup(driver.page_source, "html.parser")
print("Title:", soup.title.string)

driver.quit()
```

> **Note:** Selenium ke liye ChromeDriver install hona chahiye. (Main help kar dunga agar chahiye)

---

## 💻 8. `scrapy` (big project framework)

```bash
scrapy startproject myproject
cd myproject
scrapy genspider quotes quotes.toscrape.com
```

```python
# quotes.py spider file me likhna hota hai
import scrapy

class QuotesSpider(scrapy.Spider):
    name = "quotes"
    start_urls = ['https://quotes.toscrape.com']

    def parse(self, response):
        for quote in response.css('div.quote'):
            yield {
                'text': quote.css('span.text::text').get(),
                'author': quote.css('small.author::text').get(),
                'tags': quote.css('div.tags a.tag::text').getall(),
            }
```

Run with:
```bash
scrapy crawl quotes -o quotes.json
```

---

## 🔚 Summary Table:

| Library         | Use Case                    |
|----------------|-----------------------------|
| `requests`      | Webpage se HTML lena        |
| `bs4` (BeautifulSoup) | HTML ko parse karna         |
| `csv`           | File me save karna          |
| `pandas`        | Table data handle karna     |
| `selenium`      | JavaScript pages scrape     |
| `scrapy`        | Big website scrape project  |
| `fake_useragent`| Fake headers bhejna         |
| `time/random`   | Delay lagana (anti-block)   |

---

