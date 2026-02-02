# Configuration Guide

IronHive CLI loads configuration from multiple sources (in priority order):

1. Command-line arguments
2. Environment variables
3. `.env` file in project directory
4. Global config at `~/.ironhive/config.yaml`

## Environment Variables

### OpenAI / Compatible APIs

```bash
OPENAI_API_KEY=sk-...
OPENAI_BASE_URL=https://api.openai.com/v1  # optional
```

### GpuStack / Self-hosted

```bash
GPUSTACK_ENDPOINT=http://localhost:8080
GPUSTACK_API_KEY=your-api-key
GPUSTACK_MODEL=gpt-4o-mini
GPUSTACK_EMBEDDING_MODEL=text-embedding-3-small  # optional
GPUSTACK_RERANK_MODEL=rerank-model              # optional
```

### LMSupply (Local Inference)

```bash
LMSUPPLY_ENABLED=true
LMSUPPLY_EMBEDDER_MODEL=auto
LMSUPPLY_RERANKER_MODEL=auto
LMSUPPLY_GENERATOR_MODEL=gguf:default
```

## .env File

Create a `.env` file in your project root:

```bash
# .env
GPUSTACK_ENDPOINT=http://172.30.1.53:8080
GPUSTACK_API_KEY=gpustack_xxx
GPUSTACK_MODEL=gpt-oss-20b

# Optional: local fallback
LMSUPPLY_ENABLED=true
```

## Provider Selection

```bash
# Use specific provider
ironhive --provider openai
ironhive --provider gpustack
ironhive --provider ollama
ironhive --provider lmsupply

# Override model
ironhive --model gpt-4o-mini
ironhive --provider ollama --model llama3.2
```

## View Current Configuration

```bash
ironhive config show    # Show all settings
ironhive config path    # Show config file locations
```

## CLAUDE.md Support

Place a `CLAUDE.md` file in your project root for project-specific instructions. IronHive automatically loads and includes these instructions in the system prompt.

```markdown
# CLAUDE.md

## Project Overview
This is a React application using TypeScript...

## Coding Standards
- Use functional components
- Prefer hooks over class components
...
```
