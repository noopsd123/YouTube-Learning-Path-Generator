# 🎓 YouTube Learning Path Generator

> **Stop drowning in search results. Start learning with a plan.**

YouTube has 800 million videos — but zero structure. This tool uses the **YouTube v3 API**, **NLP sentiment analysis**, and **graph theory** to automatically curate and sequence a personalized learning path from any topic you throw at it.

> *"The goal isn't to watch more YouTube. It's to waste less time and actually learn."*

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![YouTube API](https://img.shields.io/badge/YouTube-v3%20API-FF0000?logo=youtube&logoColor=white)](https://developers.google.com/youtube/v3)
[![NLTK](https://img.shields.io/badge/NLP-NLTK%20VADER-green)](https://www.nltk.org/)
[![NetworkX](https://img.shields.io/badge/Graph-NetworkX-blue)](https://networkx.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🧩 The Problem

Search "Data Science" on YouTube. You get 10 million results.

- The most-viewed video may be 5 years old and teach deprecated syntax
- You have no idea which video comes *before* which
- Likes and views tell you nothing about whether a *beginner* can actually follow it
- You spend 2 hours deciding what to watch instead of actually learning

This is the **YouTube learning trap**: a platform built for entertainment masquerading as an education tool.

---

## 💡 The Solution

This project acts as an **intelligent learning curator**. You give it a topic. It gives you a sequenced, quality-scored, community-vetted learning path.

Under the hood, it:
1. Fetches relevant videos using the YouTube v3 API
2. Scores each video by **community sentiment** (not just likes)
3. Detects **topical relationships** between videos using NLP keyword analysis
4. Builds a **directed graph** to model prerequisite-to-advanced progressions
5. Outputs a **visual learning path** you can actually follow

---

## ⚙️ How It Works

```
User Topic Query
      │
      ▼
 YouTube v3 API ──► Fetch videos, metadata, comments
      │
      ▼
 NLTK VADER ──────► Sentiment score per video (community quality signal)
      │
      ▼
 TF-IDF Keywords ──► Extract meaningful keywords from titles + descriptions
      │
      ▼
 NetworkX Graph ──► Build nodes (videos) + edges (topical relationships)
      │
      ▼
 Matplotlib ──────► Visualize learning path as a directed graph
```

---

## ✨ Key Features

| Feature | What It Does |
|---|---|
| 🔍 **Automated Video Curation** | Pulls a wide pool of videos for any topic via YouTube v3 API |
| 💬 **Sentiment-Based Scoring** | Uses VADER on real comments to score community-approved quality |
| 🕸️ **Graph-Based Sequencing** | Models video relationships with NetworkX — nodes are videos, edges are topical links |
| 📊 **Visual Learning Path** | Renders a Matplotlib graph showing sequence and sub-topic connections |
| 🧹 **Smart Filtering** | Downweights videos with poor sentiment even if they have high view counts |

---

## 🛠️ Tech Stack

```
Data Collection   → Google API Python Client (YouTube v3)
Data Wrangling    → Pandas, NumPy
NLP & Sentiment   → NLTK (VADER Sentiment Analyzer)
Graph Modeling    → NetworkX
Visualization     → Matplotlib
Utilities         → isodate (duration parsing), re (text cleaning)
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- A [YouTube Data v3 API key](https://console.cloud.google.com/)

### Installation

```bash
# Clone the repo
git clone https://github.com/noopsd123/YouTube-Learning-Path-Generator.git
cd YouTube-Learning-Path-Generator

# Install dependencies
pip install google-api-python-client pandas numpy nltk networkx matplotlib isodate

# Download NLTK data
python -c "import nltk; nltk.download('vader_lexicon')"
```

### Usage

1. Open `YouTube_Learning_Pathway_Creator.ipynb` in **Google Colab** or **Jupyter Notebook**
2. Add your YouTube v3 API key where prompted
3. Set your topic query (e.g., `"Python for beginners"`, `"Machine Learning"`, `"3D Modeling"`)
4. Run all cells
5. Get your structured, sentiment-scored learning path graph

---

## 📊 Key Insights From Building This

This project challenged assumptions you'd never question just browsing YouTube:

**1. View count ≠ quality**
High-view "crash courses" consistently scored *lower* in community sentiment than shorter, more focused videos. Learners praised clarity over breadth.

**2. The Topical Gap is real**
The graph visualization surfaced "bridge" videos — content covering prerequisite sub-topics (e.g., *"Understanding Pandas DataFrames"*) that appear nowhere in a standard search but are critical stepping stones to advanced material.

**3. Negative comments are gold**
Analyzing negative sentiment revealed recurring learner pain points: *"too fast for beginners," "skips important steps," "outdated syntax."* These are exactly the signals a star-rating system misses.

---

## 🔭 Roadmap

- [ ] **Transcript Analysis** — Run NLP on video transcripts for richer topic modeling
- [ ] **Streamlit UI** — Interactive web app so any user can generate a path without touching code
- [ ] **Shortest Path Optimization** — Use graph algorithms to recommend a single, pruned learning track (beginner → advanced)
- [ ] **Multi-language Support** — Extend sentiment analysis beyond English comments
- [ ] **Export Options** — Save your learning path as PDF or Notion-ready checklist

---

## 📁 Repository Structure

```
YouTube-Learning-Path-Generator/
├── YouTube_Learning_Pathway_Creator.ipynb  # Main notebook — run this
├── Project Insights.md                      # Deep-dive into methodology & findings
└── README.md
```


---

## 🙋‍♀️ Author

**Noopur Shekhar Divekar** — Data Science @ Indiana University  
[LinkedIn](https://www.linkedin.com/in/noopurd) · [GitHub](https://github.com/noopsd123)

---


