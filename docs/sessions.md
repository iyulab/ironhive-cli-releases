# Session Management

IronHive automatically saves conversation history, allowing you to continue where you left off.

## Session Commands

```bash
# List recent sessions
ironhive sessions

# List with custom limit
ironhive sessions -n 20

# Delete a session
ironhive sessions delete <session-id>

# JSON output
ironhive sessions -o json
```

## Continue Previous Session

```bash
# Continue most recent session
ironhive -c
ironhive --continue

# Resume specific session by ID
ironhive -r abc123
ironhive --resume abc123

# Fork a session (create a branch)
ironhive -r abc123 --fork
```

## Session Storage

Sessions are stored per-project in:
- **Windows:** `%LOCALAPPDATA%\ironhive\sessions\`
- **Linux/macOS:** `~/.local/share/ironhive/sessions/`

Each session contains:
- Conversation transcript (JSONL format)
- Metadata (model, timestamps, message count)
- Context restoration data

## Session Lifecycle

| Status | Description |
|--------|-------------|
| `active` | Currently in use |
| `ended` | Normally closed |
| `forked` | Created from another session |
| `error` | Ended due to an error |

## Programmatic Access

Use JSON output for scripting:

```bash
# Get session list as JSON
ironhive sessions -o json

# Output format:
# [{"id":"abc123","status":"ended","model":"gpt-4o","created":"2024-01-01T12:00:00Z","messageCount":10}]
```
