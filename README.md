# Memirror

Memirror is an experimental memory layer for coding agents that preserves user and project context across sessions.

<img src="https://i.imgflip.com/1otri4.jpg" width="200" style="max-width:100%" />

## Install

Copy the contents of [`src/MEMIRROR.md`](./src/MEMIRROR.md) into your main agent instruction file such as `AGENTS.md` or `CLAUDE.md`.

Or copy [`src/MEMIRROR.md`](./src/MEMIRROR.md) into your repo and reference it from your existing instructions with something like:

```md
## Memory

Always read MEMIRROR.md upon first user's message
```

## How It Works

Memirror gives the agent a small file-based memory model. It stores durable user traits, project context and reusable past decisions in a few markdown files instead of letting that context disappear between sessions. Part of the model is profiling the user and inferring a compact working persona the agent can reuse later.

Relevant files:

- `~/.agents/memory/PROFILE.md`: stable cross-project user traits
- `~/.agents/memory/MEMORY.md`: pinned global reminders
- `~/.agents/memory/memories/*.md`: atomic global memories
- `.agents/memory/MEMORY.md`: pinned repo memory
- `.agents/memory/memories/*.md`: atomic repo memories

Flow:

- Read on the first task in a conversation and when entering a repo
- Read pinned files first then only the few atomic memories that look relevant
- Re-read only if memory changed, the task shifted or a conflict needs checking
- Write after a task only when something durable and reusable was learned either about the user or project
- Skip writing routine one-off details and keep pinned files short

Memory is split into global files for cross-project traits and local files for repo-specific context. The goal is to keep it compact, explicit and easy to maintain.
