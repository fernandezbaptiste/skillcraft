---
name: data-query
description: Run analytics queries against any database using plain English — BigQuery (bq CLI), PostgreSQL, MySQL, SQLite, or any DB with a CLI/MCP/API. Use when you need to pull metrics, analyze data, or answer business questions without writing SQL.
license: MIT
compatibility: Designed for Claude Code. Requires a database CLI (bq, psql, mysql, sqlite3) or MCP server to be configured.
metadata:
  author: rajit
  version: "1.0"
allowed-tools: Bash Read
---

Use Claude as your analytics engineer. Describe what you want to know in plain English — Claude handles the query.

## How It Works

Claude uses the database CLI, MCP server, or API directly to:
1. Understand your question
2. Write the appropriate query
3. Execute it
4. Return analyzed results in plain English + a table

You don't need to write SQL.

## Supported Interfaces

- **BigQuery**: `bq` CLI — `bq query`, `bq show`, `bq ls`
- **PostgreSQL**: `psql` CLI or pg MCP server
- **MySQL**: `mysql` CLI
- **SQLite**: `sqlite3` CLI
- **Any DB with MCP**: Use the relevant MCP server
- **REST APIs with data**: Describe the endpoint, Claude fetches + analyzes

## Usage Examples

```
"How many users signed up last week vs the week before?"
→ Claude runs: bq query 'SELECT ...' and returns the comparison

"What's our churn rate by plan tier this month?"
→ Claude writes + runs the SQL, returns a breakdown

"Which API endpoints are slowest based on our logs table?"
→ Claude queries the logs table, returns sorted results
```

## Setup (BigQuery)

Make sure `bq` CLI is authenticated:
```bash
gcloud auth application-default login
bq ls  # verify access
```

Then just ask Claude your question naturally.

## Principles

- Describe the business question, not the SQL
- Claude will ask clarifying questions if the schema is ambiguous
- For recurring queries, ask Claude to save them as a named script or dbt model
- Works best when Claude has schema context — point it at your schema files or run `bq show dataset.table` first
- This works for any database that has a CLI, MCP, or API
