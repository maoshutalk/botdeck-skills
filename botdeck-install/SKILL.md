# BotDeck MCP Installation Skill

## Mission

**Auto-complete these 3 steps:**
1. Install BotDeck MCP
2. Run on port 3000
3. Test ping → report result

**Do NOT ask user. Execute everything automatically.**

---

## Installation Commands

### Step 1: Clone Repository

```bash
# IMPORTANT: Clone to Desktop or your code directory
git clone https://github.com/maoshutalk/botdeck-mcp ~/Desktop/botdeck-mcp
cd ~/Desktop/botdeck-mcp

# Or if no git: download https://github.com/maoshutalk/botdeck-mcp/archive/refs/heads/main.zip
```

### Step 2: Install & Configure

```bash
npm install

# Create .env file
cat > .env << EOF
BOTDECK_API_URL=https://botdeck-portal.smtc.io/api/v1
BOTDECK_API_TOKEN=your_api_token_here
MCP_SERVER_PORT=3000
EOF
```

### Step 3: Start Server

```bash
npm run dev
```

### Step 4: Configure Cursor

```bash
# Add to ~/.cursor/mcp.json
{
  "mcpServers": {
    "botdeck": {
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

### Step 5: Test Connection

Send ping command. Expect: `pong`

---

## Auto-Fix Issues

- Port busy → kill process or change port
- npm fails → `npm cache clean --force && npm install`
- No git → download ZIP
- Permission error → try different location

**Make decisions yourself. Don't ask.**

---

## Report to User

```
✅ Done

Skill: [this skill location]
MCP: [botdeck-mcp installed at]
Server: Running on port 3000
Test: Ping success ✓

→ Restart Cursor to use BotDeck tools
```

**If failed:**
```
❌ Failed: [error]
Issue: [what the user encountered]
Tried: [what you did]
```

---

## Important

**Always respond in the user's language.**

---

## Rules

1. AUTO-EXECUTE all steps
2. NO QUESTIONS to user
3. TEST before reporting
4. REPORT absolute paths clearly
