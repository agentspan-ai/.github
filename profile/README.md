<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://agentspan.ai/logos/agentspan-logo-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://agentspan.ai/logos/agentspan-logo-light.png">
    <img src="https://agentspan.ai/logos/agentspan-logo-light.png" alt="Agentspan" width="360">
  </picture>
</p>

<h3 align="center">AI agents that don't die when your process does.</h3>

<p align="center">
  <a href="https://pypi.org/project/agentspan/"><img src="https://img.shields.io/pypi/v/agentspan?color=blue" alt="PyPI"></a>
  <a href="https://github.com/agentspan-ai/agentspan/stargazers"><img src="https://img.shields.io/github/stars/agentspan-ai/agentspan?style=social" alt="Stars"></a>
  <a href="https://github.com/agentspan-ai/agentspan/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License"></a>
  <a href="https://discord.com/invite/ajcA66JcKq"><img src="https://img.shields.io/discord/1488604882259939528?label=Discord&logo=discord&color=5865F2" alt="Discord"></a>
</p>

---

**Agentspan** is a durable runtime for AI agents. Agent definitions compile into server-side executions — crash-safe, human-in-the-loop, and fully observable. MIT licensed.

### Get Started in 60 Seconds

```bash
pip install agentspan          # Python SDK + CLI
agentspan server start         # starts on localhost:6767
```

```python
from agentspan.agents import Agent, AgentRuntime, tool

@tool
def get_weather(city: str) -> str:
    """Get current weather for a city."""
    return f"72°F and sunny in {city}"

agent = Agent(name="weatherbot", model="openai/gpt-4o", tools=[get_weather])

with AgentRuntime() as runtime:
    result = runtime.run(agent, "What's the weather in NYC?")
    result.print_result()
```

### Why Agentspan?

- **Durable execution** — Agents survive process crashes and resume from the last completed step
- **One primitive** — Everything is an `Agent`. Single agents, multi-agent teams, nested hierarchies
- **Human-in-the-loop** — Durable pause for approval. Resume days later, from any machine
- **Production guardrails** — Custom functions, regex, or LLM judges with retry, raise, fix, or escalate
- **Server-side tools** — HTTP endpoints, OpenAPI specs, and MCP servers with zero worker code
- **Full observability** — Visual execution UI, token tracking, full execution history
- **Framework integrations** — Wrap LangGraph, OpenAI Agents SDK, or Google ADK with one line
- **180+ examples** — Covering every feature across 5 frameworks

### Repositories

| Repository | Description |
|---|---|
| [agentspan](https://github.com/agentspan-ai/agentspan) | Core runtime, SDKs (Python & TypeScript), CLI, server, and UI |
| [agentspan-skills](https://github.com/agentspan-ai/agentspan-skills) | AI coding agent skills for Claude Code, Cursor, Codex, and more |
| [Python SDK](https://github.com/agentspan-ai/agentspan/tree/main/sdk/python) | Python SDK |
| [TypeScript SDK](https://github.com/agentspan-ai/agentspan/tree/main/sdk/typescript) | TypeScript SDK |

#### Other SDKs
Java, .NET, Go, Rust, and Ruby SDKs are in the works.

### Links

- [Documentation](https://agentspan.ai/docs)
- [Quickstart](https://agentspan.ai/docs/quickstart)
- [180+ Examples](https://github.com/agentspan-ai/agentspan/tree/main/sdk/python/examples)
- [Discord](https://discord.com/invite/ajcA66JcKq)
- [Contributing Guide](https://github.com/agentspan-ai/.github/blob/main/CONTRIBUTING.md)
