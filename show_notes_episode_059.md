# AgentStack Daily EP059 - Hermes Agent 0.15.x, Codex 0.135, Claude Code 2.1.157, Opus 4.8, Browser MCP, and Usage Telemetry

## Release Coverage Check

- **OpenClaw** - Latest stable verified: `v2026.5.27`, published 2026-05-28T11:41:42Z from GitHub releases. Recent episode version tags detected: `v2026.5.27` and `v2026.5.26`. Selected missing versions: none for stable coverage. Prerelease `v2026.5.28-beta.3` was visible on 2026-05-29 and belongs in the watch lane, not the stable release block.
- **Hermes Agent** - Latest stable verified: `v2026.5.29.2` / `v0.15.2`, published 2026-05-29T13:37:26Z from GitHub releases. Recent episode version tags detected: `v2026.5.16`. Selected missing versions: `v2026.5.28`, `v2026.5.29`, and `v2026.5.29.2`.
- **OpenAI Codex app/CLI** - Latest stable verified: `rust-v0.135.0`, published 2026-05-28T17:31:35Z from GitHub releases. Recent episode version tags detected: `rust-v0.134.0`. Selected missing version: `rust-v0.135.0`. `rust-v0.136.0-alpha.1` was seen as a prerelease and excluded from stable coverage.
- **Claude Code CLI** - Latest npm `latest` verified: `2.1.157`, published 2026-05-29T17:30:02Z; npm `stable` dist-tag remains `2.1.148`. Recent episode version tags detected: `2.1.152` and `2.1.153`. Selected missing versions from the npm `latest` lane: `2.1.154`, `2.1.156`, and `2.1.157`.
- **Candidate verification** - The selected slate leads with the Hermes, Codex, and Claude Code release block, keeps OpenClaw stable coverage in the watch lane, then moves into model/workspace-agent news and GitHub-hosted projects that improve browser debugging, code flow tracing, cost telemetry, and agent media generation.

## Runtime Target

42-50 min. Release readout up front, then source-verified stories around frontier coding models, workspace-agent controls, browser runtime tooling, local code-flow context, cost/quota telemetry, and programmable agent media.

## Episode Title

Hermes Agent 0.15.x, Codex 0.135, Claude Code 2.1.157, Opus 4.8, Browser MCP, and Usage Telemetry

## Tagline

Hermes ships a large platform release and hotfix chain, Codex and Claude Code add sharper operational surfaces, Opus 4.8 changes the coding-agent model lane, workspace agents get more policy controls, and the project radar turns browser state, code flow, usage cost, and media rendering into agent-readable tools.

## Feed Description

AgentStack Daily EP059 leads with a current agent-stack release readout. Hermes Agent moves from `v0.14.0` to the `v0.15.x` line with a major kanban/orchestration expansion, faster launch and session search, promptware defense, Bitwarden Secrets Manager support, skill bundles, an Ink multi-session TUI, image provider additions, a Nous-approved MCP catalog, ntfy messaging, and follow-up fixes for dashboard loopback auth, Docker insecure-mode opt-in, MCP PATH resolution, `.md` media delivery, plugin packaging, and wheel/sdist manifests. Codex `rust-v0.135.0` adds richer `doctor` diagnostics, remote `/status` details, Vim text objects, named permission profiles, bundled zsh helper discovery, Python SDK sandbox presets, non-interactive install mode, and TUI/session reliability fixes. Claude Code `2.1.154` through `2.1.157` adds Opus 4.8, dynamic workflows, effort controls, automatic skill loading from `.claude/skills`, plugin scaffolding, `claude agents` worktree/session improvements, richer telemetry options, and many background-session, sandbox, MCP, image, terminal, and worktree fixes. The episode then covers Anthropic Opus 4.8, OpenAI workspace-agent controls, Chrome DevTools MCP, local code-flow tools, usage/quota telemetry, and programmable video rendering for agent-built media.

## Story Slate

