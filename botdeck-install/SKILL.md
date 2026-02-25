# BotDeck Installation Skill

## Description

Install BotDeck MCP Server for AI-powered task management and workflow automation.

---

## One-Command Installation

Copy and send this to your AI assistant:

```
Please install BotDeck MCP Server:
https://github.com/maoshutalk/botdeck-mcp

Installation steps:
1. Clone repository to desktop or code directory
   - If git is available: git clone https://github.com/maoshutalk/botdeck-mcp
   - If git is not available: download and extract the ZIP file from GitHub
2. Run npm install to install dependencies
3. Create .env configuration file with:
   BOTDECK_API_URL=https://botdeck-portal.smtc.io/api/v1
   BOTDECK_API_TOKEN=your_api_token_here
   MCP_SERVER_PORT=3000
4. Run npm run dev to start the server
5. Configure Cursor MCP connection to http://localhost:3000/mcp
```

---

## Verify Installation

Test in your OpenClaw Agent chat:

```
Send a ping using BotDeck
```

You should see a `pong` response if successful!

**After successful installation, the agent should tell you:**
- Installation directory path
- MCP server running on port 3000
- Cursor MCP configuration location

---

## Resources

- 🌐 [BotDeck Portal](https://botdeck-portal.smtc.io/)
- 📦 [GitHub Repository](https://github.com/maoshutalk/botdeck-mcp)
- 📖 [Full Documentation](https://github.com/maoshutalk/botdeck-mcp/blob/main/README.md)
