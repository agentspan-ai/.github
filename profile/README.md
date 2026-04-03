<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/agentspan-ai/agentspan/main/assets/logo-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/agentspan-ai/agentspan/main/assets/logo-light.svg">
    <img src="https://raw.githubusercontent.com/agentspan-ai/agentspan/main/assets/logo-light.svg" alt="Agentspan" width="400">
  </picture>
</p>

<h3 align="center">AI agents that don't die when your process does.</h3>

<p align="center">
  <a href="https://pypi.org/project/agentspan/"><img src="https://img.shields.io/pypi/v/agentspan?color=blue" alt="PyPI"></a>
  <a href="https://github.com/agentspan-ai/agentspan/stargazers"><img src="https://img.shields.io/github/stars/agentspan-ai/agentspan?style=social" alt="Stars"></a>
  <a href="https://github.com/agentspan-ai/agentspan/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License"></a>
  <a href="https://discord.com/invite/ajcA66JcKq"><img src="https://img.shields.io/discord/1234567890?label=Discord&logo=discord&color=5865F2" alt="Discord"></a>
</p>

---

**Agentspan** is a distributed, durable runtime for AI agents that survive crashes, scale across machines, and pause for human approval for days — not minutes.

Unlike traditional agent frameworks that run agents in-memory, Agentspan compiles your agent definitions to server-side executions. Kill the process — the agent keeps running. Poll for results from anywhere.

### Get Started in 60 Seconds

```bash
# macOS / Linux
curl -fsSL https://raw.githubusercontent.com/agentspan-ai/agentspan/main/cli/install.sh | sh

# Windows (PowerShell)
irm https://raw.githubusercontent.com/agentspan-ai/agentspan/main/cli/install.ps1 | iex

# Install Python SDK
pip install agentspan


agentspan server start
```

```python
from agentspan.agents import Agent, AgentRuntime, tool

@tool
def get_weather(city: str) -> str:
    """Get current weather for a city."""
    return f"72F and sunny in {city}"

agent = Agent(name="weatherbot", model="openai/gpt-4o", tools=[get_weather])

with AgentRuntime() as runtime:
    result = runtime.run(agent, "What's the weather in NYC?")
    result.print_result()
```

### Why Agentspan?

- **Durable execution** — Agents survive process crashes and resume automatically
- **One primitive** — Everything is an `Agent`. Single agents, multi-agent teams, nested hierarchies
- **Distributed workers** — Tools execute as distributed tasks in Python, Java, Go, or any language
- **Human-in-the-loop** — Durable pause for approval. Resume days later, from any machine
- **Production guardrails** — Custom functions, regex, or LLM judges with retry, raise, fix, or escalate
- **Server-side tools** — HTTP endpoints, OpenAPI specs, and MCP servers with zero worker code
- **Full observability** — OpenTelemetry, Prometheus, visual execution UI, token tracking
- **180+ examples** — Covering every feature across 5 frameworks

### Repositories

| Repository | Description |
|---|---|
| [agentspan](https://github.com/agentspan-ai/agentspan) | Core runtime, SDKs (Python & TypeScript), CLI, server, and UI |
| [Python SDK](https://github.com/agentspan-ai/agentspan/tree/main/sdk/python) | Python SDk |
| [Typescript SDK](https://github.com/agentspan-ai/agentspan/tree/main/sdk/typescript) | Typescript SDK |

#### Where are other SDKs?
Java, .NET, Golang, Rust, Ruby SDKs are in works and going to be available here soon!

### Links

- [Documentation](https://docs.agentspan.dev)
- [180+ Examples](https://github.com/agentspan-ai/agentspan/tree/main/sdk/python/examples)
- [API Reference](https://github.com/agentspan-ai/agentspan/blob/main/docs/python-sdk/api-reference.md)
- [Discord](https://discord.gg/agentspan)
- [Contributing Guide](https://github.com/agentspan-ai/.github/blob/main/CONTRIBUTING.md)
