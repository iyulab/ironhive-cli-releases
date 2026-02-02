# IronHive CLI

A general-purpose CLI agent powered by LLMs. Think Claude Code, but extensible.

## Installation

### Via dotnet tool (Recommended)

```bash
dotnet tool install -g IronHive.Cli --prerelease
```

### Via Binary Download

Download from [Releases](https://github.com/iyulab/ironhive-cli-releases/releases):

| Platform | File |
|----------|------|
| Windows x64 | `ironhive-win-x64.zip` |
| Linux x64 | `ironhive-linux-x64.tar.gz` |
| macOS Intel | `ironhive-osx-x64.tar.gz` |
| macOS Apple Silicon | `ironhive-osx-arm64.tar.gz` |

## Quick Start

```bash
# Interactive mode
ironhive

# Single prompt
ironhive -p "List all TypeScript files in src/"

# Continue last session
ironhive -c

# Show help
ironhive --help
```

## Configuration

Create a `.env` file in your project directory:

```bash
# OpenAI
OPENAI_API_KEY=sk-...

# Or GpuStack/Ollama compatible endpoint
GPUSTACK_ENDPOINT=http://localhost:8080
GPUSTACK_API_KEY=your-key
GPUSTACK_MODEL=gpt-4o-mini
```

Or use environment variables directly.

**Supported providers:** OpenAI, Anthropic, Azure OpenAI, GpuStack, Ollama, LMSupply (local)

## CLI Options

```
ironhive [options]

Options:
  -p, --prompt <PROMPT>     Run a single prompt and exit
  -m, --model <MODEL>       Model to use (e.g., gpt-4o-mini)
  --provider <PROVIDER>     Provider (openai, ollama, gpustack)
  -c, --continue            Continue the most recent session
  -r, --resume <ID>         Resume a specific session
  --fork                    Fork the resumed session
  -o, --output <FORMAT>     Output format: text, json, jsonl
  --plain                   Plain text output (no ANSI)
  --show-tokens             Show token usage
  --show-thinking           Show model reasoning
  --no-stream               Disable streaming
  --plan                    Planning mode (read-only)
  --dry-run                 Show actions without executing
```

## Commands

```bash
ironhive                    # Interactive mode
ironhive run "prompt"       # Run single prompt
ironhive sessions           # List sessions
ironhive sessions delete ID # Delete a session
ironhive config show        # Show configuration
ironhive config path        # Show config file paths
ironhive update             # Check for updates
```

## Documentation

- [Configuration Guide](docs/configuration.md)
- [Session Management](docs/sessions.md)
- [MCP Plugins](docs/plugins.md)

## Update

```bash
dotnet tool update -g IronHive.Cli --prerelease
# or
ironhive update
```

## License

Free for personal and commercial use. Source code is proprietary.
See [LICENSE](./LICENSE) for details.
