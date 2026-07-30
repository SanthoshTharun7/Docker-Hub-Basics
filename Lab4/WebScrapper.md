# Docker Web Scraper Assignment

## Project Structure

```text
WebScrapper/
│
├── Dockerfile
├── requirements.txt
└── scrapper.py
```

---

## requirements.txt

```text
requests
beautifulsoup4
```

---

## scrapper.py

```python
import os
import requests
from bs4 import BeautifulSoup

target_url = os.getenv("TARGET_URL", "https://example.com")

try:
    response = requests.get(target_url)
    response.raise_for_status()

    soup = BeautifulSoup(response.text, "html.parser")

    titles = soup.find_all(["h1", "h2"])

    print(f"\nScraping: {target_url}\n")

    if titles:
        for i, title in enumerate(titles, 1):
            print(f"{i}. {title.get_text(strip=True)}")
    else:
        print("No <h1> or <h2> headings found.")

except Exception as e:
    print(f"Error fetching or parsing the URL: {e}")
```

---

## Dockerfile

```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY scrapper.py .

ENV TARGET_URL=https://example.com

EXPOSE 8080

CMD ["python","scrapper.py"]
```

---

## Build Image

```bash
docker build -t webscrapper .
```

---

## Run Container

Default URL:

```bash
docker run webscrapper
```

Custom URL:

```bash
docker run -e TARGET_URL=https://example.com webscrapper
```

or

```bash
docker run -e TARGET_URL=https://en.wikipedia.org/wiki/Python_(programming_language) webscrapper
```

<img width="1920" height="990" alt="Screenshot From 2026-07-31 00-54-01" src="https://github.com/user-attachments/assets/163a1b0d-e7f1-45ab-873e-cc69f289c739" />


---

## Docker Hub

Login

```bash
docker login
```

Tag

```bash
docker tag webscrapper <your-dockerhub-username>/webscrapper:latest
```

Example

```bash
docker tag webscrapper santhoshtharun7/webscrapper:latest
```

Push

```bash
docker push santhoshtharun7/webscrapper:latest
```
