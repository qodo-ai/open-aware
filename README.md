# Open Aware
<div align="center">
<!--   <img width="502" height="402" alt="image" src="https://github.com/user-attachments/assets/2b12403d-12eb-4c6c-ae32-e1d9fa30b2e5" /> -->
<img width="1024" height="683" alt="image" src="https://github.com/user-attachments/assets/882f5966-4fe1-4903-be32-2f2a89aff37e" />
</div>

Open Aware brings code intelligence directly to your AI assistant through MCP. Go beyond keyword search, understand code semantically across multiple repositories with daily updated indexes.

## 📚 Table of Contents

- [Features](#features)
- [Integration with MCP](#integration-with-mcp)
- [🤖 Prompts](#prompts)
- [🧰 Agents](#Agents)
  - [Context Retrieval](#context-retrieval-get_context)
  - [Deep Research](#deep-research-deep_research)
  - [Deep Issues](#deep-issues-issues)
- [🔬 Examples](#examples)
- [🏗️ Architecture](#️architecture)
- [⚠️ Disclaimer](#️disclaimer)
- [📤 Connect with Us](#outbox_tray-connect-with-us) 

## Features

| Category | Open Aware | Your Agent |
|----------|------------|------------|
| 🔍 **Advanced context** | ✅ Advanced context across repositories including documentation and code | ❌ |
| 🤖 **Agentic** | ✅ Agent that searches deep in indexed code and documentation for your query | ❌ |
| 🛠️ **Aware engine** | ✅ You get access via MCP to the same features enterprise customers get | ❌ |
| 🚀 **Cross-repo intelligence** | ✅ Ability to query multiple repositories | ❌ |
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

#### Example 1: Let your agent reason to select aware tools  
```text
Use open-aware to:
<USER_PROMPT>
```

#### Example 2: Specifically use deep-research / get-context
```text
Use deep-research to:
<USER_PROMPT>
```
```text
Use get-context to:
<USER_PROMPT>
```

#### Example 3: Granular search per repository/repositories 
```text
Use open-aware to: 
<USER_PROMPT>
repositories = ["<ORG/REPO_NAME>", "<ORG/REPO_NAME>", ...]
```

## 🧰 Agents

The open-aware MCP server provides two powerful tools that can be integrated into your AI workflows:

<details>
<summary>
  <b> 🔨 **Context Retrieval** (`get_context`) </b>
</summary>
This tool performs semantic search across codebase(s) to find relevant code snippets.

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
  
A deep context agent that can answer/plan/research complex queries about codebase(s) by analyzing code structure, patterns, and relationships.

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


<details>
<summary>
  <b> 🔨 **Deep Issues** (`issues`) </b>
</summary>
  
A deep issue-finding agent that accepts code diff and provides analysis of any breaking changes

**Example Usage:**
```json
{
 "tool": "issue",
 "parameters": {
   "input": [
     "@@ -10,7 +10,7 @@ router = APIRouter()",
     "",
     "-@router.get(\"/foo\")",
     "+@router.get(\"/foo/bar\")",
     " async def get_users()"
   ],
   "repositories": ["backend/api", "frontend/app"],
   "session_id": "analysis-123"
 }
}
```
</details>

## 🔬 Examples

Comparison based on code behavior: make a decision based on the implementation of the projects versus reading only the docs.
```text
use deep_research: 
Investigate repositories ["langchain-ai/langchain", "BerriAI/litellm"]. 
I don't know which one to use for LLM API calling. Create a comparison and help me decide.
```

Research for implementation and plan - In some cases you might be missing a feature from a repository and you'd like to implement it yourself via PR for the repo/as a forked version. Here is an example of a feature that is missing today in the Flask repository. First, the agent will try to make sure there is not an existing way to use the requested feature, and then if not, it will create a detailed plan of the files that need to be changed and suggest the modifications to be added.

This showcases the need to apply research for optimal implementation needs where the agent is doing the research and codebase understanding to enable execution of the change in a way that will not break the code and also be aligned with how current features are implemented.
```text
use deep_research:
Investigate repository ["pallets/flask"], is there capability to manage requests queue?
If not, I'd like to submit a PR for the Flask repo to suggest adding a queue for requests.
Therefore, investigate and plan how to do it and create a .md file plan for me to execute.
```


<details>
<summary>
  <b> More use-cases </b>
</summary>  

| Scenario | Tool | Example Query | Expected Outcome | Domain |
|----------|------|---------------|------------------|------|
| 🏛️ Understanding system architecture | `deep_research` | "Explain how our microservices communicate and what protocols they use" | Detailed explanation of service communication patterns, protocols, and data flow | 🏗️ Architecture & Design |
| 🎨 Finding design patterns | `get_context` | "singleton pattern implementation" | Code examples of singleton patterns used in the codebase | 🏗️ Architecture & Design |
| 🚨 Locating error handling patterns | `get_context` | "try catch error handling with logging" | Examples of error handling patterns with logging | 🔍 Code Discovery & Learning |
| 💰 Understanding business logic | `deep_research` | "How is pricing calculated for premium users?" | Detailed explanation of pricing logic and rules | 🔍 Code Discovery & Learning |
| 🔐 Analyzing authentication flow | `deep_research` | "Trace the complete OAuth2 authentication flow" | Step-by-step authentication process across services | 🛡️ Security & Authentication |
| ⚠️ Identifying security vulnerabilities | `issues` | [code diff with auth changes] | Potential security issues in authentication changes | 🛡️ Security & Authentication |
| ⚡ Planning feature additions | `deep_research` | "Where should we add caching for better performance?" | Strategic caching recommendations | 🚀 Feature Development |
| 🔥 Understanding error sources | `deep_research` | "What could cause a 500 error in the checkout process?" | Potential failure points and error conditions | 🐛 Debugging & Troubleshooting |
| 🔌 Planning third-party integrations | `get_context` | "stripe payment integration" | Existing integration patterns and implementations | 🔗 Integration & Migration |
| ✅ Validating best practices | `deep_research` | "Are we following REST best practices in our API design?" | Analysis of REST compliance and recommendations | 📝 Code Review & Quality |
</details>



## 🏗️ Architecture 

<div align="center">
<img width="720" height="1400" alt="image" src="https://github.com/user-attachments/assets/ff22a244-903a-49be-91e2-d5af97c31f2f" />
</div>

## ⚠️ Disclaimer

**Important Notice**: The aware-open system indexes and analyzes publicly available code libraries and repositories. 

- **No Warranty**: All code suggestions, analysis, and recommendations are provided "AS IS" without warranty of any kind
- **Your Responsibility**: You are solely responsible for reviewing, testing, and validating any code before moving it to production
- **No Liability**: We assume no liability for any damages, security issues, or problems that may arise from using code found through this system
- **License Compliance**: Ensure you comply with the original licenses of any code you use or reference
- **Security Review**: Always perform thorough security reviews and testing before deploying any code to production environments

**Remember**: This tool is designed to assist in code discovery and analysis. Professional judgment, thorough testing, and security reviews are essential before using any code in production systems.

## 📤 Connect with Us

Join our community to get support, share feedback, and stay updated with the latest features!

[![Discord](https://img.shields.io/badge/Discord-Join%20Our%20Server-7289da?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/channels/1057273017547378788/1404804854265675867)

- 💬 **Get Help**: Ask questions and get support from our community
- 🐛 **Report Issues**: Share bugs and help us improve
- 💡 **Feature Requests**: Suggest new features and capabilities
- 🚀 **Stay Updated**: Be the first to know about new releases
- 👥 **Connect**: Meet other developers using aware-open