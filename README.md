# FinancialResearchAiAgent

AI Agent Financial Research AI Agent&#39; Project.

## Quick Start

1. Install dependencies:
   ```bash
   uv sync
   ```

2. Configure your agent:
   - Edit `agentup.yml` to customize skills, providers, and features
   - Set environment variables in `.env` file

3. Start the development server:
   ```bash
   agentup run
   ```

   Or run direct with uvicorn:
   ```bash
   uv run uvicorn agent.api.app:app --reload --port 8000
   ```

### **Template-Specific Features**
This agent was created with the **** template and includes:

- ✓ Advanced authentication and security schemes

## Development

This agent runs from the AgentUp framework package.

#### 1. Adding New Tools via Plugins

**Create a Local Plugin:**
```bash
# Create plugin in the plugins directory
agentup plugin init my-skill --output-dir plugins/

# Install in development mode
pip install -e plugins/my-skill

# Add to agentup.yml
```

**Use Existing Plugins:**
```bash
# Install from PyPI
pip install agentup-plugin-name

# Or from Git
pip install git+https://github.com/user/agentup-plugin-name
```

#### 2. Configuration-Based Customization

**Modify Agent Behavior** (`agentup.yml`):
```yaml
skills:
  - plugin_id: my_plugin_skill  # From installed plugin
    name: My Skill
    description: Custom skill via plugin
    tags: [custom, business]
    # Routing is now implicit - no configuration needed
    priority: 100
```

**Environment Configuration** (`.env`):
```bash
# Set API keys and service URLs
OPENAI_API_KEY=your_key_here
GITHUB_TOKEN=your_token_here
```

#### 3. Framework Updates

Your agent automatically gets framework updates when you upgrade AgentUp:

```bash
# Upgrade to latest AgentUp version
pip install --upgrade agentup

# Restart your agent - new features available immediately
agentup run
```

## Testing

Test your agent using A2A-compliant JSON-RPC calls:

```bash
# Test basic message handling
curl -X POST http://localhost:8000/ \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "message/send",
    "params": {
      "message": {
        "role": "user",
        "parts": [{"kind": "text", "text": "Hello"}],
        "message_id": "msg-001",
        "context_id": "ctx-001",
        "kind": "message"
      }
    },
    "id": "req-001"
  }'

# Test agent discovery
curl http://localhost:8000/.well-known/agent-card.json
```

## Project Structure

```
financial_research_ai_agent/
├── agentup.yml          # Main configuration
├── .env                 # Environment variables  
├── README.md           # This file
├── pyproject.toml      # Dependencies (just agentup)
```

## Deployment

The agent can be deployed anywhere Python runs:

```bash
uvicorn agent.api.app:app --host 0.0.0.0 --port 8000
```


## Documentation

For more information:
- [AgentUp Documentation](https://docs.agentup.dev)
- [Plugin Development Guide](https://docs.agentup.dev/plugins)

## License

Apache 2.0

---
Created with [AgentUp](https://github.com/RedDotRocket/AgentUp)
