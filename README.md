# TestDino Cursor Plugin

Cursor plugin for TestDino using the documented local MCP flow for Cursor.

The MCP server source lives in the `testdino-hq/testdino-mcp` repository, and this plugin is based on the TestDino MCP local setup and tools reference docs.

TestDino: `https://app.testdino.com`

## What This Plugin Includes

- `.cursor-plugin/plugin.json` for Cursor plugin metadata
- `mcp.json` to start `testdino-mcp` through `npx`
- skills for connection checks, run analysis, manual test management, and TestDino audits

## Connection Model

This plugin follows TestDino's local MCP path for Cursor:

- Cursor uses the local MCP server path for TestDino
- the server runs through `npx -y testdino-mcp`
- authentication uses `TESTDINO_PAT` in client configuration

This matches TestDino's documented guidance for Cursor and other local MCP clients.

## Requirements

- Node.js installed
- a valid TestDino Personal Access Token
- `TESTDINO_PAT` available in the environment Cursor inherits

## Generate A TestDino PAT

To generate a Personal Access Token in TestDino:

1. Sign in to TestDino
2. Open `Profile`
3. Go to `My Account`
4. Open `Personal Access Tokens`
5. Generate a new token

Use that token as your `TESTDINO_PAT` value for local plugin testing.

Example PowerShell session:

```powershell
$env:TESTDINO_PAT="your-token-here"
cursor .
```

## Documented Workflows

The plugin is organized around the documented TestDino MCP tool groups:

- `health` for connection validation and project discovery
- test run analysis with `list_testruns`, `get_run_details`, `list_testcase`, `get_testcase_details`, and `debug_testcase`
- manual test management with `list_manual_test_cases`, `get_manual_test_case`, `create_manual_test_case`, `update_manual_test_case`, `list_manual_test_suites`, and `create_manual_test_suite`

## Example Prompts

- Check if my TestDino connection is working
- Show test runs within the last hour in project xyz
- Show me all failed tests from the last run
- Debug the test case "visual.spec.js" on development
- List all critical priority test cases in the checkout suite
- Create a new test case for password reset in Authentication

These prompts are adapted from the TestDino MCP overview and tools reference guidance.

## Support

- TestDino Support: `support@testdino.com`
- TestDino Documentation: `https://docs.testdino.com`
- MCP Documentation: `https://docs.testdino.com/mcp/local`