### 1. **OpenClaw stays stable while Hermes Agent 0.15.x becomes the main release event**
OpenClaw's stable lane remains on `v2026.5.27`, while the visible `v2026.5.28` work is still beta-watch material around agent recovery, channel identity, malformed callback rejection, and provider/media expansion. Hermes Agent is the current stable release story. Its `v0.15.x` run is a large platform update: `run_agent.py` is split into smaller modules, kanban becomes a real multi-agent surface with auto-decomposition, swarm topology, scheduled tasks, worktree-per-task, and per-task model overrides, `session_search` becomes dramatically faster and free, promptware defense lands, Bitwarden Secrets Manager reduces provider-key sprawl, skill bundles group workflow behavior, the Ink TUI gets multi-session orchestration, image providers expand, the MCP catalog gets an interactive picker, ntfy joins messaging, and xAI/Web Search provider integration deepens. `v0.15.1` fixes the loopback dashboard reload loop and Docker insecure-mode inference, and `v0.15.2` ships bundled plugin manifests in packaging artifacts.
Technical depth angle: explain durable kanban orchestration, worker lifecycle, worktree-per-task isolation, scheduled task dispatch, promptware defense boundaries, secret bootstrap tokens, MCP catalog selection, dashboard loopback auth, Docker bind-host safety, and Python packaging manifests.
Actionability angle: upgrade Hermes only after checking one local kanban board, one scheduled task, one MCP catalog install, one Bitwarden-backed provider path, and one loopback dashboard session.
Listener hook: this is Hermes moving from "agent CLI with tools" toward "local agent operations platform," which changes how teams split, recover, and audit agent work.
Primary links: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.28, https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.29, https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.29.2

### 2. **Codex 0.135 makes diagnostics, permissions, and SDK sandboxes more inspectable**
Codex `rust-v0.135.0` is smaller than the Hermes release, but it lands on the surfaces that matter when a local coding agent breaks: richer `codex doctor` output for environment, Git, terminal, app-server, and thread inventory; remote `/status` details that show connection and server version; named permission profiles in `/permissions`; a bundled patched zsh helper for packaged builds; Python SDK `Sandbox` presets for thread and turn APIs; and non-interactive installer support through `CODEX_NON_INTERACTIVE=1`. The fixes also make markdown tables, TUI output, slash-command completion, tmux/iTerm control-mode handling, remote attachments, extension errors, app-server model selection, and MCP disconnects less brittle.
Technical depth angle: explain diagnostics as support data, remote transport status, profile-based permission selection, shell helper discovery, SDK sandbox presets, non-interactive installs, and why TUI rendering and app-server model selection affect long local runs.
Actionability angle: run `codex doctor` before blaming a model, define named permission profiles for risky repos, use SDK sandbox presets instead of ad hoc config, and test one remote transport session after upgrading.
Listener hook: coding agents are only useful when failures are inspectable; this release gives more of the runtime a name, a status, and a recovery path.
Primary links: https://github.com/openai/codex/releases/tag/rust-v0.135.0

### 3. **Claude Code 2.1.157 and Opus 4.8 push workflows, plugins, effort, and worktrees forward**
Claude Code's `latest` lane moved past the `2.1.153` reliability release into an Opus 4.8 and workflow wave. `2.1.154` adds Opus 4.8 support, dynamic workflows for large background efforts, fast mode pricing changes, effort label changes, background shell dispatch through `claude agents`, streaming tool execution by default, stdio MCP session environment variables, pending-approval rendering for `.mcp.json`, and many sandbox/worktree/background fixes. `2.1.156` fixes Opus 4.8 thinking-block API errors. `2.1.157` automatically loads plugins from `.claude/skills`, adds `claude plugin init`, improves `/plugin` autocomplete, honors the `agent` field in `settings.json` for dispatched sessions, lets `EnterWorktree` move between Claude-managed worktrees, expands optional tool-parameter telemetry, leaves completed worktrees unlockable, and fixes image, sandbox prompt, background-agent, resume, worktree, terminal, and workflow-trigger issues.
Technical depth angle: explain dynamic workflow dispatch, effort controls, automatic skill/plugin loading, worktree switching, MCP session environment variables, telemetry detail flags, sandbox network prompts, background-session retirement, and image placeholder handling.
Actionability angle: pin the desired npm lane, test Opus 4.8 on one contained repo task, create one local plugin with `claude plugin init`, verify `.claude/skills` auto-loading, and inspect whether background worktrees cleanly unlock after completion.
Listener hook: Claude Code is not just getting a stronger model; it is turning workflows, skills, plugins, and worktrees into first-class operating pieces.
Primary links: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md, https://www.npmjs.com/package/@anthropic-ai/claude-code, https://www.anthropic.com/news/claude-opus-4-8

