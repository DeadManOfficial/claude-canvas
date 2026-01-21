# Claude Canvas - Complete Setup & Integration Guide
**Created:** 2026-01-10
**Repository:** https://github.com/dvdsgl/claude-canvas
**Status:** Comprehensive Setup Instructions

---

## 📚 TABLE OF CONTENTS

1. [What is Claude Canvas?](#what-is-claude-canvas)
2. [Prerequisites](#prerequisites)
3. [Installation Guide](#installation-guide)
4. [Configuration](#configuration)
5. [Beneficial MCP Servers](#beneficial-mcp-servers)
6. [Claude Code Plugins](#claude-code-plugins)
7. [Usage Examples](#usage-examples)
8. [Advanced Workflows](#advanced-workflows)
9. [Troubleshooting](#troubleshooting)
10. [Additional Resources](#additional-resources)

---

## 🎨 WHAT IS CLAUDE CANVAS?

### Overview
**Claude Canvas** is a Terminal User Interface (TUI) toolkit that extends Claude Code's display capabilities. It enables creation of interactive terminal interfaces for applications like:
- Email clients
- Calendar systems
- Flight booking platforms
- Custom interactive dashboards
- And more!

**Repository:** https://github.com/dvdsgl/claude-canvas
**Stars:** 916 ⭐
**License:** MIT
**Language:** TypeScript (99.9%)

### Key Features
- ✅ **Interactive TUIs** - Spawn interactive terminal interfaces
- ✅ **tmux Integration** - Display canvases in split panes
- ✅ **Isolated Applications** - Run apps in separate tmux panes
- ✅ **Plugin Ecosystem** - Integrates with Claude Code plugins
- ✅ **Bun-Powered** - Fast JavaScript/TypeScript runtime

### Important Note
⚠️ **Proof of Concept** - Developers state this is a proof-of-concept without official support. Use in production at your own discretion.

---

## 🔧 PREREQUISITES

### 1. Claude Code
Must have Claude Code CLI installed and configured.

**Installation:**
```bash
# Follow official installation guide at:
https://code.claude.com/docs/en/getting-started
```

### 2. Bun Runtime ⭐
**What it is:** Fast all-in-one JavaScript runtime (bundler, test runner, package manager)

**Windows Installation:**
```powershell
# PowerShell (Recommended)
powershell -c "irm bun.sh/install.ps1 | iex"

# OR via npm
npm install -g bun

# Verify installation
bun --version
```

**Linux/macOS Installation:**
```bash
curl -fsSL https://bun.sh/install | bash

# Verify
bun --version
```

**TypeScript Support:**
```bash
# Install TypeScript definitions
bun add -d @types/bun
```

### 3. tmux (Terminal Multiplexer) ⭐
**What it is:** Enables canvases to display in split panes

**Windows Installation:**
```bash
# Via WSL (Windows Subsystem for Linux)
wsl --install
# Then in WSL:
sudo apt-get update
sudo apt-get install tmux
```

**Linux Installation:**
```bash
# Ubuntu/Debian
sudo apt-get install tmux

# Fedora
sudo dnf install tmux

# Arch
sudo pacman -S tmux
```

**macOS Installation:**
```bash
brew install tmux
```

**Verify Installation:**
```bash
tmux -V
# Expected: tmux 3.x or higher
```

---

## 📦 INSTALLATION GUIDE

### Step 1: Register the Marketplace

```bash
# In Claude Code CLI
/plugin marketplace add dvdsgl/claude-canvas
```

**Expected Output:**
```
✓ Marketplace added: dvdsgl/claude-canvas
```

### Step 2: Install the Plugin

```bash
# In Claude Code CLI
/plugin install canvas@claude-canvas
```

**Expected Output:**
```
✓ Installing canvas from claude-canvas marketplace...
✓ Plugin installed successfully
```

### Step 3: Verify Installation

```bash
# List installed plugins
/plugin list

# Should show:
# canvas (from claude-canvas marketplace)
```

---

## ⚙️ CONFIGURATION

### Basic tmux Configuration

Create or edit `~/.tmux.conf`:

```bash
# ~/.tmux.conf - Claude Canvas Optimized

# Increase scrollback buffer (important for Claude Code)
set-option -g history-limit 50000

# Enable mouse support
set -g mouse on

# Split panes using | and -
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

# Reload config
bind r source-file ~/.tmux.conf \; display "Config reloaded!"

# Switch panes using Alt+Arrow without prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Better pane resizing
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# Status bar customization
set -g status-position bottom
set -g status-bg colour234
set -g status-fg colour137
set -g status-left ''
set -g status-right '#[fg=colour233,bg=colour241,bold] %d/%m #[fg=colour233,bg=colour245,bold] %H:%M:%S '
set -g status-right-length 50
set -g status-left-length 20
```

**Apply Configuration:**
```bash
tmux source-file ~/.tmux.conf
```

### Recommended tmux Layout for Claude Canvas

```bash
# Start tmux session
tmux new-session -s claude-canvas

# Split horizontally (Claude Code on top, Canvas below)
tmux split-window -v

# Split canvas pane vertically (multiple canvases)
tmux select-pane -t 1
tmux split-window -h

# Final layout:
# ┌─────────────────────┐
# │   Claude Code       │
# ├──────────┬──────────┤
# │ Canvas 1 │ Canvas 2 │
# └──────────┴──────────┘
```

---

## 🚀 BENEFICIAL MCP SERVERS

### What is MCP?
**Model Context Protocol** - Universal standard for AI-tool integrations. Think "USB-C for AI"

### Top 10 Must-Have MCP Servers

#### 1. **GitHub MCP Server** ⭐⭐⭐⭐⭐
**Purpose:** Direct interaction with repositories, issues, PRs, CI/CD

**Installation:**
```bash
# Add to Claude Code config
/mcp add github
```

**Capabilities:**
- Create/manage repositories
- Open/close issues
- Review pull requests
- Trigger workflows
- Manage branches

#### 2. **PostgreSQL MCP Server** ⭐⭐⭐⭐⭐
**Purpose:** Natural language database querying

**Installation:**
```bash
/mcp add postgresql
```

**Configuration:**
```json
{
  "mcpServers": {
    "postgresql": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgresql", "postgresql://user:pass@localhost/db"]
    }
  }
}
```

**Use Cases:**
- Query databases with natural language
- Schema exploration
- Data analysis
- Migration assistance

#### 3. **Playwright MCP Server** ⭐⭐⭐⭐⭐
**Purpose:** Browser automation and web scraping

**Installation:**
```bash
/mcp add playwright
```

**Capabilities:**
- Test automation
- Web scraping
- Screenshots/PDFs
- Accessibility snapshots

#### 4. **Notion MCP Server** ⭐⭐⭐⭐
**Purpose:** Access Notion workspace

**Installation:**
```bash
/mcp add notion
```

**Capabilities:**
- Read/create pages
- Manage databases
- Add comments
- Search workspace

#### 5. **Figma MCP Server** ⭐⭐⭐⭐
**Purpose:** Design-to-code workflows

**Installation:**
```bash
/mcp add figma
```

**Capabilities:**
- Extract designs
- Generate code from mockups
- Access design tokens
- Export assets

#### 6. **Slack MCP Server** ⭐⭐⭐⭐
**Purpose:** Team communications

**Installation:**
```bash
/mcp add slack
```

**Capabilities:**
- Send messages
- Read channels
- Manage threads
- File uploads

#### 7. **Apidog MCP Server** ⭐⭐⭐⭐
**Purpose:** API specification access

**Installation:**
```bash
/mcp add apidog
```

**Capabilities:**
- Access API documentation
- Generate accurate code
- Test endpoints
- Mock APIs

#### 8. **Filesystem MCP Server** ⭐⭐⭐⭐⭐
**Purpose:** File operations

**Installation:**
```bash
/mcp add filesystem
```

**Capabilities:**
- Read/write files
- Directory management
- File search
- Permission handling

#### 9. **Web Search MCP Server** ⭐⭐⭐⭐⭐
**Purpose:** Internet search capabilities

**Installation:**
```bash
/mcp add brave-search
# OR
/mcp add google-search
```

**Capabilities:**
- Real-time web search
- News aggregation
- Research assistance
- Fact-checking

#### 10. **Database MCP Servers** ⭐⭐⭐⭐
**Supports:** MySQL, SQLite, MongoDB, Redis

**Installation:**
```bash
# MySQL
/mcp add mysql

# SQLite
/mcp add sqlite

# MongoDB
/mcp add mongodb
```

### MCP Configuration Best Practices

**Edit config directly** (better than CLI for complex setups):
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your_token_here"
      }
    },
    "postgresql": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgresql"],
      "env": {
        "DATABASE_URL": "postgresql://localhost/mydb"
      }
    },
    "playwright": {
      "command": "npx",
      "args": ["-y", "@executeautomation/playwright-mcp-server"]
    }
  }
}
```

**Config Location:**
- **Windows:** `%APPDATA%\Claude\config.json`
- **macOS:** `~/Library/Application Support/Claude/config.json`
- **Linux:** `~/.config/Claude/config.json`

---

## 🔌 CLAUDE CODE PLUGINS

### Official Marketplace

**Auto-available** when you start Claude Code (maintained by Anthropic)

**Includes:**
- Code intelligence plugins (LSP integration)
- Jump to definitions
- Find references
- Type error detection

### Top Community Plugins

#### 1. **Production Plugin** ⭐⭐⭐⭐⭐
**Features:**
- 30+ slash commands
- Git automation
- Documentation generation
- Job queues
- Code quality tools
- 6 specialized agents (security review, etc.)

**Installation:**
```bash
/plugin marketplace add <production-marketplace-url>
/plugin install production-plugin
```

#### 2. **Auto-Config Linting Plugin** ⭐⭐⭐⭐
**Features:**
- Auto-configures linting
- Typechecking setup
- Parallel agent-based fixing

#### 3. **Repomix Plugin** ⭐⭐⭐⭐
**Features:**
- Analyze codebases
- Pack code for AI
- Natural language commands

**Installation:**
```bash
/plugin marketplace add repomix
/plugin install repomix
```

### Plugin Discovery Resources

**Official:**
- [Claude Plugins Official](https://github.com/anthropics/claude-plugins-official)
- [Claude Code Docs - Plugins](https://code.claude.com/docs/en/discover-plugins)

**Community:**
- [Awesome Claude Plugins](https://github.com/ccplugins/awesome-claude-code-plugins)
- [Claude Marketplaces](https://claudemarketplaces.com/)
- [Claude Code Marketplace](https://claudecodemarketplace.com/)

---

## 💡 USAGE EXAMPLES

### Basic Canvas Usage

```bash
# Start tmux session
tmux new-session -s dev

# Start Claude Code in one pane
claude

# In Claude Code, spawn a canvas
/canvas create email-client

# Canvas appears in separate tmux pane
```

### Example: Email Client Canvas

```typescript
// Claude creates interactive email TUI
// Features:
// - Inbox list
// - Email preview
// - Compose interface
// - Search functionality
```

### Example: Calendar Canvas

```typescript
// Interactive calendar TUI
// Features:
// - Month/Week/Day views
// - Event creation
// - Reminders
// - Integration with Google Calendar (via MCP)
```

### Example: Flight Booking Canvas

```typescript
// Flight search and booking TUI
// Features:
// - Destination search
// - Date picker
// - Price comparison
// - Booking confirmation
```

---

## 🎯 ADVANCED WORKFLOWS

### Workflow 1: Full-Stack Development

```bash
# Layout:
# ┌─────────────────────────────────┐
# │   Claude Code (Main)            │
# ├──────────┬──────────┬───────────┤
# │  Logs    │  Tests   │  Database │
# └──────────┴──────────┴───────────┘

# Create session
tmux new-session -s fullstack

# Split into 4 panes
tmux split-window -v
tmux split-window -h
tmux select-pane -t 0
tmux split-window -h

# Pane assignments:
# 0: Claude Code
# 1: Logs (tail -f logs/app.log)
# 2: Test runner (npm run test:watch)
# 3: Database client (psql -d mydb)
```

### Workflow 2: AI-Assisted Debugging

```bash
# Use MCP servers + Canvas together

# 1. GitHub MCP - Fetch code
# 2. Canvas - Display stack trace
# 3. Database MCP - Query error logs
# 4. Playwright MCP - Reproduce bug in browser
# 5. Claude analyzes and suggests fixes
```

### Workflow 3: Research & Development

```bash
# Layout:
# ┌─────────────────────────────────┐
# │   Claude Code                   │
# ├──────────┬──────────────────────┤
# │  Web     │  Documentation       │
# │  Search  │  Canvas              │
# └──────────┴──────────────────────┘

# Use Web Search MCP in one canvas
# Use Notion MCP to save findings in another
# Claude Code orchestrates research
```

---

## 🐛 TROUBLESHOOTING

### Issue 1: Plugin Not Found

**Error:**
```
Error: Marketplace not found: claude-canvas
```

**Solution:**
```bash
# Ensure correct marketplace URL
/plugin marketplace list

# Re-add marketplace
/plugin marketplace add dvdsgl/claude-canvas
```

### Issue 2: Bun Not Found

**Error:**
```
Error: bun command not found
```

**Solution:**
```bash
# Verify Bun installation
bun --version

# If not installed:
# Windows PowerShell:
powershell -c "irm bun.sh/install.ps1 | iex"

# Add to PATH if needed
# Windows: Add C:\Users\<username>\.bun\bin to PATH
# Linux/macOS: Add to ~/.bashrc or ~/.zshrc
export PATH="$HOME/.bun/bin:$PATH"
```

### Issue 3: tmux Not Starting

**Error:**
```
tmux: command not found
```

**Solution:**
```bash
# Windows: Use WSL
wsl --install
# Then install tmux in WSL:
sudo apt-get install tmux

# Linux:
sudo apt-get install tmux  # Debian/Ubuntu
sudo dnf install tmux      # Fedora
sudo pacman -S tmux        # Arch

# macOS:
brew install tmux
```

### Issue 4: Canvas Not Displaying

**Error:**
Canvas doesn't appear in separate pane

**Solution:**
```bash
# Ensure tmux is running
tmux list-sessions

# If not in tmux session:
tmux new-session -s canvas-test

# Then try creating canvas again
```

### Issue 5: MCP Server Connection Failed

**Error:**
```
Error: Failed to connect to MCP server
```

**Solution:**
```bash
# Check MCP config
cat ~/.config/Claude/config.json

# Verify server installation
npx -y @modelcontextprotocol/server-github --version

# Check environment variables
echo $GITHUB_TOKEN

# Restart Claude Code
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation
- [Claude Code Docs](https://code.claude.com/docs)
- [MCP Documentation](https://modelcontextprotocol.io/docs)
- [Claude Canvas GitHub](https://github.com/dvdsgl/claude-canvas)
- [Bun Documentation](https://bun.com/)
- [tmux Manual](https://man7.org/linux/man-pages/man1/tmux.1.html)

### Community Resources
- [Claude Code + tmux Workflow](https://www.blle.co/blog/claude-code-tmux-beautiful-terminal)
- [Best MCP Servers Guide](https://mcpcat.io/guides/best-mcp-servers-for-claude-code/)
- [Awesome Claude Plugins](https://github.com/ccplugins/awesome-claude-code-plugins)

### Tutorials
- [Using tmux with Claude Code](https://hboon.com/using-tmux-with-claude-code/)
- [MCP Integration Guide](https://www.getclockwise.com/blog/claude-code-mcp-tools-integration)
- [Configuring MCP Tools](https://scottspence.com/posts/configuring-mcp-tools-in-claude-code)

### Video Guides
- [Vibe Coding with tmux and Claude Code](https://nuttakitkundum.medium.com/vibe-coding-anytime-anywhere-with-tmux-tailscale-and-claude-code-fda01f3c5cd2)

---

## 🎯 QUICK START CHECKLIST

### Phase 1: Prerequisites (15 minutes)
- [ ] Install Claude Code
- [ ] Install Bun runtime
- [ ] Install tmux
- [ ] Create tmux config file
- [ ] Verify all installations

### Phase 2: Canvas Setup (5 minutes)
- [ ] Add canvas marketplace
- [ ] Install canvas plugin
- [ ] Verify plugin installation
- [ ] Test canvas creation

### Phase 3: MCP Servers (20 minutes)
- [ ] Edit Claude config.json
- [ ] Add GitHub MCP server
- [ ] Add Database MCP servers
- [ ] Add Playwright MCP server
- [ ] Test MCP connections

### Phase 4: Plugins (10 minutes)
- [ ] Browse plugin marketplaces
- [ ] Install production plugins
- [ ] Install Repomix
- [ ] Test plugin commands

### Phase 5: Advanced Setup (30 minutes)
- [ ] Create custom tmux layouts
- [ ] Configure workflows
- [ ] Set up keyboard shortcuts
- [ ] Create test canvases

**Total Setup Time:** ~1.5 hours

---

## 💎 RECOMMENDED TOOLS & EXTENSIONS

### Essential MCP Servers (Priority Order)
1. ✅ **Filesystem** - File operations
2. ✅ **GitHub** - Version control
3. ✅ **Web Search** - Research
4. ✅ **PostgreSQL** - Database access
5. ✅ **Playwright** - Browser automation

### Essential Plugins (Priority Order)
1. ✅ **Official Anthropic Marketplace** - Code intelligence
2. ✅ **Repomix** - Codebase analysis
3. ✅ **Production Plugin** - Git automation

### Workflow Enhancements
1. ✅ **tmux Resurrect** - Save/restore sessions
2. ✅ **tmux Continuum** - Auto-save sessions
3. ✅ **fzf** - Fuzzy finder for tmux
4. ✅ **bat** - Better cat with syntax highlighting

---

## 🚀 NEXT STEPS

### Immediate Actions
1. **Install Prerequisites** - Bun, tmux, Claude Code
2. **Setup Canvas** - Add marketplace, install plugin
3. **Test Basic Usage** - Create simple canvas
4. **Add Core MCP Servers** - GitHub, Filesystem, Web Search

### Short-Term Goals
1. **Configure tmux** - Custom layouts, shortcuts
2. **Install Plugins** - Production tools, Repomix
3. **Create Workflows** - Dev, debug, research setups
4. **Practice with Canvases** - Email, calendar examples

### Long-Term Mastery
1. **Advanced MCP** - Custom MCP servers
2. **Custom Canvases** - Build your own TUIs
3. **Automation** - Workflow automation with canvases
4. **Team Collaboration** - Shared tmux sessions

---

## Tags
`#claude-canvas` `#claude-code` `#mcp` `#tmux` `#bun` `#plugins` `#setup-guide` `#tui` `#terminal` `#development`

---

## Sources & References

### Research Sources
- [Claude Canvas GitHub](https://github.com/dvdsgl/claude-canvas)
- [Claude Code MCP Integration](https://code.claude.com/docs/en/mcp)
- [Best MCP Servers for Claude Code](https://mcpcat.io/guides/best-mcp-servers-for-claude-code/)
- [Top 10 MCP Servers 2026](https://roobia.medium.com/the-10-must-have-mcp-servers-for-claude-code-2025-developer-edition-43dc3c15c887)
- [Claude Code Plugins Marketplace](https://code.claude.com/docs/en/discover-plugins)
- [tmux + Claude Code Workflow](https://www.blle.co/blog/claude-code-tmux-beautiful-terminal)
- [Bun Installation Guide](https://bun.com/)
- [Model Context Protocol Docs](https://modelcontextprotocol.io/)

---

**Last Updated:** 2026-01-10
**Version:** 1.0.0
**Status:** ✅ **PRODUCTION-READY GUIDE**
