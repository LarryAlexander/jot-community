# Model Context Protocol (MCP) Setup

**Extend Jot's AI capabilities with external tools and data sources**

MCP allows AI to access files, databases, APIs, and more through a standardized protocol.

---

## What is MCP?

**Model Context Protocol (MCP)** is an open standard that connects AI models to external tools and data sources. With MCP, Jot's AI can:

- 📁 Read and search files on your computer
- 🗄️ Query databases and structured data
- 🌐 Fetch live data from the web
- 🔧 Execute custom tools and scripts
- 🔒 Do all of this with your explicit permission

**Privacy:** MCP tools run locally on your desktop. You control which tools are enabled and approve each action.

---

## Why Use MCP?

| Feature | Without MCP | With MCP |
|---------|-------------|----------|
| **File Access** | Copy/paste only | AI can read files directly |
| **Data Sources** | Manual lookup | AI queries databases, APIs |
| **Capabilities** | Text generation only | Text + actions + data retrieval |
| **Privacy** | Cloud API calls | Local tools, explicit permission |

**Best for:** Desktop users (macOS, Windows, Linux) who want AI to access specific files or data sources while maintaining full control.

---

## Quick Start

### 1. Find or Build an MCP Server

MCP servers expose tools to AI. Choose from community servers or build your own:

**Popular MCP Servers:**
- **Filesystem** — Read/search local files and folders
- **GitHub** — Query repositories, issues, PRs
- **PostgreSQL** — Query databases
- **Slack** — Read messages, send notifications
- **Custom** — Build your own with `@modelcontextprotocol/sdk`