### 4. **OpenAI workspace agents add policy controls for Slack threads, speech output, and shared directories**
OpenAI's May 28 workspace-agent release notes move the ChatGPT agent surface toward managed team operation. Workspace agents can use GPT-5.5 with reasoning-effort controls, admins can choose which roles may publish agents into the shared directory, guided setup asks better configuration questions, agents can generate audio files, Slack agents can respond to relevant follow-up messages in a thread after the initial mention, and app action safeguards let builders constrain what an agent can do in each enabled workspace app. In the same broader Codex direction, mobile remote access and scoped access tokens keep showing the pattern: execution lives near the trusted environment, while control and identity become managed surfaces.
Technical depth angle: explain role-based publishing, guided agent setup, per-app action safeguards, Slack thread-follow behavior, speech output as generated media, reasoning effort as an admin/user control, and scoped workspace identity for automations.
Actionability angle: separate personal agents from shared-directory agents, test Slack thread replies in one low-risk channel, set app-level action safeguards before enabling mutating tools, and keep audio generation on explicit workflows until storage and review behavior are clear.
Listener hook: once agents can speak in shared Slack threads and take app actions, the admin surface becomes part of the product, not paperwork after the fact.
Primary links: https://help.openai.com/en/articles/10128477-chatgpt-enterprise-edu-release-notes, https://openai.com/index/work-with-codex-from-anywhere/

### 5. **Chrome DevTools MCP makes browser runtime state a first-class coding-agent tool**
Chrome DevTools MCP is a browser-debugging bridge for coding agents, and its current release line matters because frontend work often fails in the gap between code edits and what the browser actually does. Version `1.1.1` is a small CLI argument fix, but the project itself is the useful stack surface: it lets agents query and operate Chrome DevTools through MCP instead of relying only on screenshots, static files, or manual console copying. For OpenClaw, Codex, Claude Code, and Hermes, the value is a tighter loop from DOM, network, console, performance, and page state back into the agent's reasoning.
Technical depth angle: explain MCP as a browser-inspection boundary, page identifiers, DevTools protocol-backed state, console/network/runtime observability, DOM inspection, performance data, and how browser tools differ from visual-only computer use.
Actionability angle: connect it to one local frontend, reproduce a bug through the browser, inspect console and network state, then ask the coding agent to patch only after it can cite the browser evidence.
Listener hook: a frontend agent that can inspect the running page is less likely to hallucinate from the source tree alone.
Primary links: https://github.com/ChromeDevTools/chrome-devtools-mcp, https://github.com/ChromeDevTools/chrome-devtools-mcp/releases/tag/chrome-devtools-mcp-v1.1.1

### 6. **Usage telemetry projects turn model cost and quota into data the stack can act on**
The ccusage project is a useful reminder that model choice is not only quality and latency; it is also local usage evidence, pricing, missing telemetry, and quota behavior. The current `v20.0.6` release adds Claude Opus 4.8 rates, fallback to `models.dev` pricing, warnings when model pricing is missing, Copilot missing-OTel explanations, opencode Kimi cost fixes, and release/install fixes. That fits the week because the stack is getting more background workflows, more long-running agent sessions, more model routing, and more media uploads. Without usage accounting, teams discover limits only when a job fails.
Technical depth angle: explain local usage log parsing, OpenTelemetry gaps, provider pricing tables, fallback pricing sources, missing-price warnings, model-family rate changes, and how cost telemetry differs from API quota telemetry while still supporting the same scheduling decisions.
Actionability angle: run usage accounting across Claude Code, Codex, Copilot, or OpenCode sessions, compare the cost profile of background workflows against foreground edits, and feed usage limits into schedulers before launching bulk agent or media work.
Listener hook: the cheapest failure is the one your scheduler avoids because it knew the budget before it clicked upload or spawned twenty agents.
Primary links: https://github.com/ryoppippi/ccusage, https://github.com/ryoppippi/ccusage/releases/tag/v20.0.6

