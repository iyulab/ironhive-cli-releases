# MCP Plugins

IronHive supports [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) servers for tool extension.

## Plugin Configuration

Create `.ironhive/plugins.yaml` in your project:

```yaml
plugins:
  filesystem:
    transport: stdio
    command: npx
    arguments:
      - -y
      - "@modelcontextprotocol/server-filesystem"
      - "/path/to/allowed/directory"

  github:
    transport: stdio
    command: npx
    arguments:
      - -y
      - "@modelcontextprotocol/server-github"
    environment:
      GITHUB_PERSONAL_ACCESS_TOKEN: "your-token"

  memory:
    transport: sse
    url: http://localhost:3000/sse

# Global settings
defaultTimeoutMs: 30000
autoConnect: true
excludePlugins:
  - disabled-plugin
```

## Configuration Options

| Field | Type | Description |
|-------|------|-------------|
| `transport` | `stdio` \| `sse` | Transport protocol |
| `command` | string | Executable command (stdio) |
| `arguments` | string[] | Command arguments |
| `environment` | object | Environment variables |
| `workingDirectory` | string | Working directory |
| `url` | string | Server URL (sse transport) |
| `timeoutMs` | number | Connection timeout |
| `autoReconnect` | boolean | Auto-reconnect on disconnect |

## File Locations

Plugins are loaded from (in order):
1. `.ironhive/plugins.yaml`
2. `.ironhive/plugins.yml`
3. `.ironhive/plugins.json`
4. `plugins.yaml`
5. `plugins.yml`
6. `plugins.json`

## Example: Custom MCP Server

```yaml
plugins:
  my-server:
    transport: stdio
    command: node
    arguments:
      - ./my-mcp-server/index.js
    environment:
      DEBUG: "true"
```

## Hot Reload

Plugin configuration changes are detected automatically. No restart required.
