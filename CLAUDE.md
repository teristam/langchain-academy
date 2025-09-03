# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

LangChain Academy is an educational repository containing modules focused on foundational concepts within the LangChain ecosystem, with modules 1-6 focusing on LangGraph. The project uses Python 3.11+ and contains Jupyter notebooks for interactive learning, along with LangGraph Studio files for testing and visualization.

## Environment Setup

Python requirements: >= 3.11 (specified in pyproject.toml, though README mentions Python 3.13)

Required API keys in environment:
- `OPENAI_API_KEY` - OpenAI API access
- `LANGSMITH_API_KEY` - LangSmith tracing  
- `LANGSMITH_TRACING_V2=true`
- `LANGSMITH_PROJECT="langchain-academy"`
- `TAVILY_API_KEY` - Web search API (used in Module 4)

## Development Commands

### Setup
```bash
python3 -m venv lc-academy-env
source lc-academy-env/bin/activate  # or lc-academy-env\scripts\activate on Windows
pip install -r requirements.txt
```

### Running Notebooks
```bash
jupyter notebook
```

### LangGraph Studio Development
Navigate to any `module-x/studio/` directory and run:
```bash
langgraph dev
```
This starts the development server at:
- API: http://127.0.0.1:2024
- Studio UI: https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024
- API Docs: http://127.0.0.1:2024/docs

Each studio directory needs a `.env` file with API keys. Use the `.env.example` as a template.

## Project Architecture

### Module Structure
- **module-0**: Basic setup and fundamentals
- **module-1**: LangGraph basics (simple graphs, chains, routers, agents)
- **module-2**: State management (schemas, reducers, memory, message handling)  
- **module-3**: Human-in-the-loop (breakpoints, streaming, time travel)
- **module-4**: Advanced patterns (parallelization, map-reduce, sub-graphs, research assistant)
- **module-5**: Memory systems (stores, schemas, collections, profiles)
- **module-6**: Assistant patterns (creation, connection, double-texting)

### Key Components per Module
Each module contains:
- **Jupyter notebooks** (`.ipynb`) - Interactive tutorials and exercises
- **studio/** subdirectory - LangGraph Studio files for visualization/testing
  - `langgraph.json` - Graph configuration
  - Python files (e.g., `simple.py`, `router.py`, `agent.py`) - Graph implementations
  - `.env.example` - Environment variable template

### Core Dependencies
- **LangGraph**: Core graph framework and prebuilt components
- **LangChain**: Community tools, core abstractions, OpenAI integration
- **LangSmith**: Tracing and monitoring
- **Tavily**: Web search integration
- **SQLite**: Checkpoint storage for LangGraph
- **Jupyter**: Interactive notebook environment

## Working with the Codebase

### Studio Graphs
Each module's studio directory contains graph implementations that can be run via LangGraph Studio. The `langgraph.json` file defines which graphs are available and their entry points.

### Notebook Development  
Notebooks are the primary learning interface. They contain progressive exercises building from basic concepts to advanced implementations. Many reference corresponding studio graphs for hands-on testing.

### Environment Files
Create `.env` files in studio directories using the pattern:
```bash
cp module-X/studio/.env.example module-X/studio/.env
# Then add your API keys
```