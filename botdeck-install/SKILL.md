# BotDeck MCP Installation Skill (for OpenClaw)

## Mission

**Auto-complete these 2 sections:**

### Section 1: Install MCP Server
1. Clone BotDeck MCP Server
2. **Ask user for API Token from https://botdeck-portal.smtc.io/**
3. Configure with user's token and run on port 3000
4. Configure Cursor (optional)

### Section 2: Install BotDeck MCP HTTP Bridge Skill
1. Clone botdeck-mcp-http to OpenClaw skills directory
2. Make CLI executable
3. **Verify MCP Server is running on port 3000 (REQUIRED)**
4. **Test ping with botdeck_call CLI (REQUIRED)**

**IMPORTANT:** 
- **ONLY ask user for API token**
- **All other issues: auto-fix yourself, don't ask user**
- **Choose best installation directory yourself** (Desktop, ~/Projects, ~/Code, etc.)
- Make all decisions automatically (port conflicts, installation paths, etc.)

---

## Section 1: Install MCP Server

### Step 1: Clone MCP Server Repository

```bash
# Choose installation directory (Desktop recommended, or any code directory you prefer)
# Options: ~/Desktop, ~/Documents, etc.
# You decide the best location

git clone https://github.com/maoshutalk/botdeck-mcp [your-chosen-directory]/botdeck-mcp
cd [your-chosen-directory]/botdeck-mcp

# Or if no git: download https://github.com/maoshutalk/botdeck-mcp/archive/refs/heads/main.zip
# Extract to your chosen directory
```

### Step 2: Get API Token from User

**IMPORTANT: Ask user for their BotDeck API Token**

```
⚠️ REQUIRED: BotDeck API Token

To use BotDeck, you need an API token from:
https://botdeck-portal.smtc.io/

Please:
1. Register/Login at https://botdeck-portal.smtc.io/
2. Go to Settings → API Tokens
3. Create a new token or copy existing one
4. Provide the token to continue

What is your BotDeck API Token?
```

**Wait for user to provide the token before continuing.**

### Step 3: Install & Configure MCP Server

```bash
npm install

# Create .env file with user's API token
cat > .env << EOF
BOTDECK_API_URL=https://botdeck-portal.smtc.io/api/v1
BOTDECK_API_TOKEN=[use token from user]
MCP_SERVER_PORT=3000
EOF
```

### Step 4: Start MCP Server

```bash
npm run dev
```

### Step 5: Configure Cursor (Optional)

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

---

## Section 2: Install BotDeck MCP HTTP Bridge Skill

**Install HTTP Bridge CLI for OpenClaw:**

### Step 6: Clone HTTP Bridge to OpenClaw Skills Directory

```bash
# OpenClaw skills directory
SKILLS_DIR="$HOME/.openclaw/skills"

# Create skills directory if not exists
mkdir -p "$SKILLS_DIR"

# Clone HTTP Bridge CLI
git clone https://github.com/maoshutalk/botdeck-mcp-http.git "$SKILLS_DIR/botdeck-mcp-http"

# Make CLI executable
chmod +x "$SKILLS_DIR/botdeck-mcp-http/bin/botdeck_call"
```

---

## Test Connection

### Step 7: Verify MCP Server is Running

**IMPORTANT: Before testing, ensure MCP Server is running on port 3000:**

```bash
# Check if MCP server is running
curl http://localhost:3000/mcp

# OR check if port 3000 is listening
lsof -i :3000

# If not running, start it:
cd [your-mcp-installation-directory]/botdeck-mcp
npm run dev

# Wait for server to be ready (should see "Server running on port 3000")
```

### Step 8: Test Ping with botdeck_call CLI (REQUIRED)

**MUST test ping to verify installation:**

```bash
# Test ping using botdeck_call CLI (use user's token)
$SKILLS_DIR/botdeck-mcp-http/bin/botdeck_call \
  tool="ping" \
  agent_name="TestAgent" \
  api_token="[use token from user]"

# Expected response: pong
# If ping fails, check:
# 1. MCP server is running on port 3000
# 2. API token is correct
# 3. Network connectivity
```

### Step 9: Final Verification

```bash
# Test help command
$SKILLS_DIR/botdeck-mcp-http/bin/botdeck_call --help

# Expected: Shows command usage and available tools
```

---

## Auto-Fix Issues

**You MUST auto-fix all issues. Don't ask user:**

- Port busy → kill process or change port automatically
- npm fails → run `npm cache clean --force && npm install`
- No git → download ZIP automatically
- Permission error → try different location or use sudo
- Directory exists → backup old and install new
- OpenClaw skills dir not found → create it automatically
- **MCP server not running → start it automatically before ping test**

**Make ALL decisions yourself. ONLY ask for API token.**

---

## Report to User

```
✅ Done

This Skill: [location in OpenClaw skills directory]

Section 1 - MCP Server:
  MCP Server: [botdeck-mcp installed at your-chosen-directory]
  Server: Running on port 3000 ✓
  Cursor Config: Updated (if applicable) ✓

Section 2 - HTTP Bridge Skill:
  HTTP Bridge: [installed at ~/.openclaw/skills/botdeck-mcp-http]
  MCP Server Check: Running on port 3000 ✓
  Ping Test: SUCCESS - pong received ✓
  CLI Verified: botdeck_call is executable ✓

→ All agents can now use botdeck_call command
→ For Cursor users: Restart Cursor to use BotDeck MCP tools
```

**If failed:**
```
❌ Failed: [error]
Section: [1 or 2]
Issue: [what the user encountered]
Tried: [what you did]
```

---

## Important

**Always respond in the user's language.**

---

## Rules

1. **AUTO-EXECUTE all steps in both sections**
2. **ONLY ask user for API token from https://botdeck-portal.smtc.io/**
3. **AUTO-FIX all other issues - NO questions to user**
4. **MUST TEST ping - installation not complete without ping success**
5. **REPORT absolute paths clearly**
6. **REPORT which section succeeded/failed**
