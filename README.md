<div align="center">

<br>

# Claude Canvas

**External Monitor for Claude Code**

See AI work on a second screen in real-time with tmux split panes.

<br>

<a href="https://github.com/DeadManOfficial/claude-canvas">
  <img src="https://img.shields.io/badge/GitHub-Source-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
</a>
<a href="https://bun.sh">
  <img src="https://img.shields.io/badge/Bun-Runtime-000000?style=for-the-badge&logo=bun&logoColor=white" alt="Bun" />
</a>
<a href="https://www.typescriptlang.org">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
</a>

<br><br>

</div>

---

## Install

```bash
# Prerequisites: Bun + tmux

# Add marketplace & install
/plugin marketplace add dvdsgl/claude-canvas
/plugin install canvas@claude-canvas
```

---

## Features

| Feature | Description |
|---------|-------------|
| **External Display** | Dedicated tmux pane for Claude output |
| **Real-time Updates** | Watch Claude work as it happens |
| **Interactive TUIs** | Emails, calendars, flight booking |
| **Code Preview** | Syntax-highlighted output |
| **Custom Interfaces** | Build your own displays |

---

## How It Works

```
┌─────────────────────┬─────────────────────┐
│                     │                     │
│   Your Terminal     │   Claude Canvas     │
│   (Claude Code)     │   (External View)   │
│                     │                     │
└─────────────────────┴─────────────────────┘
```

1. Runs as a Bun server
2. Connects via tmux
3. Streams Claude output in real-time
4. Renders interactive TUI components

---

## Development

```bash
git clone https://github.com/DeadManOfficial/claude-canvas.git
cd claude-canvas
bun install
bun --hot ./index.ts
```

---

## Related

- **[mcp-auditor](https://github.com/DeadManOfficial/mcp-auditor)** — Security & compliance auditor for Claude
- **[token-optimization](https://github.com/DeadManOfficial/token-optimization)** — Save 30-50% on API costs
- **[AI-Updates](https://github.com/DeadManOfficial/AI-Updates)** — Daily AI intelligence briefs

---

## License

MIT

---

<div align="center">

<br>

<a href="https://twitter.com/DeadManAI">
  <img src="https://img.shields.io/badge/X-000000?style=flat&logo=x&logoColor=white" alt="X" />
</a>
<a href="https://youtube.com/@DeadManAI">
  <img src="https://img.shields.io/badge/YouTube-FF0000?style=flat&logo=youtube&logoColor=white" alt="YouTube" />
</a>
<a href="https://tiktok.com/@DeadManAI">
  <img src="https://img.shields.io/badge/TikTok-000000?style=flat&logo=tiktok&logoColor=white" alt="TikTok" />
</a>

<br><br>

<sub>**BUILD > BUY**</sub>

</div>
