# Specification: Implement core project scaffolding and CLI initialization

## Objective
Establish the foundational directory structure, configuration files, and initial CLI command for generating new AI agent projects.

## Scope
- Create standard Python project configuration (`pyproject.toml` or `uv` setup).
- Define the base directory structure (e.g., `src/`, `tests/`, `docs/`).
- Implement the core CLI entry point (e.g., using `argparse` or `click` or `typer`).
- Add the initialization command `init` to generate the boilerplate structure.

## Technical Details
- **Language**: Python 3.10+
- **Tooling**: `poetry` or `uv`, `pytest`, `ruff`
- **CLI Framework**: To be decided (e.g., `typer`)

## Acceptance Criteria
- A developer can install the package locally.
- Running the CLI `init` command generates a complete, working boilerplate project in the target directory.
- The boilerplate includes a `README.md`, basic test setup, and a `main.py` entry point.
- All tests for the CLI tool pass with >80% coverage.