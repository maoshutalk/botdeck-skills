# BotDeck MCP Installation Skill

## Mission

Install BotDeck MCP Server automatically. Complete all steps without asking the user.

**Three Goals:**
1. ✅ Install BotDeck MCP Server
2. ✅ Run it successfully on port 3000
3. ✅ Test ping connection

**Report to user only after everything is done.**

---

## Auto-Installation Steps

Execute these steps automatically:

### 1. Clone Repository

```bash
# Clone to desktop or code directory
git clone https://github.com/maoshutalk/botdeck-mcp
cd botdeck-mcp

# If git not available: download https://github.com/maoshutalk/botdeck-mcp/archive/refs/heads/main.zip and extract
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment

Create `.env` file:

```env
BOTDECK_API_URL=https://botdeck-portal.smtc.io/api/v1
BOTDECK_API_TOKEN=your_api_token_here
MCP_SERVER_PORT=3000
```

### 4. Start Server

```bash
npm run dev
```

Server must run on port 3000.

### 5. Setup Cursor MCP

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "botdeck": {
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

### 6. Test Connection

Send ping command to verify connection works.

Expected result: `pong`

---

## Auto-Fix Common Issues

**Handle these automatically without asking:**

- **Port 3000 busy**: Kill the process or use another port
- **npm fails**: Clear cache and retry: `npm cache clean --force && npm install`
- **No git**: Download ZIP instead
- **Permission error**: Adjust permissions or try alternative location

**Make decisions yourself. Don't ask user for next steps.**

---

## Final Report

After completing all steps, tell the user:

```
✅ Installation Complete

📦 Skill Location: [where this skill was loaded from]
📍 MCP Location: [where botdeck-mcp was installed]
🚀 Server Status: Running on port 3000
🔗 MCP Config: [mcp.json path]
✓ Ping Test: Success

Next: Please restart Cursor IDE to activate BotDeck tools.
```

**If anything fails, report:**
```
❌ Installation Failed

Error: [what went wrong]
Attempted: [what you tried]
Need: [what's required to fix]
```

---

## Important Rules

1. **AUTO-EXECUTE** - Do everything automatically
2. **NO QUESTIONS** - Make decisions yourself
3. **TEST BEFORE REPORT** - Verify ping works
4. **CLEAR SUMMARY** - Tell user exactly what happened

---

## Resources

- 🌐 [BotDeck Portal](https://botdeck-portal.smtc.io/)
- 📦 [GitHub Repo](https://github.com/maoshutalk/botdeck-mcp)
