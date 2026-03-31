# Contributing to Agentspan

Thanks for your interest in contributing to Agentspan. This guide covers the development setup, workflow, and standards for contributing code, docs, and examples.

## Quick Start

```bash
git clone https://github.com/agentspan-ai/agentspan.git
cd agentspan
```

### Python SDK (most common)

```bash
cd sdk/python
uv venv && source .venv/bin/activate
uv pip install -e ".[dev]"
make test-unit        # Run unit tests (no server needed)
make lint             # Lint with ruff
make typecheck        # Type check with mypy
```

### Java Server

```bash
cd server
./gradlew test        # Run tests
./gradlew bootJar     # Build the JAR
```

### Go CLI

```bash
cd cli
go test ./... -count=1 -race
go build -o agentspan .
```

### TypeScript SDK

```bash
cd sdk/typescript
npm install
npm run build
npx vitest run tests/unit/
```

### React UI

```bash
cd ui
pnpm install
pnpm dev              # Dev server at localhost:1234
pnpm test
pnpm lint
```

## Running the Full Stack

For integration or end-to-end testing, start the server first:

```bash
agentspan server start          # Starts on localhost:6767
```

Then run integration tests:

```bash
cd sdk/python
make test-integration           # Requires running server + LLM API key
```

## Project Structure

```
agentspan/
├── cli/                  # Go CLI
├── server/               # Java/Spring Boot runtime (Conductor-based)
├── sdk/
│   ├── python/           # Primary Python SDK
│   │   ├── src/agentspan/agents/
│   │   ├── examples/     # 180+ runnable examples
│   │   └── tests/        # unit/, integration/, e2e/
│   └── typescript/       # TypeScript SDK
├── ui/                   # React execution dashboard
├── deployment/           # Docker Compose, Helm, K8s manifests
└── docs/                 # Documentation
```

## Development Workflow

1. **Fork the repo** and create a feature branch from `main`
2. **Make your changes** with tests
3. **Run the relevant test suite** before pushing (see Quick Start above)
4. **Open a pull request** against `main`

### Commit Messages

Write clear, concise commit messages. Use imperative mood ("Add feature", not "Added feature"). No strict format enforced — just be descriptive.

### Pull Requests

- Keep PRs focused. One feature or fix per PR.
- Include tests for new functionality.
- Update or add examples if your change affects the public API.
- Link related issues in the PR description.

## What to Contribute

### Good First Contributions

- **Examples** — Add examples for features or use cases not yet covered
- **Documentation** — Improve or clarify existing docs
- **Bug fixes** — Check [open issues](https://github.com/agentspan-ai/agentspan/issues) for bugs

### Larger Contributions

- **New tools or integrations** — HTTP, MCP, or framework integrations
- **New multi-agent strategies** — Beyond the 8 built-in strategies
- **Server features** — New database backends, observability, performance
- **SDK features** — Guardrails, memory, termination conditions
- **CLI improvements** — New commands, better UX

For larger changes, open an issue first to discuss the approach.

## Code Standards

| Component | Linter | Type Checker | Test Runner |
|---|---|---|---|
| Python SDK | ruff | mypy | pytest |
| Java Server | — | javac (JDK 21) | JUnit (Gradle) |
| Go CLI | go vet | go (built-in) | go test |
| TypeScript SDK | ESLint | tsc (strict) | Vitest |
| React UI | ESLint + Prettier | tsc | Vitest |

### Python-Specific

- Target Python 3.9+
- Use type annotations for public APIs
- Use `ruff` for formatting and linting
- Prefer `uv` for dependency management

### Testing

- **Unit tests** should not require a running server or LLM API keys
- **Integration tests** are marked and require a running server
- **E2e tests** run the full stack and are part of CI

## CI

GitHub Actions runs on every PR:

1. Python unit tests with coverage
2. TypeScript unit tests
3. Java server tests
4. Go CLI tests with race detector
5. Server build + Python/TypeScript e2e tests

All checks must pass before merging.

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](https://github.com/agentspan-ai/agentspan/blob/main/LICENSE).

## Questions?

- **[Discord](https://discord.gg/agentspan)** — Ask questions, discuss ideas
- **[GitHub Issues](https://github.com/agentspan-ai/agentspan/issues)** — Bug reports and feature requests
