# Agent Guide

## Project

- This workspace contains a small Python example that calls an Azure-hosted, OpenAI-compatible chat deployment.
- The main entry point is [zai-org--glm-52-fp8.py](zai-org--glm-52-fp8.py).
- Keep changes focused on the example unless the user explicitly asks to expand the project structure.

## Run And Dependencies

- Install the current dependencies with `python3 -m pip install openai azure-identity`.
- Run the example with `python3 zai-org--glm-52-fp8.py`.
- There is currently no `requirements.txt`, `pyproject.toml`, lockfile, test suite, or documented Python version.

## Terminal Workflow

- Always show the exact terminal command in the progress update before running it.

## Azure Authentication

- Authentication uses `DefaultAzureCredential` with the `https://ai.azure.com/.default` scope.
- A usable Azure identity must be available through the standard Azure credential chain, such as an authenticated Azure CLI session, environment credentials, or managed identity.
- Never add credentials, tokens, or other secrets to source control. Prefer environment-based configuration when making the endpoint or deployment portable.

## API Contract

- The script uses the OpenAI Python client with an Azure OpenAI-compatible `base_url` and bearer-token provider.
- The deployment name must match the Azure deployment and support `/chat/completions`.
- Preserve the existing client API style unless a dependency upgrade requires a deliberate migration.
- When changing request or response handling, validate with a live authenticated request when available; otherwise run a syntax check and clearly state that network validation was not performed.