# Kyma Companion

## Status

[![REUSE status](https://api.reuse.software/badge/github.com/kyma-project/kyma-companion)](https://api.reuse.software/info/github.com/kyma-project/kyma-companion)

## Overview

Kyma Companion is an AI-powered assistant for Kyma users. It provides contextual help in-app and supports users with general Kyma-related tasks.

## Prerequisites

- Python `3.13.x`
- [Poetry](https://python-poetry.org/)
- A running Redis instance
  - internal reference: [Create Redis](https://github.tools.sap/kyma/ai-force/blob/main/docs/infrastructure/setup.md#15-redis) <!--the link must be replaced when the OS documentation is available -->

## Quick Start

1. Install dependencies:

   ```bash
   poetry install
   ```

2. Set required environment variable:

   ```bash
   export REDIS_URL="redis://<host-or-ip>:6379"
   ```

3. Start the app (development mode):

   ```bash
   poetry run poe run-local
   ```

The service starts on port `8000`.

## Run Locally

### Recommended (FastAPI via Poe task)

```bash
poetry run poe run-local
```

### Alternative commands

```bash
poetry run fastapi dev src/main.py --port 8000
```

or

```bash
poetry run poe run
```

### Run via Python entrypoint

```bash
python src/main.py
```

With auto-reload:

```bash
python src/main.py --reload
```

## Configuration

- Default config file: `config/config.json`
- Override with:

  ```bash
  export CONFIG_PATH="/path/to/config.json"
  ```

## Dependency Management (Poetry)

Install all dependencies:

```bash
poetry install
```

Update a package:

```bash
poetry update <package_name>
```

Add a package:

```bash
poetry add <package_name>
```

Add with exact version:

```bash
poetry add <package_name>@<version>
```

Remove a package:

```bash
poetry remove <package_name>
```

## Development

### Redis

Kyma Companion stores LLM conversation state in Redis.

Set the `REDIS_URL` environment variable before running the app.

Example:

```bash
export REDIS_URL="redis://<host-or-ip>:6379"
```

For setup details, see [Create Redis](https://github.tools.sap/kyma/ai-force/blob/main/docs/infrastructure/setup.md#15-redis). <!--the link must be replaced when the OS documentation is available -->

### IDE Debugging

Because the project uses FastAPI, refer to:

- [PyCharm](https://www.jetbrains.com/help/pycharm/fastapi-project.html#create-project)
- [VS Code](https://code.visualstudio.com/docs/python/tutorial-fastapi)

### Tracing

Kyma Companion uses [Langfuse](https://langfuse.com/).
See [Using Langfuse in Kyma Companion](./docs/langfuse.md).

## Code Quality

Run all checks (lint + typecheck + formatting check):

```bash
poetry run poe codecheck
```

Auto-fix formatting and safe lint issues:

```bash
poetry run poe code-fix
```

### Linting (Ruff)

```bash
poetry run poe lint
```

Auto-fix (safe fixes):

```bash
poetry run poe lint-fix
```

> [!WARNING]
> Run auto-fix carefully, because it can modify code in unexpected ways.

### Formatting (Black)

Check formatting:

```bash
poetry run poe format
```

Fix formatting:

```bash
poetry run poe format-fix
```

### Type checking (mypy)

```bash
poetry run poe typecheck
```

## Tests

### Unit tests

```bash
poetry run poe test
```

Alternative:

```bash
poetry run pytest tests/unit
```

### Integration tests

See [Integration Tests README](./tests/integration/README.md).

### Blackbox tests

See [Blackbox Tests README](./tests/blackbox/README.md).

## Release Process

Release testing and release creation are separate processes.
For details, see the [Contributor README](./docs/contributor/README.md).

## Contributing

<!--- mandatory section - do not change this! --->

See the [Contributing Rules](CONTRIBUTING.md).

## Code of Conduct

<!--- mandatory section - do not change this! --->

See the [Code of Conduct](CODE_OF_CONDUCT.md) document.

## Licensing

<!--- mandatory section - do not change this! --->

See the [license](./LICENSE) file.
