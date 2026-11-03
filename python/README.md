# sports-odds-mcp (Python)

<!-- mcp-name: io.github.GeminiGeorge22/sports-odds-api -->

Python version of the [sports-odds-mcp](https://github.com/GeminiGeorge22/sports-odds-mcp) stdio MCP server, built on the official [`mcp`](https://pypi.org/project/mcp/) Python SDK. Same tools, same `APIFY_TOKEN` env var, same hosted endpoint as the Node.js server.

Stdio MCP server for live sportsbook odds (Kambi books) via Apify's hosted MCP gateway

It answers `initialize` and `tools/list` locally from the bundled `tools.json` (no token, no network). `tools/call` is forwarded to Apify's hosted MCP endpoint (`mcp.apify.com`) with **your own** `APIFY_TOKEN`, so each run uses your Apify account. Without a token a call returns a clear error instead of running anything. The token is only sent in the `Authorization` header and is never logged.

## Install

Requires Python 3.10+. With [uv](https://docs.astral.sh/uv/):

```bash
uvx sports-odds-mcp
```

With pip:

```bash
pip install sports-odds-mcp
sports-odds-mcp
```

To run the latest unreleased code from GitHub instead of the PyPI release: `uvx --from "git+https://github.com/GeminiGeorge22/sports-odds-mcp#subdirectory=python" sports-odds-mcp`.

MCP client config:

```json
{
  "mcpServers": {
    "sports-odds": {
      "command": "uvx",
      "args": ["sports-odds-mcp"],
      "env": { "APIFY_TOKEN": "YOUR_APIFY_TOKEN" }
    }
  }
}
```

Optional env: `APIFY_ACTORS` (comma-separated subset of the Actors) and `APIFY_MCP_URL` (full endpoint override).

## Tests

Tests use an in-process mock server, with no network and no token. They fail if `APIFY_TOKEN` is set.

```bash
cd python && pip install -e ".[test]"
env -u APIFY_TOKEN python -m pytest
```

`python scripts/build_tools.py --check` compares the bundled `tools.json` with each Actor's live public input schema and exits 1 on any mismatch.