### 7. **Agent-native media tools make generated video a programmable surface**
Hyperframes is a practical project for a different part of the stack: agents that create media need renderable, inspectable, code-shaped artifacts. The project turns HTML into video and is explicitly built for agents. Its current releases are small playback and design-panel fixes, but the stack angle is bigger: HTML, CSS, animation state, playback rate, and rendered output become testable assets instead of opaque video-editor state. For podcast, short-form, product demo, and documentation workflows, that means a coding agent can generate a visual sequence, render it, inspect it, patch it, and keep the source in version control.
Technical depth angle: explain HTML-as-video source, runtime playback constraints, GSAP state, deterministic rendering, asset versioning, preview/player limits, and how a generated media pipeline can be tested before publication.
Actionability angle: use it first for a short explainer or product-demo clip, keep the HTML source beside the script, render in CI or a local job, and add visual checks before upload.
Listener hook: agents are better at media when the media has source code, not just a final MP4.
Primary links: https://github.com/heygen-com/hyperframes, https://github.com/heygen-com/hyperframes/releases/tag/v0.6.58

## GitHub Project Radar

- **Chrome DevTools MCP** - https://github.com/ChromeDevTools/chrome-devtools-mcp - TypeScript MCP bridge exposing Chrome DevTools to coding agents. GitHub API check on 2026-05-29 showed 42,258 stars, 2,700 forks, created 2025-09-11, pushed 2026-05-28. Latest release `chrome-devtools-mcp-v1.1.1` shipped 2026-05-27 with a CLI page-id argument fix. Stack improvement angle: give Codex, Claude Code, OpenClaw, and Hermes browser evidence from the running app before frontend edits. Try now: reproduce one UI bug, inspect console/network/DOM state through MCP, then patch from the evidence.
- **CodeGraph** - https://github.com/colbymchenry/codegraph - TypeScript local code knowledge graph for Claude Code, Codex, Gemini, Cursor, OpenCode, Antigravity, Kiro, and Hermes Agent. GitHub API check on 2026-05-29 showed 33,096 stars, 2,001 forks, created 2026-01-18, pushed 2026-05-29. Latest release `v0.9.7` shipped 2026-05-28 with better Go gRPC implementation resolution, generated-file deprioritization, dynamic-dispatch trace output, multi-module endpoint selection, and route-table context. Stack improvement angle: let agents answer flow and routing questions with pre-indexed local structure instead of spending tool calls on generated files and same-name symbols. Try now: ask `codegraph_context` how one web request reaches its handler and compare the answer with raw text search.
- **ccusage** - https://github.com/ryoppippi/ccusage - Rust CLI for analyzing local coding-agent token usage and cost across supported tools. GitHub API check on 2026-05-29 showed 15,154 stars, 597 forks, created 2025-05-29, pushed 2026-05-29. Latest release `v20.0.6` shipped 2026-05-29 with Claude Opus 4.8 pricing, fallback pricing, missing-price warnings, Copilot OTel explanations, and opencode cost fixes. Stack improvement angle: make model spend visible before background workflows, long compactions, or multi-agent runs surprise the budget. Try now: run it over recent local agent sessions, compare model families, and set scheduler limits from observed usage.
- **Hyperframes** - https://github.com/heygen-com/hyperframes - TypeScript project for writing HTML and rendering video, built for agents. GitHub API check on 2026-05-29 showed 22,236 stars, 2,076 forks, created 2026-03-10, pushed 2026-05-29. Latest release `v0.6.58` shipped 2026-05-29 with playback-rate clamping and GSAP design-panel state fixes. Stack improvement angle: give media-generation agents source-controlled video scenes that can be rendered, inspected, patched, and tested like code. Try now: build a 20-second product explainer from HTML, render it locally, and verify playback/visual state before upload.
- **claude-mem** - https://github.com/thedotmack/claude-mem - TypeScript persistent context layer that captures, compresses, and reinjects agent session context across Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, and OpenCode. GitHub API check on 2026-05-29 showed 79,591 stars, 6,846 forks, created 2025-08-31, pushed 2026-05-29. Latest release `v13.4.0` shipped 2026-05-29 with OpenAI-compatible base URL configuration, spawn-contract fixes, worker lifecycle hardening, output-fidelity fixes, SQLite repair improvements, and green CI. Stack improvement angle: make memory provider selection and persistence repair explicit instead of tying cross-session context to one CLI's transcript format. Try now: connect it to a disposable repo, run two short sessions with different clients, and verify what context is recalled and what is withheld.

## Extra Research Candidates

