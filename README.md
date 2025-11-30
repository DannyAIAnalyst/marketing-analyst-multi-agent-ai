## **Project Overview - Marketing Insight Analyst**

This is a multi-agent AI system that automates the process for querying, analyzing, and summarizing daily/weekly insights from marketing campaign data. It uses:

- LLM-powered agents
- BigQuery ADK tools
- Memory and session management
- Multi-agent orchestration
- Automatic summarization workflows

### **Problem Statement:**

Large organizations that run multiple marketing campaigns often encounter challenges with interpreting their data. Extracting meaningful insights from top level campaign metrics like CTR (clickthrough rate), CPL (cost-per-lead), ROI (return on ad investment), AOV (average campaign order value), cost efficiency - requires manual SQL writing, repetitive data exploration, analysis, and summarization of key take aways.

This creates a few friction points:

1. Non-technical teams cannot self-serve insights.
2. Writing SQL queries could become repetitive across multiple campaigns/projects.
3. Insights varying across teams depending on who performs the analysis and when, due to varying techniques, processes, and measurement criteria.
4. Memory of past queries and context is easily lost.

Marketing teams need a natural-language interface to their performance data—one that is accurate, structured, consistent, and available on demand.


### **Why agents?** 

A single LLM is not reliable for end-to-end analytics. This multi-agent workflow creates separation of responsibility:

|**Agent**|**Responsibility**|
| --- | --- |
|**InsightAgent**|SQL generation, BigQuery execution, pipeline orchestration|
|**SummarizerAgent**|High-quality insight reporting|


This guarantees:

- Structured SQL output
- Accurate data extraction
- Clear separation between “data retrieval” and “insight interpretation”

Using agents eliminates hallucinations, ensures reproducibility, and enables tool calling and workflow orchestration that a single prompt cannot achieve.

This marketing campaign Insight Analyst is a multi-agent AI system that converts natural language questions into BigQuery queries, executes them safely, analyzes the results, and returns executive-ready summaries.


The system uses:

1. InsightAgent: An agent that generates and safely executes BigQuery SQL queries.
2. SummarizerAgent: An agent that produces structured insight reports.
3. Memory Service: An AI agent tool that stores conversation context and past analyses.
4. Sessions: Ensures stateful multi-turn conversations.
5. BigQuery Toolset: A first-party MCP toolset for BigQuery - Managed through ADK tools framework


Users can ask:

- “What were the key performance metrics for the last 7 days?”
- “Which campaign is most cost-efficient this week?”
- “Summarize overall ROI in November 2025 by channel.”


### **How it works**: 
The system automatically generates SQL based on the table schema, then it executes SQL using the BigQuery tool. The result is then passed to a second agent (SummarizerAgent) for summarization. The insight generated is stored into memory for long-term context.

**Overall Architecture Summary**


Core components:

- InsightAgent (LLM agent with BigQueryToolset and memory tools)
- SummarizerAgent (LLM agent for insight synthesis)
- InMemorySessionService: for Session tracking
- InMemoryMemoryService: acts as a long-term memory bank
- Runner: Orchestrates agent execution
- BigQueryToolset: Executes SQL queries
- Custom auto-save callback: Writes memory after each turn

-----------------------
This project is released under a Non-Commercial License. Commercial use is prohibited without explicit written permission from the author.
Contact: s.o@sesandatalab.com.
