# TestDino Plugin for Cursor

This repository contains the configuration needed to integrate the TestDino Model Context Protocol (MCP) server with Cursor IDE. The MCP enables your agents to interact directly with TestDino projects, allowing you to inspect test runs, debug failing or flaky test cases, manage manual test cases and suites, and run TestDino audits through natural language.

## Features

The TestDino MCP server provides the following capabilities:

- Connection and access checks: Validate your PAT, list organizations, and discover available projects
- Test run analysis: List test runs, inspect run details, and review failures across branches, commits, authors, environments, and time ranges
- Test case debugging: Inspect test case details, historical failures, retries, artifacts, and debugging context
- Manual test management: List, create, and update manual test cases and suites
- Audit workflows: Run the TestDino audit flow for Playwright test code

## MCP Server

The plugin includes the [Testdino MCP server](https://github.com/testdino-hq/testdino-mcp), giving agents tool access to the full Testdino API.

## Prerequisites

Before setting up the TestDino MCP server, ensure you have:

- Cursor IDE installed
- Node.js installed
- Access to a TestDino workspace
- A valid TestDino Personal Access Token

## Installation Instructions for Cursor

Follow these steps to configure the TestDino MCP server in Cursor.

### Step 1: Generate a TestDino PAT

To generate a Personal Access Token in TestDino:

1. Sign in to [TestDino](https://app.testdino.com)
2. Open `Profile`
3. Go to `My Account`
4. Open `Personal Access Tokens`
5. Generate a new token

Use that token as your `TESTDINO_PAT` value.

### Step 2: Add the token to the plugin MCP config

Open [mcp.json](./mcp.json) and paste the generated PAT token into the `TESTDINO_PAT` field.

Example configuration:

```json
{
  "mcpServers": {
    "testdino": {
      "command": "npx",
      "args": ["-y", "testdino-mcp"],
      "env": {
        "TESTDINO_PAT": "paste-your-generated-pat-here"
      }
    }
  }
}
```

### Step 3: Reload Cursor

After updating `mcp.json`, reload Cursor so the TestDino plugin picks up the new configuration.

### Step 4: Start using TestDino in chat

Once Cursor reloads, you can start using the TestDino plugin in chat.

## Usage Examples

Once configured, you can interact with TestDino through Cursor using natural language:

- Connection check: `Check if my TestDino connection is working`
- Project discovery: `Show my TestDino projects`
- Test run analysis: `Show test runs from the last hour`
- Failure analysis: `List failed test cases from the latest run`
- Flaky test debugging: `Find flaky tests in TestDino from the last 3 days`
- Test case debugging: `Debug the failing test case "visual.spec.js" in TestDino`
- Manual test management: `Create a manual test case in TestDino for checkout`
- Audit workflow: `Run a TestDino audit on this Playwright spec`

## Documentation & Resources

- TestDino: `https://app.testdino.com`
- MCP Documentation: `https://docs.testdino.com/mcp/local`
- TestDino Documentation: `https://docs.testdino.com`
- MCP Server Repository: `https://github.com/testdino-hq/testdino-mcp`

## Notes & Limitations

- Local MCP flow: This plugin is currently configured for TestDino's local MCP pattern in Cursor
- PAT required: The MCP server requires `TESTDINO_PAT`
- Audit scope: The TestDino audit flow is intended for Playwright automated test code
- Publish safety: Do not publish the plugin with a hardcoded PAT in `mcp.json`

## Questions or Issues?

For questions about the TestDino MCP server or setup issues, please use the resources below:

- TestDino Support: `support@testdino.com`
- TestDino Documentation: `https://docs.testdino.com`
