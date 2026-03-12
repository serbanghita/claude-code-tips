# How I Researched Claude Code CLI Tips

## Finding the binary

1. Ran `which claude` → `/Users/serbanghita/.local/bin/claude`
2. Ran `claude --version` → `2.1.74`
3. Found the actual binary at `~/.local/share/claude/versions/2.1.74` — a Mach-O 64-bit ARM64 executable (Bun-compiled)

## Initial string extraction from the binary

Used `strings` on the binary to grep for patterns like `"Tip:"`, `"Use /"`, `"Run /"`, `"Press "`. This surfaced some tips but was noisy — the binary includes strings from bundled dependencies (ripgrep, Bun runtime, ugrep, etc.) that had to be filtered out.

## Getting the actual source code

The binary is a compiled Bun executable, making it hard to read structured code from `strings` output alone. Instead:

1. Ran `npm pack @anthropic-ai/claude-code` to download the npm package tarball
2. Extracted it to `/tmp/package/` — the key file is `cli.js`, a large minified JavaScript bundle

## Tracing the tip system in the minified source

1. **Found the spinner component**: Searched for `"Tip: "` in `cli.js` and found it rendered as `` `Tip: ${l}` `` inside a React component
2. **Found the random tip selector**: Traced `zRK()` → calls `MD(oK_())` → `oK_()` returns `wvq` — but this turned out to be the **spinner verbs** array (1282 funny loading words like "Clauding", "Percolating"), not the tips
3. **Found the actual tips array**: Searched for known tip strings like `"Use /clear"` and `"Use /agents"`. Found them on line 7088 of `cli.js` in a function called `fS1()` that assembles tips from two arrays: `ewz` (the main tips) and `AOz` (empty)
4. **Extracted the tips data structure**: The `ewz` array contains 36 tip objects, each with:
   - `id` — unique identifier
   - `content` — async function returning the tip string
   - `cooldownSessions` — minimum sessions between re-showing
   - `isRelevant` — async function checking if the tip should appear (based on user state, platform, startup count, etc.)

## Key discovery: tips are contextual

The tips aren't a simple static list. Each tip has an `isRelevant()` function that checks conditions like:
- `D1().numStartups` — how many times the user has launched Claude Code
- `d8.terminal` — which terminal is being used (Apple Terminal, VS Code, etc.)
- `R8()` — which OS (macOS, Linux, Windows)
- `d8.isSSH()` — whether running over SSH
- Feature-specific state like `shiftEnterKeyBindingInstalled`, `memoryUsageCount`, `githubActionSetupCount`

There's also a `spinnerTipsOverride` config option that lets users add custom tips or replace the defaults entirely.

## Also found (but separate from tips)

- **Spinner verbs**: 1282 humorous gerunds shown while Claude is thinking (e.g., "Accomplishing", "Clauding", "Flibbertigibbeting")
- **Inline contextual hints**: Two hardcoded tips shown in the input area: "Use /clear to start fresh..." and "Use /btw to ask a quick side question..."
- **Startup tips**: "Tip: You can launch Claude Code with just \`claude\`" and "Tip: You can enable auto-connect to IDE in /config or with the --ide flag"
