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
