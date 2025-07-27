# aware-open
<div align="center">
  <img width="502" height="402" alt="image" src="https://github.com/user-attachments/assets/2b12403d-12eb-4c6c-ae32-e1d9fa30b2e5" />
</div>

## Features

| Category | Capability | Your Agent |
|----------|------------|------------|
| 🔍 **Addvance context** | Advanced context across repositories include documentation and code | ❌ |
| 🤖 **Agentic** | Agent that searche deep in indexed code and documentation for your query | ❌ |
| 🛠️ **Aware engine** | You get access via MCP to the same features enterprise customers get | ❌ |
| 🚀 **Cross repo intelegence** | Ability to query multiple repositories | ❌ |
| 🎯 **Up to date** | We index daily all changes from the latest version for each repo | ❌ |


### 🤖 Prompts

```python
# Example 1: Let the model use aware tools based on resoning 
"""
Use open-aware to: Find all database connection implementations in our Python repositories 
and suggest connection pooling improvements for better performance.
"""

# Example 2: Spesificlly use deep-research
"""
Use deep-research to: Analyze the user authentication module in /backend/auth, identify code smells,
and generate a refactored version following SOLID principles.
"""

# Example 3: Spesificlly use get-context
"""
Use get-context to: Scan all API endpoints in our microservices, understand their functionality,
and create comprehensive OpenAPI documentation with examples.
"""

# Example 4: Granular search per repositories 
"""
Use open-aware to: Scan all API endpoints in our microservices, understand their functionality,
and create comprehensive OpenAPI documentation with examples.
repositories = ["...", "..."]
"""
```

## 🔨 Available Tools

The aware-open MCP server provides two powerful agent tools that can be integrated into your AI workflows:

### 1. **Context Retrieval Tool** (`get_context`)
This tool performs semantic search across your codebase to find relevant code snippets and implementations.

**Key Features:**
- **Semantic Search**: Uses vector embeddings to find conceptually similar code, not just keyword matches
- **Multi-Repository Support**: Search across multiple repositories simultaneously
- **Language Filtering**: Filter results by programming language (Python, JavaScript, TypeScript, etc.)
- **Intelligent Ranking**: Returns results ranked by relevance with configurable result limits
- **Tag-Based Filtering**: Use repository tags to narrow search scope

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

### 2. **Deep Ask Tool** (`deep_ask`)
An intelligent Q&A agent that can answer complex questions about your codebase by analyzing code structure, patterns, and relationships.

**Key Features:**
- **Code Understanding**: Comprehends code logic, architecture, and design patterns
- **Cross-Repository Analysis**: Can analyze relationships between different parts of your codebase
- **Implementation Planning**: Helps plan new features based on existing code patterns
- **Best Practice Recommendations**: Suggests improvements based on codebase analysis
- **Architecture Insights**: Provides high-level understanding of system design

**Example Usage:**
```json
{
  "tool": "deep_ask",
  "parameters": {
    "input": "How does the authentication flow work across our microservices? What security measures are in place?",
    "repositories": ["auth-service", "api-gateway", "user-service"],
    "session_id": "analysis-123"
  }
}
```

### Integration with MCP
Both tools are exposed through the Model Context Protocol (MCP), making them easily accessible to any MCP-compatible AI assistant or development environment. This enables:
- Seamless integration with AI coding assistants
- Automated code analysis workflows
- Context-aware code generation
- Intelligent refactoring suggestions

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
