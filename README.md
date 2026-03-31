# Antimetal Plugin — Claude Code (beta)

Bring [Antimetal's](https://antimetal.com) software investigation intelligence into Claude Code. Triage problems, investigate root causes, fetch observability artifacts, and apply remediations — all from your terminal.

## Setup

### 1. Create an Antimetal Account

Sign up at [antimetal.com](https://antimetal.com) and connect your cloud infrastructure.

### 2. Add the Plugin Marketplace

Since this plugin is hosted on GitHub (not the built-in Claude Code marketplace), you need to register this repo as a plugin source first:

```
/plugin marketplace add antimetal/claude-plugin
```

### 3. Install the Plugin

```
/plugin install antimetal
```

### 4. Authenticate

When you first use an Antimetal tool or skill, Claude Code will open a browser window to log in to your Antimetal account via OAuth. Once you log in, you're all set — tokens are stored securely and refreshed automatically.

#### Alternative: API key

If OAuth isn't available in your environment, you can authenticate with an API key instead:

1. Generate a key at [API Keys Settings](https://overlook.antimetal.com/settings/api-keys)
2. Set the environment variable:
   ```bash
   export ANTIMETAL_API_KEY="your-key-here"
   ```
   Add it to your shell profile (`~/.zshrc`, `~/.bashrc`, etc.) so it persists.

### MCP server only (no skills)

If you just want the MCP tools without the plugin skills:

```bash
claude mcp add --transport http antimetal https://mcp.antimetal.com
```

OAuth will trigger automatically on first use. For API key auth, pass the header explicitly:

```bash
claude mcp add --transport http antimetal https://mcp.antimetal.com \
  --header "Authorization: Bearer ${ANTIMETAL_API_KEY}"
```

## Skills

| Skill | Description |
| --- | --- |
| `/investigate` | Search issues, kick off investigations, read reports, query Antimetal's AI |
| `/fix` | Retrieve and apply remediation steps to your codebase |
| `/antimetal-mcp-setup` | Configure the MCP server connection (OAuth or API key) |

## MCP Tools

Connects to Antimetal's remote MCP server at `mcp.antimetal.com`, providing access to these tools:

| Tool                | Description                                                                           |
| ------------------- | ------------------------------------------------------------------------------------- |
| `search_issues`     | Paginated list of issues with severity, status, and environment                       |
| `get_issue_report`  | Full investigative report — root cause, timeline, causal graph                        |
| `get_issue_fixes`   | Remediation steps (code changes, CLI commands, context)                               |
| `investigate_issue` | Create a new issue and start async automated investigation                            |
| `get_artifact`      | Retrieve raw evidence: logs, traces, metrics, events, files, topology                 |
| `ask`               | Ask Antimetal's AI about infrastructure, software, deployments, telemetry, logs, code  |

## Usage

### Investigate a problem

```
/investigate
> Our API latency spiked in us-east-1 around 2pm
```

### Check on an investigation

```
/investigate
> Check on issue #42
```

### Fix an issue

```
/fix
> Fix issue #42
```

## Links

- [Documentation](https://docs.antimetal.com/connect)
- [Antimetal](https://antimetal.com)
- [Cursor Plugin](https://github.com/antimetal/cursor-plugin)
