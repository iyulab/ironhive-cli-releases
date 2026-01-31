# IronHive CLI

A general-purpose CLI agent powered by LLMs. Think Claude Code, but extensible.

## Installation

### Via dotnet tool (Recommended)

```bash
dotnet tool install -g IronHive.Cli --prerelease
```

### Via Binary Download

Download the latest release for your platform from the [Releases](https://github.com/iyulab/ironhive-cli-releases/releases) page.

| Platform | File |
|----------|------|
| Windows x64 | `ironhive-*-win-x64.zip` |
| Linux x64 | `ironhive-*-linux-x64.tar.gz` |
| macOS Intel | `ironhive-*-osx-x64.tar.gz` |
| macOS Apple Silicon | `ironhive-*-osx-arm64.tar.gz` |

## Quick Start

```bash
# Interactive mode
ironhive

# Single prompt
ironhive -p "List all files in this directory"

# Show help
ironhive --help
```

## Configuration

Set your LLM provider credentials:

```bash
# OpenAI
export OPENAI_API_KEY=sk-...

# Or use .env file in your project directory
echo "OPENAI_API_KEY=sk-..." > .env
```

Supported providers: OpenAI, Anthropic, Azure OpenAI, GpuStack, Ollama, LMSupply (local).

## Update

```bash
dotnet tool update -g IronHive.Cli --prerelease
# or
ironhive update
```

## License

MIT
