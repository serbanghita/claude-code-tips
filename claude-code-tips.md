# Claude Code CLI Tips (v2.1.74)

All 36 tips that Claude Code rotates through in the CLI, shown as `Tip:` messages in the spinner/status area. Each tip has conditions for when it appears and a cooldown between showings.

| # | ID | Tip Text | Cooldown | When Shown |
|---|-----|----------|----------|------------|
| 1 | `new-user-warmup` | Start with small features or bug fixes, tell Claude to propose a plan, and verify its suggested edits | 3 sessions | < 10 startups |
| 2 | `plan-mode-for-complex-tasks` | Use Plan Mode to prepare for a complex request before making changes. Press **shift+tab** twice to enable. | 5 sessions | Haven't used plan mode in 7+ days |
| 3 | `default-permission-mode-config` | Use /config to change your default permission mode (including Plan Mode) | 10 sessions | Used plan mode but haven't set a default mode |
| 4 | `git-worktrees` | Use git worktrees to run multiple Claude sessions in parallel. | 10 sessions | Only 1 worktree & 50+ startups |
| 5 | `terminal-setup` | Run /terminal-setup to enable convenient terminal integration like Shift + Enter for new line and more | 10 sessions | Terminal setup not yet installed |
| 6 | `shift-enter` | Press Shift+Enter to send a multi-line message *(or Option+Enter on Apple Terminal)* | 10 sessions | Terminal setup installed & 3+ startups |
| 7 | `shift-enter-setup` | Run /terminal-setup to enable Shift+Enter for new lines *(or Option+Enter on Apple Terminal)* | 10 sessions | Shift+Enter not installed |
| 8 | `memory-command` | Use /memory to view and manage Claude memory | 15 sessions | Never used memory |
| 9 | `theme-command` | Use /theme to change the color theme | 20 sessions | Always |
| 10 | `colorterm-truecolor` | Try setting environment variable COLORTERM=truecolor for richer colors | 30 sessions | COLORTERM not set |
| 11 | `status-line` | Use /statusline to set up a custom status line that will display beneath the input box | 25 sessions | No status line configured |
| 12 | `prompt-queue` | Hit Enter to queue up additional messages while Claude is working. | 5 sessions | Used prompt queue ≤ 3 times |
| 13 | `enter-to-steer-in-relatime` | Send messages to Claude while it works to steer Claude in real-time | 20 sessions | Always |
| 14 | `todo-list` | Ask Claude to create a todo list when working on complex tasks to track progress and remain on track | 20 sessions | Always |
| 15 | `vscode-command-install` | Open the Command Palette (Cmd+Shift+P) and run "Shell Command: Install 'code' command in PATH" to enable IDE integration | 0 (always) | In VS Code/Cursor/Windsurf on macOS without shell command |
| 16 | `ide-upsell-external-terminal` | Connect Claude to your IDE · /ide | 4 sessions | Not in IDE, no IDE connections, IDEs detected |
| 17 | `install-github-app` | Run /install-github-app to tag @claude right from your Github issues and PRs | 10 sessions | Haven't set up GitHub app |
| 18 | `install-slack-app` | Run /install-slack-app to use Claude in Slack | 10 sessions | Haven't installed Slack app |
| 19 | `permissions` | Use /permissions to pre-approve and pre-deny bash, edit, and MCP tools | 10 sessions | 10+ startups |
| 20 | `drag-and-drop-images` | Did you know you can drag and drop image files into your terminal? | 10 sessions | Not on SSH |
| 21 | `paste-images-mac` | Paste images into Claude Code using control+v (not cmd+v!) | 10 sessions | macOS only |
| 22 | `double-esc` | Double-tap esc to rewind the conversation to a previous point in time | 10 sessions | Not in a git repo |
| 23 | `double-esc-code-restore` | Double-tap esc to rewind the code and/or conversation to a previous point in time | 10 sessions | In a git repo |
| 24 | `continue` | Run claude --continue or claude --resume to resume a conversation | 10 sessions | Always |
| 25 | `rename-conversation` | Name your conversations with /rename to find them easily in /resume later | 15 sessions | 10+ startups |
| 26 | `custom-commands` | Create skills by adding .md files to .claude/skills/ in your project or ~/.claude/skills/ for skills that work in any project | 15 sessions | 10+ startups |
| 27 | `shift-tab` | Hit shift+tab to cycle between default mode, auto-accept edit mode, and plan mode | 10 sessions | Always |
| 28 | `image-paste` | Use ctrl+v to paste images from your clipboard | 20 sessions | Always |
| 29 | `custom-agents` | Use /agents to optimize specific tasks. Eg. Software Architect, Code Writer, Code Reviewer | 15 sessions | 5+ startups |
| 30 | `agent-flag` | Use --agent \<agent_name\> to directly start a conversation with a subagent | 15 sessions | 5+ startups |
| 31 | `desktop-app` | Run Claude Code locally or remotely using the Claude desktop app: clau.de/desktop | 15 sessions | Not on Linux |
| 32 | `desktop-shortcut` | Continue your session in Claude Code Desktop with /desktop | 15 sessions | Feature flag enabled, macOS/Windows |
| 33 | `web-app` | Run tasks in the cloud while you keep coding locally · clau.de/web | 15 sessions | Always |
| 34 | `mobile-app` | /mobile to use Claude Code from the Claude app on your phone | 15 sessions | Always |
| 35 | `opusplan-mode-reminder` | Your default model setting is Opus Plan Mode. Press shift+tab twice to activate Plan Mode and plan with Claude Opus. | 2 sessions | Using opusplan mode, haven't used plan mode in 3+ days |
| 36 | `frontend-design-plugin` | Working with HTML/CSS? Add the frontend-design plugin: /plugin install frontend-design | dynamic | Plugin system available |

Users can add custom tips via the `spinnerTipsOverride` setting in their config, with an option to either extend or replace the defaults.