- **OpenClaw v2026.5.28 beta watch** - Primary source: https://github.com/openclaw/openclaw/releases/tag/v2026.5.28-beta.3. Technical depth angle: explain app-server recovery, channel identity, Discord recovered tool warnings, malformed callback rejection, provider/media additions, and why beta-only changes should be watched without replacing stable release coverage.
- **Claude Opus 4.8 system-card deep dive** - Primary source: https://www.anthropic.com/news/claude-opus-4-8. Technical depth angle: compare benchmark methodology, effort settings, fast mode, pricing, safety/evaluation claims, and how model behavior changes should alter coding-agent task selection.
- **OpenAI Codex remote access and tokens** - Primary source: https://openai.com/index/work-with-codex-from-anywhere/. Technical depth angle: explain secure relay, remote host state sync, scoped access tokens, hooks, and why local credentials plus mobile supervision changes the coding-agent deployment boundary.

## Show Notes

```md
OpenClaw `v2026.5.27` remains the stable OpenClaw baseline while `v2026.5.28` is a beta watch item, and Hermes Agent `v2026.5.29.2` is the new stable agent-stack release event. Codex 0.135, Claude Code 2.1.157, and Opus 4.8 complete the release context for EP059. Hermes gets the largest platform move: kanban orchestration, worktree-per-task execution, scheduled tasks, faster session search, promptware defense, skill bundles, MCP catalog selection, ntfy messaging, and follow-up fixes for loopback dashboards, Docker insecure mode, MCP PATH resolution, `.md` media, and plugin packaging. Codex adds better diagnostics, remote status, named permission profiles, SDK sandbox presets, non-interactive install support, and TUI/runtime reliability. Claude Code adds Opus 4.8, dynamic workflows, automatic `.claude/skills` plugin loading, plugin scaffolding, worktree switching, telemetry detail options, and background-session cleanup. Then the episode moves into workspace-agent policy, browser runtime MCP, code-flow graphs, usage telemetry, and agent-built media.

[00:00] Opening: agent stacks become easier to inspect
The useful theme today is inspectability. Hermes is making orchestration visible. Codex is naming more of the runtime through `doctor`, `/status`, profiles, and SDK sandbox presets. Claude Code is putting workflows, plugins, effort, worktrees, and background sessions on clearer rails. OpenAI workspace agents are getting policy controls around publishing, Slack, speech, and app actions. The project lane keeps the same shape: browser state, code-flow state, usage cost, and media rendering all become things an agent can query instead of guessing.

[03:00] OpenClaw and Hermes Agent release readout
OpenClaw starts this release block as a stability check. The latest stable tag remains `v2026.5.27`, which means the content-boundary, Codex app-server recovery, provider catalog, embedding-provider, VLLM thinking-parameter, channel-delivery, and metadata-cache work from the prior stable release is still the baseline. The newer `v2026.5.28` line is visible as beta material, and it is worth watching because the beta notes point at the exact surfaces local agent stacks care about: app-server recovery, subagent cwd/workspace separation, hook context isolation, timeout lock release, stale restart avoidance, channel identity, Discord recovered tool warnings, Slack and Telegram delivery paths, malformed callback rejection, provider additions, and browser timeout validation. Because it is beta, it belongs in the watch lane rather than the stable upgrade lane.

Hermes Agent has the biggest stable agent-stack release of the day. The 0.15 line moves a lot of machinery into core product surfaces. Kanban is no longer a thin board around prompts; it grows orchestration features such as auto-decomposition, swarm topology, scheduled tasks, worktree-per-task execution, and per-task model overrides. That matters because multi-agent work needs durable assignment, isolation, and recovery. A board is only useful if work can be split, claimed, retried, and inspected without turning into a loose pile of chat transcripts.

The codebase shape changed too. The large `run_agent.py` path was split into smaller modules, cold start improved again, and `session_search` became dramatically faster and free. The practical value is simple: when a local agent has many sessions, many tools, and a lot of remembered work, search and startup cost become part of the workflow. Slow search makes memory feel fake. Fast search makes prior work reachable.

Hermes also adds promptware defense, Bitwarden Secrets Manager support, skill bundles, an Ink multi-session TUI, two image-generation providers, a Nous-approved MCP catalog with an interactive picker, ntfy messaging, and deeper xAI integration. The follow-up releases are important too. The dashboard loopback 401 reload loop is fixed. Docker insecure mode becomes an explicit opt-in instead of inferred from bind host. MCP bare-command PATH resolution improves. Markdown media delivery is restored. Packaging now includes bundled plugin manifests in wheel and source distributions.

[12:00] Codex 0.135 makes failures more diagnosable
Codex 0.135 is not the loudest release, but it improves the day-to-day support surface. `codex doctor` now reports richer environment, Git, terminal, app-server, and thread inventory diagnostics. That kind of command matters because coding-agent failures are often environmental: the shell helper is wrong, the app-server is stale, the remote transport is mismatched, the repo state is surprising, or the terminal is corrupting output.

Remote `/status` now shows connection details and server version when the TUI is connected over a remote transport. `/permissions` understands named permission profiles and displays custom profiles. Packaged builds can discover the bundled patched zsh helper across supported macOS and Linux targets. The Python SDK adds friendly `Sandbox` presets for thread and turn APIs. Install scripts support non-interactive installation through `CODEX_NON_INTERACTIVE=1`.

The fixes are also practical: markdown tables and multiline lists render more readably, TUI output is more stable on macOS and Zellij, slash-command completion preserves draft text, older tmux and iTerm control-mode sessions keep normal Ctrl-C behavior, extension tools surface errors better, remote attachments attach correctly, app-server runtime respects model choices, and disconnected MCP tools stop showing as running. The release is about making local and remote Codex runs easier to explain when they misbehave.

[19:00] Claude Code 2.1.157 and Opus 4.8
Claude Code's latest lane moved through an Opus 4.8 release wave. Version 2.1.154 adds Opus 4.8 support, dynamic workflows, fast mode changes, effort label updates, background shell dispatch from `claude agents`, default streaming tool execution, stdio MCP session environment variables, and pending-approval rendering for `.mcp.json` servers. The dynamic workflow piece is the most important part: it lets Claude Code organize larger efforts across background agents and workflow status instead of making one foreground turn carry the whole job.

Version 2.1.156 fixes a thinking-block issue on Opus 4.8. Version 2.1.157 then turns plugin and worktree behavior into a more direct path. Plugins in `.claude/skills` directories are loaded automatically. `claude plugin init` scaffolds a new plugin. `/plugin` autocomplete improves. `claude agents` honors the configured agent field in `settings.json`. `EnterWorktree` can switch between Claude-managed worktrees. Tool-decision telemetry can include tool parameters when the user opts into detail. Completed worktrees are left unlockable so cleanup can prune them.

Anthropic's Opus 4.8 release is the model side of the same movement. It is positioned for harder coding, agentic tasks, and professional work, with unchanged regular pricing from Opus 4.7 and cheaper fast mode than earlier fast-mode pricing. The right evaluation is not only whether a benchmark moved. It is whether the model plus workflow layer can run a larger task, ask better questions, avoid silent wrongness, and clean up its worktree afterward.

[27:00] Workspace agents need policy because they now live in shared channels
OpenAI's workspace-agent release notes show another direction: agents are becoming shared workspace actors. Workspace agents can use GPT-5.5 with reasoning effort controls. Admins can control which roles publish agents into a shared directory. Guided setup helps users configure agents. Agents can produce audio files. Slack agents can respond to relevant follow-up messages in a thread after the initial mention. Builders can define safeguards for actions in each enabled app.

Those details matter because shared agents have different risks than personal chat. A Slack-thread agent can be useful only if it knows when a follow-up is relevant and when to stay quiet. A speech-output agent needs storage, review, and distribution expectations. A shared directory needs publishing permissions, not just a pile of clever prompts. App safeguards need to be set before the agent gets write-capable tools.

Codex remote access and access tokens fit the same pattern. The machine that owns the files and credentials remains the execution boundary, while phones, scripts, and managed workspace identity become control surfaces. That is the stable architecture for agent work: run near the data, supervise from the channel that fits the moment, and keep identity scoped.

[34:00] Browser runtime MCP beats guessing from source
Chrome DevTools MCP is a good project to watch because frontend agents need browser evidence. A model can read source files and still miss the runtime problem: a network request failed, a console error happened after hydration, a CSS rule was overridden, a page id changed, or a performance issue only appears once the app runs. A DevTools-backed MCP bridge lets the agent inspect the actual browser state.

The current release is a small CLI page-id fix, but the project shape is bigger than that patch. MCP can expose DOM, console, network, runtime, and performance surfaces in a way coding agents can ask about. That differs from visual computer use. Screenshots show what a user sees; DevTools state explains why the browser behaved that way. For local apps, the best loop is evidence first: reproduce, inspect, patch, verify.

[39:00] Code flow, usage cost, and generated media become agent-readable
The project radar has three more useful surfaces. CodeGraph gives agents a local pre-indexed code knowledge graph. Its latest release improves Go gRPC implementation resolution, deprioritizes generated files, handles dynamic-dispatch trace breaks by including endpoint source plus callers and callees, improves multi-module endpoint selection, and inlines routing context for small projects. That is what a coding agent needs when a question is about flow, not just text matches.

ccusage attacks a different blind spot: usage and cost. Its current release adds Opus 4.8 rates, fallback pricing, missing-price warnings, Copilot telemetry explanations, opencode cost fixes, and release/install improvements. As background workflows and multi-agent runs become normal, usage telemetry stops being accounting trivia. It becomes scheduler input. A system that knows model cost, missing pricing, and telemetry gaps can choose a smaller model, wait for a budget window, or stop before a task becomes wasteful.

Hyperframes is the media counterpart. It treats video as HTML source plus renderable runtime, which makes generated media more inspectable. Agents can edit source, render, inspect, patch playback behavior, and keep the media scene in version control. That is more reliable than treating a final MP4 as the first real artifact.

[46:00] Close
The practical queue from EP059 is clear. Hermes is the major platform release to study. Codex is better at showing what environment and permissions it is actually using. Claude Code is moving workflows, plugins, effort, and worktrees into the foreground. Opus 4.8 changes the high-end coding model lane. Workspace agents need policy because they now operate in shared channels. Browser MCP, code graphs, usage telemetry, and source-controlled media are the tool layer that makes agent work less mysterious. The best stack is not the one with the most agents running. It is the one where each agent can see the runtime, know the code path, understand the budget, and leave evidence behind.
```

