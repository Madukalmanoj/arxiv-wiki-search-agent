#  LangGraph Research Agent

An agentic AI pipeline built with **LangGraph** and **Groq** that autonomously searches Arxiv, Wikipedia, and the web to answer research queries — with full tool-calling support.

---

##  How It Works

The agent uses a **stateful graph** (LangGraph) where an LLM decides which tools to call based on the user's query. It loops between reasoning and tool use until it has a complete answer.

```
START → tool_calling_llm → [tools if needed] → tool_calling_llm → END
```

---

## 🛠️ Tools Available

| Tool | Source | Use Case |
|------|--------|----------|
| `arxiv` | ArxivQueryRun | Search research papers |
| `wiki` | WikipediaQueryRun | Search Wikipedia articles |
| `tavily` | TavilySearchResults | Real-time web search |

---

##  Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/langgraph-research-agent.git
cd langgraph-research-agent
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Set up environment variables

Copy the example env file and fill in your API keys:

```bash
cp .env.example .env
```

Then edit `.env`:

```env
GROQ_API_KEY=your_groq_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here
```

### 4. Run the notebook

```bash
jupyter notebook agentdemo.ipynb
```

---

##  Requirements

```
langchain-community
langchain-core
langchain-groq
langgraph
arxiv
wikipedia
tavily-python
python-dotenv
ipython
typing-extensions
```

---

##  API Keys

| Key | Where to get it |
|-----|----------------|
| `GROQ_API_KEY` | [console.groq.com](https://console.groq.com) |
| `TAVILY_API_KEY` | [app.tavily.com](https://app.tavily.com) |

---

##  Project Structure

```
langgraph-research-agent/
├── agentdemo.ipynb     # Main notebook
├── requirements.txt    # Python dependencies
├── .env                # Your API keys (never commit this)
├── .env.example        # Template for API keys
├── .gitignore          # Ignores .env and cache files
└── README.md           # This file
```

---

##  Tech Stack

- [LangGraph](https://github.com/langchain-ai/langgraph) — Agent graph orchestration
- [LangChain](https://github.com/langchain-ai/langchain) — Tool integrations
- [Groq](https://groq.com) — Ultra-fast LLM inference (`llama-3.3-70b-versatile`)
- [Tavily](https://tavily.com) — Real-time web search API

---

##  Example Usage

```python
from langchain_core.messages import HumanMessage

messages = graph.invoke({"messages": [HumanMessage(content="1706.03762")]})
for m in messages["messages"]:
    m.pretty_print()
```

---

##  Notes

- Make sure to use model `qwen/qwen3-32b` on Groq for reliable tool calling
- Never commit your `.env` file — it's listed in `.gitignore`

---

##  License

MIT
