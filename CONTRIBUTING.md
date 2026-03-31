# Contributing to Agentspan

Thanks for your interest in contributing to Agentspan! We welcome contributions of all sizes — from typo fixes to new examples to core features.

## Getting Started

### Prerequisites

| Component | Requirements |
|---|---|
| Python SDK | Python 3.9+, [uv](https://docs.astral.sh/uv/) (recommended) |
| Server | Java 21+ (auto-downloaded by CLI) |
| CLI | Go 1.21+ |
| UI | Node.js 18+, pnpm |
| TypeScript SDK | Node.js 18+ |

### Setup

```bash
git clone https://github.com/agentspan-ai/agentspan.git
cd agentspan
```

**Python SDK** (most common contribution area):

```bash
cd sdk/python
uv venv && source .venv/bin/activate
uv pip install -e ".[dev]"
```

**Server:**

```bash
cd server
./gradlew bootJar
```

**CLI:**

```bash
cd cli
go build -o agentspan .
```

**UI:**

```bash
cd ui
pnpm install
pnpm dev
```

**TypeScript SDK:**

```bash
cd sdk/typescript
npm install
npm run build
```

## Development Workflow

1. **Fork the repo** and create a branch from `main`.
2. **Make your changes** with tests.
3. **Run checks** before pushing:

   ```bash
   # Python SDK
   cd sdk/python
   make test-unit      # Unit tests (no server needed)
   make lint           # ruff check
   make typecheck      # mypy

   # Server
   cd server
   ./gradlew test

   # CLI
   cd cli
   go test ./... -count=1 -race

   # TypeScript SDK
   cd sdk/typescript
   npx vitest run tests/unit/

   # UI
   cd ui
   pnpm test
   pnpm lint
   ```

4. **Open a pull request** against `main`.

## What to Contribute

### Good first issues

Look for issues labeled [`good first issue`](https://github.com/agentspan-ai/agentspan/labels/good%20first%20issue) — these are scoped, well-described tasks ideal for new contributors.

### Examples

We have 180+ examples and always welcome more. Examples live in `sdk/python/examples/` and `sdk/typescript/examples/`. Follow the numbered naming convention (`XX_description.py`) and include a docstring explaining what the example demonstrates.

### Bug fixes

Found a bug? Check [existing issues](https://github.com/agentspan-ai/agentspan/issues) first. If it's new, open an issue with reproduction steps, then submit a fix.

### Features

For non-trivial features, **open an issue first** to discuss the design. This saves everyone time and ensures your contribution aligns with the project's direction.

### Documentation

Docs live in `docs/`. Improvements to API docs, guides, and tutorials are always welcome.

## Code Standards

### Python

- **Formatter/Linter:** [ruff](https://docs.astral.sh/ruff/)
- **Type checking:** [mypy](https://mypy-lang.org/) (strict)
- **Compatibility:** Python 3.9+
- **Tests:** [pytest](https://docs.pytest.org/) with coverage

### Java

- **Build:** Gradle
- **JDK:** 21+
- **Framework:** Spring Boot

### Go

- **Version:** 1.21+
- **Tests:** `go test` with `-race` flag
- **Style:** Standard Go conventions (`gofmt`)

### TypeScript

- **Linter:** ESLint
- **Formatter:** Prettier
- **Mode:** TypeScript strict
- **Tests:** [Vitest](https://vitest.dev/)

## Testing

| Level | What it tests | Server required? |
|---|---|---|
| Unit | Individual functions and classes | No |
| Integration | SDK ↔ server interaction | Yes |
| E2E | Full stack (SDK + server + LLM) | Yes |

Run unit tests freely — they need no external dependencies. Integration and E2E tests require a running server (`agentspan server start`).

## Pull Request Guidelines

- Keep PRs focused. One feature or fix per PR.
- Include tests for new functionality.
- Update examples if you change public API behavior.
- Write a clear PR description explaining *what* and *why*.
- CI must pass before merge.

## Commit Messages

Write clear, concise commit messages. Use present tense ("Add feature" not "Added feature"). No strict format enforced, but be descriptive.

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](https://github.com/agentspan-ai/agentspan/blob/main/LICENSE).
