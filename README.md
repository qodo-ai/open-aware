# Open Aware
<div align="center">
<!--   <img width="502" height="402" alt="image" src="https://github.com/user-attachments/assets/2b12403d-12eb-4c6c-ae32-e1d9fa30b2e5" /> -->
<img width="1024" height="683" alt="image" src="https://github.com/user-attachments/assets/882f5966-4fe1-4903-be32-2f2a89aff37e" />
</div>



Open Aware brings the code intelligence directly to your AI assistant through MCP. Go beyond keyword search, understand code semantically across multiple repositories with daily updated indexes. 

## Features

| Category | Open Aware | Your Agent |
|----------|------------|------------|
| 🔍 **Addvance context** | ✅ Advanced context across repositories include documentation and code | ❌ |
| 🤖 **Agentic** | ✅ Agent that searche deep in indexed code and documentation for your query | ❌ |
| 🛠️ **Aware engine** | ✅ You get access via MCP to the same features enterprise customers get | ❌ |
| 🚀 **Cross repo intelegence** | ✅ Ability to query multiple repositories | ❌ |
| 🎯 **Up to date** | ✅ We index daily all changes from the latest version for each repo | ❌ |

## Integration with MCP
Both tools are exposed through the Model Context Protocol (MCP), making them easily accessible to any MCP-compatible AI assistant or development environment.
```json
{
  "open-aware": {
    "command": "npx",
    "args": [
      "mcp-remote",
      "https://open-aware.qodo.ai/mcp/"
    ]
  }
}
```

## 🤖 Prompts

#### Example 1: Let your agent resoning to select aware tools  
```text
Use open-aware to:
<USER_PROMPT>
```

#### Example 2: Spesificlly use deep-research / get-context
```text
Use deep-research to:
<USER_PROMPT>
```
```text
Use get-context to:
<USER_PROMPT>
```

#### Example 3: Granular search per repositorie\s 
```text
Use open-aware to: 
<USER_PROMPT>
repositories = ["<ORG/REPO_NAME>", "<ORG/REPO_NAME>", ...]
```

## 🧰 Available Tools

The open-aware MCP server provides two powerful tools that can be integrated into your AI workflows:

<details>
<summary>
  <b> 🔨 **Context Retrieval** (`get_context`) </b>
</summary>
This tool performs semantic search across codebase/s to find relevant code snippets.

**Key Features:**
- **Semantic Search**: Uses vector embeddings to find conceptually similar code, not just keyword matches
- **Multi-Repository Support**: Search across multiple repositories simultaneously
- **Language Filtering**: Filter results by programming language (Python, JavaScript, TypeScript, etc.)
- **Intelligent Ranking**: Returns results ranked by relevance with configurable result limits

**Example Usage:**
```json
{
  "tool": "get_context",
  "parameters": {
    "query": "authentication middleware implementation",
    "repositories": ["backend/api", "frontend/app"],
    "language": ["python", "typescript"],
    "max_results": 10
  }
}
```
</details>



<details>
<summary>
  <b> 🔨 **Deep Research** (`deep_research`) </b>
</summary>
  
An deep context agent that can answer / plan / research complex queries about a codebase\s by analyzing code structure, patterns, and relationships.

**Key Features:**
- **Code Understanding**: Comprehends code logic, architecture, and design patterns
- **Cross-Repository Analysis**: Can analyze relationships between different parts of your codebase
- **Implementation Planning**: Helps plan new features based on existing code patterns
- **Best Practice Recommendations**: Suggests improvements based on codebase analysis
- **Architecture Insights**: Provides high-level understanding of system design

**Example Usage:**
```json
{
  "tool": "deep_research",
  "parameters": {
    "input": "How does the authentication flow work across our microservices? What security measures are in place?",
    "repositories": ["backend/api", "frontend/app"],
    "session_id": "analysis-123"
  }
}
```
</details>

## 🔬 Deep research exsamples

```text
use deep_research: 
Investigate repositories ["langchain-ai/langchain", "BerriAI/litellm"]. 
I don't know witch one to use for LLM API calling create a comparison and help me decide.
```

Research for implementation and plan - In some cases you migth be missing a feature from a repository and you like to implemnt it your self via PR for the repo / as forked version, here is exsample of feature that is missing today in flask repository, first the agent will try to make sure there is not exsisitng way to use the rewuested feature and then if not he will create a details plan of the files need to be chnage and suggest the modificayion to be added.

This shwcase need to applay research for optimal implementation need where the agent is doing the research and codebase understadning to enable ececute the chnage in a way that will not brake the code and also be alinged with how fetures current features are implemned.
```text
use deep_research:
Investigate repository ["pallets/flask"], is there capability to manage requests queue ?
If Not i like to submmit a PR for flask repo to suggest adding a queue for requests.,
therfor investigate and plan how to do it and create .md file plan for me to execute
```

## ⚠️ Disclaimer

**Important Notice**: The aware-open system indexes and analyzes publicly available code libraries and repositories. 

- **No Warranty**: All code suggestions, analysis, and recommendations are provided "AS IS" without warranty of any kind
- **Your Responsibility**: You are solely responsible for reviewing, testing, and validating any code before moving it to production
- **No Liability**: We assume no liability for any damages, security issues, or problems that may arise from using code found through this system
- **License Compliance**: Ensure you comply with the original licenses of any code you use or reference
- **Security Review**: Always perform thorough security reviews and testing before deploying any code to production environments

**Remember**: This tool is designed to assist in code discovery and analysis. Professional judgment, thorough testing, and security reviews are essential before using any code in production systems.

## :outbox_tray: Connect with Us

Join our community to get support, share feedback, and stay updated with the latest features!

[![Discord](https://img.shields.io/badge/Discord-Join%20Our%20Server-7289da?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/your-invite-link)

- 💬 **Get Help**: Ask questions and get support from our community
- 🐛 **Report Issues**: Share bugs and help us improve
- 💡 **Feature Requests**: Suggest new features and capabilities
- 🚀 **Stay Updated**: Be the first to know about new releases
- 👥 **Connect**: Meet other developers using aware-open
