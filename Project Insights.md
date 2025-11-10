YouTube Learning Pathway Creator

A data-driven tool that transforms chaotic YouTube search results into a structured, high-quality learning path.

The Problem

YouTube is one of the world's largest learning platforms, but it was not designed for structured education. For anyone trying to learn a new, complex topic (like "Data Science" or "3D Modeling"), the experience is chaotic. A single search returns thousands of videos, leaving the learner with critical, unanswered questions:

Where do I start? Is the video with 10 million views the right one for a beginner?

What comes next? How do videos relate to each other?

Is this video even good? View counts and likes can be misleading. How can I gauge the quality of the content without watching hours of it?

Manually curating a learning path from this noise is time-consuming, frustrating, and a significant barrier to learning.

The Solution

This project solves the problem by automating the creation of an intelligent learning pathway. This tool ingests a user's topic query (e.g., "Python for beginners") and leverages the YouTube API, natural language processing (NLP), and graph theory to produce a curated, sequenced list of videos.

It functions as an intelligent curator, analyzing not just basic statistics but also the content of the videos and the sentiment of the community to build a path that is both logical and high-quality.

Key Features

Automated Video Curation: Fetches a wide range of videos related to a topic using the YouTube v3 API.

Sentiment-Based Quality Scoring: Moves beyond simple like/dislike ratios by applying nltk's VADER (Valence Aware Dictionary and sEntiment Reasoner) to video comments. This generates a sentiment score that acts as a powerful proxy for community-vetted video quality.

Graph-Based Sequencing: Models the video ecosystem as a directed graph using the networkx library.

Nodes: Represent individual videos, weighted by their sentiment score and view counts.

Edges: Represent topical relationships, calculated by analyzing shared keywords between video titles and descriptions.

Learning Path Visualization: Generates a matplotlib visualization of the video graph, allowing a user to see the recommended sequence and how different sub-topics connect.

Tech Stack

Data Collection: Google API Python Client (for YouTube v3 API)

Data Manipulation: Pandas, NumPy

NLP & Sentiment Analysis: NLTK (VADER)

Graph Modeling: NetworkX

Data Visualization: Matplotlib

Utility: isodate (for parsing video durations), re (for text cleaning)

Key Insights & Analysis

Building this project revealed several insights that simple YouTube browsing hides:

View Count is Not a Quality Metric: The analysis consistently showed a weak correlation between a video's total view count and its community sentiment score. Several high-view "crash courses" had significantly lower sentiment scores than shorter, more focused introductory videos, which the community praised for their clarity.

The "Topical Gap" is Real: The networkx graph visualization often revealed "topical gaps"—key sub-topics that are necessary to bridge two advanced concepts but are not immediately obvious from a standard search. The tool was able to identify these "bridge" videos (e.g., "Understanding Pandas DataFrames") as critical prerequisites for more advanced topics (e.g., "Kaggle Project Walkthrough").

Sentiment Reveals User Pain Points: Analyzing negative comments for high-view videos was insightful. Common themes included "too fast for beginners," "skips important steps," or "outdated information." This data reinforces the need for a quality filter that this tool provides.

Challenges & Future Improvements

Challenge: The YouTube API has a strict quota system, which made fetching comments for a large set of videos slow and resource-intensive. This was managed by implementing request batching and caching API responses.

Challenge: Defining a "topical relationship" from just titles and descriptions was difficult. The initial keyword-matching algorithm created too many weak connections. This was improved by weighting keywords based on their rarity (TF-IDF-like logic) to strengthen meaningful connections.

Future Work:

Transcript Analysis: Integrate NLP on video transcripts (where available) for a much richer keyword and topic-modeling dataset.

Interactive UI: Build a simple web-based front-end (e.g., using Streamlit or Flask) to make the tool interactive for any user.

Path Pruning: Implement more advanced graph algorithms (e.g., finding the shortest path from an "intro" node to an "advanced" node) to recommend a single, optimized learning track instead of just visualizing the whole network.
