<div align="center">

# Claude Canvas

### External Monitor for Claude Code

[![Bun](https://img.shields.io/badge/Bun-000000?style=for-the-badge&logo=bun&logoColor=white)](https://bun.sh)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![tmux](https://img.shields.io/badge/tmux-1BB91F?style=for-the-badge&logo=tmux&logoColor=white)](https://github.com/tmux/tmux)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

**Give Claude Code its own display. See AI work on a second screen in real-time.**

*Spawn interactive TUI interfaces for emails, calendars, flight bookings, and more.*

![Claude Canvas Screenshot](media/screenshot.png)

</div>

---

## Why Use This?

| Problem | Solution |
|---------|----------|
| Claude Code output is cramped in the terminal | **External display** in a dedicated tmux pane |
| Can't visualize Claude's work in progress | **Real-time updates** as Claude works |
| Terminal gets cluttered with AI responses | **Clean separation** - your terminal stays focused |
| No way to show interactive UIs | **Full TUI toolkit** for rich interfaces |

---

## Quick Start

### Prerequisites

- [Bun](https://bun.sh) - Fast JavaScript runtime
- [tmux](https://github.com/tmux/tmux) - Terminal multiplexer

### Installation

```bash
# Add the marketplace
/plugin marketplace add dvdsgl/claude-canvas

# Install the canvas plugin
/plugin install canvas@claude-canvas
```

### Usage

Once installed, Claude Canvas automatically:
- Spawns in a tmux split pane
- Displays Claude Code output externally
- Updates in real-time as Claude works

---

## What You Can Display

| Interface | Description |
|-----------|-------------|
| **Email Viewer** | Interactive email drafts and threads |
| **Calendar** | Scheduling interfaces |
| **Flight Booking** | Search and booking flows |
| **Code Preview** | Syntax-highlighted code output |
| **Data Tables** | Structured data visualization |
| **Custom TUIs** | Build your own interfaces |

---

## Tech Stack

```
Runtime     Bun (not Node.js)
Language    TypeScript
Frontend    HTML imports with Bun.serve()
Terminal    tmux split panes
```

---

## Development

```bash
# Clone the repo
git clone https://github.com/DeadManOfficial/claude-canvas.git
cd claude-canvas

# Install dependencies
bun install

# Run in development mode
bun --hot ./index.ts

# Run tests
bun test
```

---

## How It Works

1. Claude Canvas runs as a Bun server
2. Connects to Claude Code via tmux
3. Spawns dedicated display panes
4. Streams Claude's output in real-time
5. Renders interactive TUI components

```
┌─────────────────────┬─────────────────────┐
│                     │                     │
│   Your Terminal     │   Claude Canvas     │
│                     │                     │
│   (Claude Code)     │   (External View)   │
│                     │                     │
└─────────────────────┴─────────────────────┘
```

---

## Requirements

- Bun runtime
- tmux installed and running
- Claude Code CLI

---

## License

MIT License

---

<div align="center">

**Created by DEADMAN**

[![GitHub](https://img.shields.io/badge/DeadManOfficial-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DeadManOfficial)

*Give Claude its own screen. Work smarter, not harder.*

</div>
