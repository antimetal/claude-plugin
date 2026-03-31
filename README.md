# Antimetal Plugin — Claude Code (beta)

Bring [Antimetal's](https://antimetal.com) software investigation intelligence into Claude Code. Triage problems, investigate root causes, fetch observability artifacts, and apply remediations — all from your terminal.

## Setup

### 1. Create an Antimetal Account

Sign up at [antimetal.com](https://antimetal.com) and connect your cloud infrastructure.

### 2. Set Your API Key

```bash
export ANTIMETAL_API_KEY="your-key-here"
```

Get your API key from [Account Settings](https://app.antimetal.com/settings/api). Add it to your shell profile (`~/.zshrc`, `~/.bashrc`, etc.) so it persists.

### 3. Install the Plugin

```
/plugin install antimetal/claude-plugin
```

Or add just the MCP server (no skills):

```bash
claude mcp add --transport http antimetal https://mcp.antimetal.com
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

- [Documentation](https://docs.antimetal.com/ai/claude-code)
- [Antimetal](https://antimetal.com)
- [Cursor Plugin](https://github.com/antimetal/cursor-plugin)
