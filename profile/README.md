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
  <a href="https://www.npmjs.com/package/@agentspan-ai/agentspan"><img src="https://img.shields.io/npm/v/@agentspan-ai/agentspan?color=blue" alt="npm"></a>
  <a href="https://github.com/agentspan-ai/agentspan/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License"></a>
  <a href="https://discord.gg/agentspan"><img src="https://img.shields.io/discord/1234567890?label=Discord&logo=discord&color=5865F2" alt="Discord"></a>
</p>

---

**Agentspan** is a distributed, durable runtime for AI agents that survive crashes, scale across machines, and pause for human approval for days — not minutes.

Unlike traditional agent frameworks that run agents in-memory, Agentspan compiles agent definitions to server-side executions — giving you crash recovery, distributed tool scaling, and real human-in-the-loop out of the box.

### Get started in 60 seconds

```bash
npm install -g @agentspan-ai/agentspan
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

### Highlights

- **Durable execution** — Kill the process. The agent keeps running. Poll results from anywhere.
- **One primitive** — Everything is an `Agent`. Single agents, multi-agent teams, nested hierarchies.
- **Distributed workers** — Tools execute as distributed tasks in Python, Java, Go, or any language.
- **Human-in-the-loop** — `@tool(approval_required=True)` pauses durably. Approve days later, from any machine.
- **180+ examples** — Progressive examples covering tools, pipelines, guardrails, streaming, and more.
- **15+ LLM providers** — OpenAI, Anthropic, Gemini, Bedrock, Mistral, Ollama, and more.

### Repositories

| Repository | Description |
|---|---|
| [agentspan](https://github.com/agentspan-ai/agentspan) | Core runtime, SDKs (Python & TypeScript), CLI, server, and UI |

### Links

- [Documentation](https://docs.agentspan.dev)
- [Discord](https://discord.gg/agentspan)
- [PyPI](https://pypi.org/project/agentspan/)
- [npm](https://www.npmjs.com/package/@agentspan-ai/agentspan)
