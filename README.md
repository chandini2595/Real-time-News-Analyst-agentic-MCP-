# Real-time-News-Analyst-agentic-MCP

## Purpose of the Project

The primary purpose of this project is to develop an autonomous, multi-agent system that can continuously monitor, analyze, and summarize live news data from multiple sources to provide timely and accurate insights for decision-makers.

In today’s information-driven environment, traditional news aggregation systems only collect and display headlines without offering meaningful context or analysis. This project aims to bridge that gap by leveraging Agentic AI and the Model Context Protocol (MCP) to create a network of intelligent agents capable of reasoning over real-time data.

## Objectives

1.	Develop a Real-Time News Retrieval Framework
2.	Design and Implement Multiple Specialized Agents
3.	Automate News Classification and Summarization
4.	Enable Contextual Querying through MCP
5.	Ensure Data Reliability and Explainability
6.	Deliver Actionable Intelligence and Alerts

## Architecture

<img width="621" height="694" alt="image" src="https://github.com/user-attachments/assets/8d1653cf-ec9f-45e1-95a3-fea1a16ea43b" />

### Overview

The Real-Time News Analyst Agent system is built using a multi-agent architecture, leveraging the Model Context Protocol (MCP) to allow AI agents to query, reason over, and act upon real-time information. The system is designed for continuous ingestion, intelligent analysis, and actionable output based on live news data.

**1. Data Sources:** The system pulls data from diverse, real-time public sources:
- RSS Feeds from major media outlets (e.g., BBC, Reuters)
- Reddit via subreddit APIs for community trends
- Twitter (X) for real-time events and public sentiment
- Google News for aggregated mainstream headlines

**2. Ingestion Agent:** A centralized Ingestion Agent collects and normalizes data from all sources. It:
- Fetches and parses raw content
- Deduplicates and timestamps entries
- Extracts basic metadata (title, summary, source)
- Stores cleaned data in a structured database

**3. Events Database (PostgreSQL):** All normalized news items are saved in a relational database:
- Each item includes fields such as title, url, published_at, topics, entities, sector, and summary
- Supports queries for latest items, trend analysis, and comparisons (e.g., 24-hour changes)

**4. MCP Server:** The Model Context Protocol (MCP) server acts as the middleware between the data and the agents. It exposes:
- Resources (e.g., latest.json, diff_24h.json) that agents can query
- Tools (e.g., fetch_latest(), summarize(), classify(), alert()) that agents can call for reasoning and actions
- Prompts to ensure structured responses and reduce hallucinations

**5. Specialist Agents:**
Domain-specific agents each focus on a category of news:
- Finance Agent → markets, companies, earnings, economic indicators
- Geopolitics Agent → international relations, trade policy, security issues
- Social Media Agent → trending posts, community opinions, public sentiment

Each agent:
- Uses MCP tools to fetch and analyze relevant data
- Classifies and summarizes news items
- Returns structured insights to the coordinator

**6. Coordinator Agent:** The Coordinator Agent orchestrates the entire process. It:
- Queries MCP resources for real-time data (e.g., what changed in 24h)
- Delegates analysis tasks to domain experts (specialist agents)
- Merges their reports into a unified summary or alert
- Ensures responses are source-cited, timestamped, and readable

**7. Output Layer:**
a. Chat System
- Lets users interact via natural language questions
- Example: “What’s trending in the AI sector today?”

b. Insight Dashboard
- Displays summarized events by topic or sector
- Designed for decision-makers and analysts

c. Alert System
- Triggers notifications (e.g., Slack, email, webhook) based on predefined rules
- Useful for rapid response to significant news (e.g., policy changes, company earnings shocks)
