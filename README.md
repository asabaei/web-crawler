# UCI Academic Web Crawler

A Python web crawler that discovers and analyzes pages across UCI's ICS, Computer Science, Informatics, and Statistics websites. Built for CS121 (Information Retrieval), based on the `spacetime-crawler4py` starter code provided by the course staff.

## Features

* **Link discovery:** Parses HTML with Beautiful Soup and lxml to extract hyperlinks.
* **URL normalization:** Resolves relative links and removes URL fragments to reduce duplicate URLs.
* **Domain and file-type filtering:** Restricts crawling to allowed UCI domains and filters out unsupported file types and known crawler-trap patterns.
* **Persistent frontier:** Uses `shelve` to track discovered and completed URLs, allowing crawl state to persist between runs.
* **Politeness:** Enforces a delay between downloads to limit request frequency.
* **Analytics:** Reports unique pages found, the longest page by word count, the top 50 frequent words, and page counts by subdomain.

## Results

| Metric                  | Result                                                  |
| ----------------------- | ------------------------------------------------------- |
| Unique pages found      | 4,200                                                   |
| Subdomains represented  | 80                                                      |
| Longest page            | [CML AI/ML page](https://cml.ics.uci.edu/category/aiml) |
| Longest page word count | 25,028                                                  |

The crawl report also records the 50 most frequent words across the collected content. The most frequent terms include `research` (9,291), `data` (8,158), `information` (7,186), `computer` (7,109), and `uci` (6,587).

## Project Structure

* `launch.py` — crawler launch script
* `scraper.py` — link extraction and URL filtering, including `scraper` and `is_valid`
* `crawler/worker.py` — downloads and processes webpages
* `crawler/frontier.py` — manages the URL queue and persistent crawl state
* `analytics.py` — calculates crawl statistics and generates the report

## Setup and Usage

Install the required dependencies:

```bash
pip install -r packages/requirements.txt
```

Configure the user agent and seed URLs in `config.ini`, then launch the crawler:

```bash
python3 launch.py
```

Make sure any required cache-server services are configured and running before starting the crawl.

## Technologies

Python · Beautiful Soup · lxml · shelve 