## Chapters

- 00:00 Agent stacks become easier to inspect
- 03:00 Hermes Agent v0.15.x release readout
- 12:00 Codex 0.135 makes failures more diagnosable
- 19:00 Claude Code 2.1.157 and Opus 4.8
- 27:00 Workspace agents need policy in shared channels
- 34:00 Browser runtime MCP beats guessing from source
- 39:00 Code flow, usage cost, and generated media become agent-readable
- 46:00 Close

## Verified Links

- Hermes Agent v2026.5.28: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.28
- Hermes Agent v2026.5.29: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.29
- Hermes Agent v2026.5.29.2: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.29.2
- Codex rust-v0.135.0: https://github.com/openai/codex/releases/tag/rust-v0.135.0
- Claude Code changelog: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md
- Claude Code npm package: https://www.npmjs.com/package/@anthropic-ai/claude-code
- Claude Opus 4.8: https://www.anthropic.com/news/claude-opus-4-8
- OpenAI workspace-agent release notes: https://help.openai.com/en/articles/10128477-chatgpt-enterprise-edu-release-notes
- Codex remote access and tokens: https://openai.com/index/work-with-codex-from-anywhere/
- OpenClaw v2026.5.27: https://github.com/openclaw/openclaw/releases/tag/v2026.5.27
- OpenClaw v2026.5.28 beta watch: https://github.com/openclaw/openclaw/releases/tag/v2026.5.28-beta.3
- Chrome DevTools MCP: https://github.com/ChromeDevTools/chrome-devtools-mcp
- Chrome DevTools MCP v1.1.1: https://github.com/ChromeDevTools/chrome-devtools-mcp/releases/tag/chrome-devtools-mcp-v1.1.1
- CodeGraph: https://github.com/colbymchenry/codegraph
- CodeGraph v0.9.7: https://github.com/colbymchenry/codegraph/releases/tag/v0.9.7
- ccusage: https://github.com/ryoppippi/ccusage
- ccusage v20.0.6: https://github.com/ryoppippi/ccusage/releases/tag/v20.0.6
- Hyperframes: https://github.com/heygen-com/hyperframes
- Hyperframes v0.6.58: https://github.com/heygen-com/hyperframes/releases/tag/v0.6.58
- claude-mem: https://github.com/thedotmack/claude-mem
- claude-mem v13.4.0: https://github.com/thedotmack/claude-mem/releases/tag/v13.4.0
