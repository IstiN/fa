# Fa (`IstiN/fa`)

Umbrella repository for the **[Fa](https://fa1.dev)** multi-repository ecosystem under `IstiN`, wired with the **FA Universal Agent Workflow** (`IstiN/dmtools-agentic-workflows/.github/workflows/fa-universal.yml@main`) and `.dmtools/repositories.json`.

## Child Repositories (`.dmtools/repositories.json`)

Triggering the `FA Universal Agent` workflow (or running `dmtools-agents/setup/checkout.sh` locally) clones/updates all Fa ecosystem repositories into `./dependencies/<repo>/`:

### Core 5 Repositories
- **[`IstiN/flutter_agent_harness`](https://github.com/IstiN/flutter_agent_harness)** (`dependencies/flutter_agent_harness`) — Core pure-Dart SDK, `fa` CLI, Flutter app (`flutter_app/`), `fa_ui`, `fa_llm`, `dap_hub`, browser extension, and Office add-in.
- **[`IstiN/fa_network`](https://github.com/IstiN/fa_network)** (`dependencies/fa_network`) — Go REST+WS edge relay (`https://network.fa1.dev`) and webhook bridge to DAP E2E-encrypted channels.
- **[`IstiN/fa_cube`](https://github.com/IstiN/fa_cube)** (`dependencies/fa_cube`) — Declarative command sandboxing policy engine and OS kernel backends (`sandbox-exec`, `unshare`, Windows Job Object).
- **[`IstiN/fa_widgets`](https://github.com/IstiN/fa_widgets)** (`dependencies/fa_widgets`) — Curated JS widget catalog (`catalog.json` + widget zips) and `fa_widgets_tool` validator.
- **[`IstiN/fa_hub_client`](https://github.com/IstiN/fa_hub_client)** (`dependencies/fa_hub_client`) — DAP/1 signed WebSocket hub client (`MessagingRepository`).

### Supporting First-Party Packages
- **[`IstiN/flutter_agent_memory`](https://github.com/IstiN/flutter_agent_memory)** (`dependencies/flutter_agent_memory`) — LLM-powered Obsidian-compatible Markdown knowledge base (`memory_*` tools).
- **[`IstiN/fa_exec_env`](https://github.com/IstiN/fa_exec_env)** (`dependencies/fa_exec_env`) — `ExecutionEnv` portability boundary (FileSystem + Shell) and `CancelToken`.
- **[`IstiN/flutter_js_widget_runtime`](https://github.com/IstiN/flutter_js_widget_runtime)** (`dependencies/flutter_js_widget_runtime`) — Flutter renderer for `jsr.*` JavaScript widgets (`pub: js_widget_runtime`).
- **[`IstiN/js_widget_runtime`](https://github.com/IstiN/js_widget_runtime)** (`dependencies/js_widget_runtime`) — Platform-neutral `jsr` UI contract and conformance fixtures.
- **[`IstiN/quickjs_runtime`](https://github.com/IstiN/quickjs_runtime)** (`dependencies/quickjs_runtime`) — Pure-Dart QuickJS `dart:ffi` runtime with synchronous host callbacks.
- **[`IstiN/dart_tui`](https://github.com/IstiN/dart_tui)** (`dependencies/dart_tui`) — Elm-style terminal UI framework powering the `fa` CLI.
- **[`IstiN/yoxterm`](https://github.com/IstiN/yoxterm)** (`dependencies/yoxterm`) — High-performance fork of `xterm.dart` (`Terminal` + `TerminalView`) used for PTY terminal emulation (`vendor/xterm`) and `fa` CLI visual screenshot tests (`flutter_app/test/cli_visual/`).
- **[`IstiN/pty2`](https://github.com/IstiN/pty2)** (`dependencies/pty2`) — Pseudo-terminal (PTY) fork with `pid` access (`vendor/pty2`) driving live CLI PTY integration & visual tests.

## Usage

### Local Checkout
```bash
GH_TOKEN=$(gh auth token) bash ../dmtools-agents/setup/checkout.sh
```
All repositories are cloned into `./dependencies/<repo>/` (override destination with `--dest <dir>`).

### Chatting with `@fa` (Universal Workflow)
- Mention `@fa` in any Issue or Pull Request comment in `IstiN/fa`
- Or trigger via `workflow_dispatch` / `repository_dispatch` (`fa-trigger`, `fa-webhook`) from `https://network.fa1.dev`
- `fa-universal` automatically checks out all repositories from `.dmtools/repositories.json` into `./dependencies/`, restores the conversation session from `fa-sess/<session_key>`, and persists long-term cross-repo memory in `.fah/memory`.