**Find servers:** [modelcontextprotocol.io/servers](https://modelcontextprotocol.io/servers)

### 2. Install an MCP Server

**Option A: Filesystem Server (Recommended for beginners)**

```bash
# Install Node.js if needed
brew install node

# Install filesystem MCP server globally
npm install -g @modelcontextprotocol/server-filesystem
```

**Option B: Python-based servers**

```bash
# Install Python if needed
brew install python3

# Example: SQLite MCP server
pip install mcp-server-sqlite
```

### 3. Add Server to Jot

1. Open **Settings → MCP Servers**
2. Tap **"Add MCP Server"**
3. Choose transport type:
   - **stdio** (Command-line servers) — Most common
   - **HTTP** (Web servers) — For remote or self-hosted servers

**For stdio (filesystem example):**
- **Server Name:** Filesystem
- **Command:** `/usr/local/bin/mcp-server-filesystem`
- **Arguments:** `/Users/yourname/Documents/Notes`
- Tap **"Connect"**

**For HTTP:**
- **Server Name:** Custom API
- **URL:** `http://localhost:3000/mcp`
- Tap **"Connect"**

### 4. Enable Tools

After connecting:
1. Jot lists all available tools from the server
2. Review each tool's description
3. Toggle **ON** for tools you want to use
4. Tools are now available to AI

### 5. Use Tools in AI Requests

When you ask AI a question that needs external data:
1. AI detects relevant tool (e.g., "Read this file")
2. **Permission dialog appears** showing:
   - Tool name
   - What it will do
   - Redacted preview of parameters
3. Tap **"Allow"** to execute or **"Deny"** to skip
4. AI receives tool result and incorporates it into response

---

## Example MCP Servers

### Filesystem Server

**What it does:** Allows AI to read files, list directories, search file contents

**Install:**
```bash
npm install -g @modelcontextprotocol/server-filesystem
```

**Add to Jot:**
- **Transport:** stdio
- **Command:** `mcp-server-filesystem`
- **Arguments:** `~/Documents` (or your chosen directory)

**Tools provided:**
- `read_file` — Read file contents
- `list_directory` — List files in folder
- `search_files` — Search for text in files

**Example use:**
> "Summarize all markdown files in my Documents folder"

AI will:
1. Request `list_directory ~/Documents` → You approve
2. Request `read_file` for each .md file → You approve each
3. Generate summary from file contents

---

### GitHub Server

**What it does:** Query GitHub repositories, issues, pull requests

**Install:**
```bash
npm install -g @modelcontextprotocol/server-github
```

**Setup:**
1. Create GitHub Personal Access Token:
   - GitHub.com → Settings → Developer Settings → Personal Access Tokens
   - Generate token with `repo` scope
2. Add to Jot:
   - **Transport:** stdio
   - **Command:** `mcp-server-github`
   - **Environment Variables:** `GITHUB_TOKEN=your_token_here`

**Tools provided:**
- `get_repository` — Fetch repo details
- `list_issues` — Query open issues
- `search_code` — Find code snippets

**Example use:**
> "Find all TypeScript files with 'export class' in my jot repository"

---

### PostgreSQL Server

**What it does:** Query PostgreSQL databases

**Install:**
```bash
npm install -g @modelcontextprotocol/server-postgres
```

**Setup:**
- **Transport:** stdio
- **Command:** `mcp-server-postgres`
- **Arguments:** `postgres://user:pass@localhost:5432/mydb`

**Tools provided:**
- `query` — Execute SELECT queries (read-only)
- `list_tables` — Show database schema

**Example use:**
> "How many users signed up this month?"

AI generates and executes: `SELECT COUNT(*) FROM users WHERE created_at >= '2026-01-01'`

---

### Custom HTTP Server

**What it does:** Connect to any MCP-compatible web server

**Example:** Your own API that exposes company data

**Setup:**
1. Deploy MCP server (Node.js example):
   ```javascript
   const { Server } = require('@modelcontextprotocol/sdk/server');
   const server = new Server({
     name: "company-data",
     version: "1.0.0"
   });
   
   server.setRequestHandler("tools/list", async () => ({
     tools: [{
       name: "get_sales_data",
       description: "Fetch sales metrics",
       inputSchema: { /* ... */ }
     }]
   }));
   
   // Start HTTP server on port 3000
   ```

2. Add to Jot:
   - **Transport:** HTTP
   - **URL:** `http://localhost:3000`

---

## Security & Privacy

### Permission System

Every MCP tool execution requires your approval:

1. **Request appears** with tool name and parameters
2. **Redacted preview** hides sensitive data (emails, IPs, long content)
3. **You choose**: Allow (execute once) or Deny (skip this tool)
4. **No auto-execution** — AI can't run tools without permission

### What's Logged

**Activity History (Settings → MCP Servers → Activity):**
- ✅ Timestamp
- ✅ Server name
- ✅ Tool name
- ✅ Duration
- ✅ Success/failure status
- ❌ **NOT LOGGED:** Tool arguments, results, or note contents

**Debug Logs (Optional):**
- Enable in Settings → MCP Servers → Debug Logging
- Writes raw MCP data to `~/Documents/Jot/mcp_debug.log`
- ⚠️ **WARNING:** Contains unredacted arguments and results
- Use only for troubleshooting, delete log when done

### SSRF Prevention

Jot blocks dangerous URLs to prevent Server-Side Request Forgery:

- ✅ **Allowed:** `http://localhost:*`, `http://127.0.0.1:*`, `http://[::1]:*`
- ❌ **Blocked:** Private network IPs (`192.168.*.*`, `10.*.*.*`, `172.16-31.*.*`)
- ⚠️ **Warning shown:** For any non-localhost URL

**Why:** Prevents MCP servers from accessing your home network or internal services.

### Rate Limiting

- **Max 10 tool calls per AI request**
- Prevents runaway loops (e.g., AI recursively reading files forever)
- Configurable in MCP integration service code

---

## Troubleshooting

### "Server failed to start"

**Check command path:**
```bash
# Find where mcp-server-filesystem is installed
which mcp-server-filesystem

# Use full path in Jot configuration
# e.g., /usr/local/bin/mcp-server-filesystem
```

**Verify server runs manually:**
```bash
mcp-server-filesystem ~/Documents
# Should output JSON-RPC initialization messages
```

**Common fixes:**
- Install with `-g` flag: `npm install -g @modelcontextprotocol/server-*`
- Use absolute paths for command and arguments
- Check server documentation for required environment variables

---

### "No tools available"

**Fix 1:** Reconnect to server
1. Settings → MCP Servers
2. Tap server name → "Disconnect"
3. Tap "Connect" again

**Fix 2:** Check server supports `tools/list`
- Not all MCP servers expose tools
- Some only provide resources or prompts
- Verify with server documentation

---

### "Permission denied" when executing tool

**Cause:** Server doesn't have file/database access

**Fix (Filesystem):**
```bash
# Check file permissions
ls -l ~/Documents/your-file.txt

# Ensure user running Jot can read the file
chmod +r ~/Documents/your-file.txt
```

**Fix (Database):**
- Verify connection string has correct username/password
- Check database user has SELECT permissions
- Test connection outside Jot first

---

### Slow Tool Execution

**Timeout:** 30 seconds per tool call

**If tools time out:**
- **Filesystem:** Reduce search scope (smaller directory)
- **Database:** Add indexes, simplify queries
- **HTTP:** Check network latency, optimize server response time

**Check activity log:**
1. Settings → MCP Servers → Activity
2. Find tool call
3. Check duration column
4. If > 25s, consider optimizing tool or server

---

## Building Custom MCP Servers

### Quick Start (Node.js)

```javascript
const { Server } = require('@modelcontextprotocol/sdk/server');
const { StdioServerTransport } = require('@modelcontextprotocol/sdk/server/stdio.js');

const server = new Server({
  name: "my-custom-server",
  version: "1.0.0"
});

// Define tools
server.setRequestHandler("tools/list", async () => ({
  tools: [
    {
      name: "greet",
      description: "Greet a user by name",
      inputSchema: {
        type: "object",
        properties: {
          name: { type: "string", description: "User's name" }
        },
        required: ["name"]
      }
    }
  ]
}));

// Handle tool execution
server.setRequestHandler("tools/call", async (request) => {
  if (request.params.name === "greet") {
    const name = request.params.arguments.name;
    return {
      content: [
        {
          type: "text",
          text: `Hello, ${name}! Welcome to custom MCP.`
        }
      ]
    };
  }
  throw new Error(`Unknown tool: ${request.params.name}`);
});

// Start stdio transport
const transport = new StdioServerTransport();
server.connect(transport);
```

**Save as `my-server.js`, then:**
```bash
node my-server.js
```

**Add to Jot:**
- **Transport:** stdio
- **Command:** `node`
- **Arguments:** `/full/path/to/my-server.js`

---

### MCP SDK Resources

**Official SDK:**
- TypeScript/JavaScript: `@modelcontextprotocol/sdk`
- Python: `mcp`
- Rust: Coming soon

**Documentation:**
- Spec: [spec.modelcontextprotocol.io](https://spec.modelcontextprotocol.io)
- Examples: [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- Community: [discord.gg/modelcontextprotocol](https://discord.gg/modelcontextprotocol)

**Server Examples:**
- Filesystem: [github.com/modelcontextprotocol/servers/tree/main/src/filesystem](https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem)
- GitHub: [github.com/modelcontextprotocol/servers/tree/main/src/github](https://github.com/modelcontextprotocol/servers/tree/main/src/github)
- PostgreSQL: [github.com/modelcontextprotocol/servers/tree/main/src/postgres](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres)

---

## Advanced Configuration

### Environment Variables

Pass secrets or config to MCP servers:

**In Jot (Settings → MCP Servers → Add Server → Advanced):**
- `GITHUB_TOKEN=ghp_xxxxxxxxxxxx`
- `DATABASE_URL=postgres://localhost/mydb`
- `API_KEY=sk_xxxxxxxxxxxx`

**Multiple variables:** Separate with newlines or commas

**Security:** Environment variables are stored encrypted in Jot's settings

---

### Transport Types

#### stdio (Command-Line)

**Best for:** Local tools, scripts, installed packages

**Pros:**
- Simple setup
- No network required
- Works with any executable

**Cons:**
- Must install locally
- Command path can be fragile

**Example config:**
```
Command: /usr/local/bin/mcp-server-filesystem
Arguments: ~/Documents /opt/data
```

#### HTTP (Web Server)

**Best for:** Remote services, Docker containers, shared infrastructure

**Pros:**
- Server can run anywhere
- Multiple clients can connect
- Easier to update (server-side only)

**Cons:**
- Requires network
- More complex security (auth, HTTPS)

**Example config:**
```
URL: http://localhost:3000/mcp
Headers: Authorization: Bearer token123
```

---

### Managing Multiple Servers

**Add multiple MCP servers** for different domains:

1. **Filesystem** → Access notes and documents
2. **GitHub** → Query code repositories
3. **PostgreSQL** → Business intelligence queries
4. **Custom API** → Company-specific tools

**All appear in one AI conversation:**
> "Read my meeting notes from last week (Filesystem), check if there's a GitHub issue about Project X (GitHub), and query how many users signed up that week (PostgreSQL)"

AI orchestrates multiple tool calls across servers, subject to your approval.

---

## FAQ

### Is MCP only for developers?

**No!** While custom servers require coding, using pre-built servers is straightforward:
1. Install with one command (npm/pip)
2. Add to Jot via settings UI
3. Approve tool requests as they come

### Does MCP work with cloud AI providers?

**Yes!** MCP works with:
- OpenAI (GPT-3.5, GPT-4)
- Anthropic (Claude)
- Google (Gemini)
- Local AI (Ollama, LM Studio)

MCP is AI-provider agnostic.

### Can MCP tools write files or modify data?

**Yes, if the server supports it.** Examples:
- Filesystem server with write permissions
- Database server with INSERT/UPDATE (not just SELECT)
- GitHub server with push access

**Jot's permission system applies:** Every write operation requires your approval.

### How much does MCP cost?

**MCP itself is free** (open protocol, open-source servers).

**Costs:**
- Cloud AI usage (per-token pricing from OpenAI, etc.)
- Local AI: Free (Ollama/LM Studio)
- Running your own MCP server: Server hosting costs (if remote)

### What's the difference between MCP and function calling?

**Function calling** (native to GPT/Claude):
- Cloud providers define available functions
- Limited to provider's predefined set
- No access to local files or databases

**MCP**:
- You define tools (or use community servers)
- Access to ANY data source (local files, databases, APIs)
- Runs locally with permission gating

**MCP extends function calling** to your own data.

### Can I use MCP on mobile?

**Not yet.** MCP is desktop-only (macOS, Windows, Linux) because:
- Mobile sandboxing prevents stdio transport
- File access is restricted on iOS/Android
- HTTP transport theoretically possible but not implemented

### Do I need to keep the MCP server running?

**stdio servers:** No. Jot starts them on-demand when connecting.  
**HTTP servers:** Yes. Must be running before Jot connects.

### Can I disable MCP entirely?

**Yes.** If you don't add any MCP servers, the feature is inactive and has zero overhead.

---

## Best Practices

### Start Small
- Begin with **one server** (filesystem recommended)
- Enable **one or two tools** initially
- Test with simple queries before complex workflows

### Review Tool Descriptions
- Read what each tool does before enabling
- Some tools have broad access (e.g., "search entire drive")
- Disable tools you won't use

### Monitor Activity Log
- Settings → MCP Servers → Activity
- Check for unexpected tool calls
- Investigate errors or slow executions

### Use Debug Logging Sparingly
- Only enable for troubleshooting
- **Remember:** Debug logs contain unredacted data
- Delete `~/Documents/Jot/mcp_debug.log` when done

### Limit Tool Scope
- Filesystem: Point to specific folder, not root (`/`)
- Database: Use read-only user, not admin
- HTTP: Restrict server to localhost unless trusted network

### Keep Servers Updated
```bash
# Update Node.js-based servers
npm update -g @modelcontextprotocol/server-*

# Update Python-based servers
pip install --upgrade mcp-server-*
```

---

## Getting Help

### MCP Resources
- **Website:** [modelcontextprotocol.io](https://modelcontextprotocol.io)
- **Spec:** [spec.modelcontextprotocol.io](https://spec.modelcontextprotocol.io)
- **GitHub:** [github.com/modelcontextprotocol](https://github.com/modelcontextprotocol)
- **Discord:** [discord.gg/modelcontextprotocol](https://discord.gg/modelcontextprotocol)

### Jot Support
- **Settings → Feedback** — Report MCP integration issues
- **Settings → Help → AI Features** — General AI guide
- **Debug logs:** Enable in MCP settings for troubleshooting

---

## Quick Reference

### Adding a Server

**stdio (Command-Line Server):**
1. Install: `npm install -g @modelcontextprotocol/server-NAME`
2. Settings → MCP Servers → Add Server
3. Transport: stdio
4. Command: `mcp-server-NAME` (or full path)
5. Arguments: Server-specific (e.g., directory path)
6. Connect → Review tools → Enable desired tools

**HTTP (Web Server):**
1. Start server (must be running)
2. Settings → MCP Servers → Add Server
3. Transport: HTTP
4. URL: `http://localhost:PORT/path`
5. Optional: Add auth headers
6. Connect → Review tools → Enable desired tools

### Approving Tool Requests

When AI needs to use a tool:
1. **Permission dialog appears**
2. Shows: Tool name, redacted parameters
3. Tap **"Allow"** to proceed or **"Deny"** to skip
4. AI incorporates result (if allowed) or continues without

### Managing Servers

**View all servers:** Settings → MCP Servers  
**Disconnect server:** Tap server → Disconnect  
**Remove server:** Tap server → Remove  
**View activity:** Settings → MCP Servers → Activity  
**Enable debug logging:** Settings → MCP Servers → Debug Logging toggle

---

**Last Updated:** 2026-01-13  
**Jot Version:** 1.0.10+  
**MCP Spec Version:** 1.0.0
