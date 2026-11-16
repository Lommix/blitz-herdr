# blitz-herdr

A [blitzdenk](https://github.com/Lommix/blitzdenk) plugin that reports the state
of the main agent to the [herdr](https://github.com/Lommix/herdr) pane the
session runs in.

When blitzdenk starts inside a herdr pane, the plugin watches the main agent and
keeps the pane status current: agent state, a short label, and tokens such as
the model, effort, context fill, throughput, queued messages, the active todo,
and the session cost.

## What gets reported

| Report      | Content                                                               |
| ----------- | --------------------------------------------------------------------- |
| Agent state | `working`, `blocked`, or `idle`, plus a one-line message              |
| State label | A label per state, for example `thinking`, `review patch`, `question` |
| Tokens      | `model`, `effort`, `ctx`, `tps`, `queued`, `todo`, `cost`             |

## Requirements

The plugin activates only inside a herdr pane. It reads these environment
variables, which herdr sets for each pane:

- `HERDR_ENV` — must be `1`
- `HERDR_PANE_ID` — the pane the reports belong to
- `HERDR_BIN_PATH` — the `herdr` binary used to submit reports

## Install

```lua
blitz.plugin("blitz-herdr", { url = "https://github.com/Lommix/blitz-herdr.git" })
-- or from a local checkout, which hot reloads:
-- blitz.plugin("blitz-herdr", { path = "~/Projects/lua/blitz-herdr" })

local herdr = require("blitz-herdr")
herdr.setup()
```
