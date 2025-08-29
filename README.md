# Commodity-news-digest2
This is a ready-to-run GitHub repo for a “Morning Commodity News” tool
commodity-news-digest/
├── .github/
│   └── workflows/
│       └── daily.yml          # GitHub Actions workflow (07:00 SGT)
├── config/
│   ├── taxonomy.yaml          # commodities / themes / geographies
│   ├── sources.yaml           # RSS & GDELT feeds
│   └── settings.yaml          # timezone, thresholds, secrets placeholders
├── data/                      # SQLite DB + daily CSVs will land here
├── src/
│   ├── __init__.py
│   ├── ingest_rss.py          # fetch RSS & GDELT feeds
│   ├── parse_article.py       # extract article text
│   ├── nlp.py                 # AI analysis: relevance, tags, sentiment, summary
│   ├── ranker.py              # scoring + deduplication
│   ├── output.py              # save DB, export CSV, send Slack/Email
│   └── run.py                 # main entrypoint
├── requirements.txt
├── README.md
└── .gitignore

# Commodity News Digest

Automated daily AI-powered digest of commodity-related news.

## Features
- Fetches RSS & official feeds
- Extracts & cleans article text
- Uses AI (zero-shot, embeddings, FinBERT, summarization) to tag & score relevance
- Deduplicates, summarizes, ranks
- Persists results in SQLite & CSV
- Sends top headlines to Slack daily at 07:00 SGT

## Setup
1. Clone repo
2. `pip install -r requirements.txt`
3. `python -m spacy download en_core_web_sm`
4. Add feeds in `config/sources.yaml`
5. Add Slack webhook URL in `config/settings.yaml` or as GitHub secret

## Run locally
```bash
python src/run.py
