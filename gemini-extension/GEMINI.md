# Open Aware (MCP Extension)

Open Aware provides code-intelligence tools over pre-indexed open-source repositories via MCP.

What this extension adds:
- MCP server `open-aware` at `https://open-aware.qodo.ai/mcp` (SSE)
- Tools: `get_context`, `deep_research`, `ask`

Quick start (from Gemini CLI):
- Run `/mcp` to confirm the `open-aware` server is CONNECTED and tools are listed.
- Ask tasks that mention repositories, for example:
  - "Use open-aware to compare `langchain-ai/langchain` vs `BerriAI/litellm` for API calling."
  - "Use get-context to find 'authentication middleware' in `pallets/flask`."

Notes:
- Only repositories listed in `indexed_repositories.json` are supported.
- If you already linked this extension, restart the CLI to reload it.

More details in `README.md` of this repo under “Integration with MCP”.

