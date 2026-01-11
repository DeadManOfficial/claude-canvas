# Claude Canvas - External Monitor

**Identity:** External monitor for Claude Code sessions.
**Ecosystem:** [DeadManOfficial](https://github.com/DeadManOfficial)

---

## PURPOSE

Give Claude Code an external monitor - visualize sessions, track progress, display context externally.

---

## TECH STACK

- **Runtime:** Bun (not Node.js)
- **Language:** TypeScript
- **Frontend:** HTML imports with Bun.serve()

---

## RULES

See `.claude/rules/bun.md` for Bun-specific development rules:
- Use `bun` instead of `node`, `npm`, `pnpm`
- Use `Bun.serve()` instead of express
- Use `bun:test` instead of jest

---

## COMMANDS

```bash
# Install dependencies
bun install

# Run development
bun --hot ./index.ts

# Run tests
bun test
```

---

Created-By: DEADMAN
