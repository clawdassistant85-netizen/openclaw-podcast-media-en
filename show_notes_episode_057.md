# AgentStack Daily EP057 - OpenClaw 2026.5.22, Claude Code 2.1.149, Gemini Managed Agents, Codex Remote Work, Anthropic Tooling, and Agent-Stack Projects

## Release Coverage Check

- **OpenClaw** - Latest stable verified: v2026.5.22. Recent episode version tags detected: v2026.5.20. Selected missing version: v2026.5.22.
- **Claude Code CLI** - Latest npm `latest` verified: 2.1.150. Recent episode version tags detected: 2.1.148. Selected missing versions: 2.1.149 and 2.1.150. Version 2.1.149 has user-facing CLI changes and security fixes; 2.1.150 is internal infrastructure only.
- **Hermes Agent** - Latest stable verified: v2026.5.16. Recent episode version tags detected: v2026.5.16. No selected missing version.
- **OpenAI Codex app-CLI** - Latest stable verified: rust-v0.133.0. Recent episode version tags detected: rust-v0.133.0. No selected missing version.
- **Candidate verification** - The selected slate starts with the OpenClaw and Claude Code CLI release readout, then moves into source-verified AI news and GitHub-hosted projects that are adjacent to OpenClaw, Codex, Claude Code, Hermes Agent, MCP, local/self-hosted agents, model routing, and codebase understanding.

## Runtime Target

40-48 min. Release readout up front, then AI news and project segments with concrete feature deltas, implications, and short recommendations.

## Episode Title

OpenClaw 2026.5.22, Claude Code 2.1.149, Gemini Managed Agents, Codex Remote Work, Anthropic Tooling, and Agent-Stack Projects

## Tagline

OpenClaw and Claude Code get a real release readout, Google ships managed Gemini agents, OpenAI pushes Codex into mobile and hybrid environments, Anthropic tightens SDK/MCP and security work, and the project lane focuses on repo tools that can improve the stack.

## Feed Description

AgentStack Daily EP057 leads with OpenClaw v2026.5.22 and Claude Code 2.1.149/2.1.150, then broadens into source-verified AI news and practical GitHub-hosted projects. OpenClaw improves gateway startup behavior, plugin metadata reuse, meeting-notes capture contracts, chat-session pagination, Discord callback lifetimes, xAI/Grok search reuse, plugin SDK helpers, provider/media fallbacks, and reliability fixes. Claude Code 2.1.149 adds per-category usage accounting, keyboard-scrollable diff detail, task-list rendering, managed cloud MCP connector loading, and permission/sandbox/PowerShell/macOS safety fixes, while 2.1.150 is internal-only. Then the episode covers Gemini 3.5 Flash and Gemini API Managed Agents, Codex mobile/remote access and hybrid/on-prem enterprise movement, Anthropic's Stainless acquisition and Project Glasswing update, and a GitHub project radar focused on semantic code intelligence, MCP builders, model routing, local agents, security scanners, and multi-harness setup tools.

## Story Slate

### 1. **OpenClaw 2026.5.22 and Claude Code 2.1.149 fix real stack friction**
OpenClaw's v2026.5.22 release adds process-stable channel catalog reads, plugin metadata snapshot reuse, lazy startup-idle plugin work, embedded ACPX runtime work, external meeting-notes plugin/source-provider contracts, Discord voice-first source support, chat-session search and Load More pagination, bounded Discord component callback lifetimes, subagent bootstrap trimming, native subagent handoff fixes, xAI/Grok web_search OAuth reuse, plugin SDK poll/session/embedding-provider helpers, and provider/media fallback cleanup. Claude Code moves from 2.1.148 to 2.1.149/2.1.150 on npm `latest`: 2.1.149 adds `/usage` category breakdowns, keyboard scrolling in `/diff`, GFM task-list rendering, managed cloud MCP connector loading, and several permission/sandbox/PowerShell/macOS vnode safety fixes; 2.1.150 is internal-only. Codex and Hermes stay in the watch lane for release tags, but the episode should still explain where they fit in the stack.
Technical depth angle: explain OpenClaw gateway startup/cache behavior, plugin metadata reuse, meeting-notes source-provider contracts, Discord component TTLs, xAI/Grok search auth reuse, Codex image/provider fallback behavior, Claude Code usage accounting, cloud MCP connector policy, and shell/sandbox fixes that reduce accidental permission bypasses.
Actionability angle: update OpenClaw and Claude Code for the gateway, meeting-notes, provider, usage, diff, MCP-policy, and shell-safety improvements; treat 2.1.149 as the user-facing Claude Code change and 2.1.150 as internal-only.
Listener hook: the useful part is not the version numbers; it is that the local gateway layer and coding CLI layer both get less brittle in places where real agent work stalls.
Primary links: https://github.com/openclaw/openclaw/releases/tag/v2026.5.22, https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md, https://www.npmjs.com/package/@anthropic-ai/claude-code

### 2. **Gemini 3.5 Flash and Gemini API Managed Agents make sandboxed agents a platform feature**
Google's May agent news is not just another model headline. Gemini 3.5 Flash is positioned for agentic and coding work, with Google claiming strong Terminal-Bench, GDPval-AA, MCP Atlas, multimodal, speed, and long-horizon task performance, while Gemini API Managed Agents let developers spin up an Antigravity-powered agent in an isolated ephemeral Linux environment that can reason, use tools, execute code, browse, persist session state across follow-up calls, and be customized with AGENTS.md and SKILL.md files.
Technical depth angle: explain managed remote Linux environments, session state continuation, tool execution, browsing, Antigravity harness behavior, custom agent definition files, and why benchmarks like Terminal-Bench and MCP Atlas matter for coding agents more than chat-only scores.
Actionability angle: use Gemini Managed Agents first for public, disposable, or clean-room tasks; keep private code, credentials, subscribed tools, and machine-specific workflows on local or tightly controlled hosts until the managed boundary is clear.
Listener hook: this is a direct signal that agent infrastructure is becoming a product surface, not a hidden implementation detail.
Primary links: https://blog.google/intl/en-africa/products/explore-get-answers/gemini-3-5/, https://blog.google/innovation-and-ai/technology/developers-tools/managed-agents-gemini-api/

### 3. **OpenAI pushes Codex toward remote supervision, automation tokens, and hybrid enterprise environments**
OpenAI's Codex updates matter because they match the way long-running coding agents are actually used: start work in the environment that owns the files and dependencies, supervise it later from another device, review diffs, approve commands, and keep local or enterprise credentials near the execution boundary. Codex in the ChatGPT mobile app exposes live session state from connected Macs or remote environments, while Remote SSH, hooks, programmatic access tokens, and the Dell partnership point toward Codex running inside managed remote, hybrid, and on-prem enterprise setups instead of only a single laptop.
Technical depth angle: explain secure relay state sync, remote host connection, approvals from mobile, terminal/test/diff streaming, scoped access tokens, hooks for prompt scanning and validators, and why hybrid/on-prem Codex changes the security and deployment model for coding agents.
Actionability angle: use Codex mobile supervision for narrow decision points, prefer scoped access tokens over broad logged-in sessions for automation, and place execution near the repo, credentials, and policy boundary that the task actually needs.
Listener hook: Codex is moving from "agent on my machine" toward "agent work that can be supervised anywhere while still running near the data."
Primary links: https://openai.com/index/work-with-codex-from-anywhere/, https://openai.com/index/dell-codex-enterprise-partnership/

### 4. **Anthropic's Stainless acquisition and Project Glasswing update make agent connectivity and AI security feel like the same story**
Anthropic acquired Stainless, the SDK and MCP-server tooling company that has generated official Anthropic SDKs and helps turn API specs into SDKs, CLIs, and MCP servers across languages. A few days later, Anthropic's Project Glasswing update said Claude Mythos Preview had been used across more than 1,000 open-source projects and found large numbers of high- or critical-severity vulnerabilities, shifting the bottleneck from finding issues to verifying, disclosing, and patching them.
Technical depth angle: explain why SDK generation, CLI generation, MCP server generation, API specs, and agent tool surfaces are core infrastructure for agents that act, then connect that to frontier-model vulnerability discovery, triage bottlenecks, disclosure flow, and patch velocity.
Actionability angle: treat clean API specs as future agent-tool surfaces, and use agent-assisted security scanning only where verification, disclosure, and repair ownership are explicit.
Listener hook: agents need better handles on systems, but the same handle that lets an agent act can also let it find flaws faster than teams can process.
Primary links: https://www.anthropic.com/news/anthropic-acquires-stainless, https://www.anthropic.com/research/glasswing-initial-update

### 5. **Codebase-intelligence projects give Claude Code, Codex, and Hermes better eyes**
The project lane should include tools that make agents less dependent on blind grep and giant context dumps. Serena adds MCP-based semantic retrieval, editing, refactoring, and debugging tools; Claude Context adds semantic code search for Claude Code and other agents; Sourcebot self-hosts code search, navigation, and repo Q&A; Understand-Anything turns codebases into interactive knowledge graphs; Chunkhound and Code Review Graph push local-first code intelligence and persistent code maps.
Technical depth angle: explain symbol-level retrieval, references/definition navigation, vector-backed semantic search, persistent code graphs, local indexing, and how these tools reduce context waste before a coding agent edits a repo.
Actionability angle: add a code-intelligence layer when repo size justifies it: Serena for symbol-aware MCP tools, Claude Context for semantic search, Sourcebot for self-hosted cited search, Understand-Anything for architecture graphs, and Chunkhound or Code Review Graph for local-first maps.
Listener hook: the faster way to make an agent better may be giving it a better map, not just a bigger model.
Primary links: https://github.com/oraios/serena, https://github.com/zilliztech/claude-context, https://github.com/sourcebot-dev/sourcebot, https://github.com/Lum1104/Understand-Anything, https://github.com/chunkhound/chunkhound, https://github.com/tirth8205/code-review-graph

### 6. **Model-routing, MCP, local-agent, and security projects are the practical stack upgrades**
The second project segment should be about tools that change how the stack is operated. Claude Code Router routes Claude Code requests across providers and models; mcp-use helps build, inspect, and deploy MCP servers and apps; goose provides a local desktop/CLI/API agent with provider and MCP extension support; gstack packages Claude Code roles and workflows for review, QA, release, security, and planning; deepsec uses coding agents for vulnerability scanning; context-mode and multi-harness setup tools try to reduce output noise and keep Claude Code, Codex, OpenCode, Gemini CLI, and related agents configured consistently.
Technical depth angle: explain request routing, provider failover, MCP app/server development, local agent extension models, reusable role/skill packs, agent-powered security scanners, context-window output filtering, and cross-harness setup sync.
Actionability angle: choose these tools by job: Context7 for current docs, Claude Code Router for visible provider routing, mcp-use for scoped MCP tools, goose for local-agent comparison, gstack for repeatable roles, deepsec for verified security scans, and setup/context tools for drift and output control.
Listener hook: these are the kinds of GitHub projects that can change the day-to-day stack, because they sit between the model, the repo, the tools, and the human approval loop.
Primary links: https://github.com/musistudio/claude-code-router, https://github.com/mcp-use/mcp-use, https://github.com/aaif-goose/goose, https://github.com/garrytan/gstack, https://github.com/vercel-labs/deepsec, https://github.com/mksglu/context-mode, https://github.com/caliber-ai-org/ai-setup

## GitHub Project Radar

- **Serena** - https://github.com/oraios/serena - Python MCP toolkit for semantic retrieval, editing, refactoring, and debugging, positioned as IDE-like tooling for coding agents. GitHub API check on 2026-05-26 showed 24,637 stars, 1,650 forks, created 2025-03-23, and pushed 2026-05-26. Stack improvement angle: add symbol-aware navigation and refactoring to Claude Code, Codex, OpenCode, Gemini CLI, or Hermes-connected MCP clients so agents stop relying only on text search. Try now: run Serena against one large repo and ask a coding agent to trace a symbol, find references, and plan a refactor before it edits anything.
- **Context7** - https://github.com/upstash/context7 - TypeScript project that gives LLMs and coding agents up-to-date library documentation through CLI/skills or MCP. GitHub API check on 2026-05-26 showed 56,113 stars, 2,656 forks, created 2025-03-26, and pushed 2026-05-26. Stack improvement angle: reduce stale API hallucinations when Claude Code, Codex, or Hermes is generating code against fast-moving libraries. Try now: install Context7 in MCP or CLI+skills mode and force one library-specific task to use current docs before writing code.
- **Claude Code Router** - https://github.com/musistudio/claude-code-router - TypeScript router for Claude Code requests across providers such as OpenRouter, DeepSeek, Ollama, Gemini, and others, with request/response transformers and route-specific model choices. GitHub API check on 2026-05-26 showed 34,404 stars, 2,808 forks, created 2025-02-25, and updated 2026-05-26. Stack improvement angle: route background, long-context, cheap, local, or high-reasoning Claude Code work to different providers without changing the front-end workflow. Try now: configure one safe background route and compare quality, latency, and subscription/API behavior before using it for important edits.
- **Claude Context** - https://github.com/zilliztech/claude-context - Semantic code-search MCP for Claude Code and other AI coding agents. GitHub API check on 2026-05-26 showed 11,576 stars, 851 forks, created 2025-06-06, and pushed 2026-05-22. Stack improvement angle: make large repos searchable by meaning instead of pushing full directories into context. Try now: index a repo where grep is not enough and ask Claude Code to retrieve the most relevant code paths before planning.
- **Sourcebot** - https://github.com/sourcebot-dev/sourcebot - Self-hosted codebase understanding tool with repo search, code navigation, file exploration, and Ask Sourcebot Q&A with citations. GitHub API check on 2026-05-26 showed 3,431 stars, 283 forks, created 2024-08-23, and pushed 2026-05-26. Stack improvement angle: give humans and agents a shared self-hosted code search surface across repos and branches. Try now: deploy with Docker Compose and connect one multi-repo workspace before asking an agent a cross-repo question.
- **Understand-Anything** - https://github.com/Lum1104/Understand-Anything - TypeScript project that turns codebases into interactive knowledge graphs with search and Q&A, explicitly positioned for Claude Code, Codex, Cursor, Copilot, Gemini CLI, and related tools. GitHub API check on 2026-05-26 showed 33,484 stars, 2,722 forks, created 2026-03-15, and pushed 2026-05-26. Stack improvement angle: create visual and queryable architecture maps before agent edits on unfamiliar systems. Try now: run it on one repo and attach the generated map to a Claude Code or Codex planning session.
- **mcp-use** - https://github.com/mcp-use/mcp-use - Full-stack MCP framework for building MCP apps and servers in TypeScript/Python, with inspection and deployment paths. GitHub API check on 2026-05-26 showed 9,993 stars, 1,303 forks, created 2025-03-28, and pushed 2026-05-26. Stack improvement angle: make custom tools easier to build, debug, and package for Claude, Codex, ChatGPT, or OpenClaw-adjacent agents. Try now: scaffold one internal MCP server for a harmless read-only workflow and inspect calls before connecting it to an agent.
- **goose** - https://github.com/aaif-goose/goose - Rust local AI agent with desktop app, CLI, API, multi-provider support, subscription/ACP paths, and MCP extensions, now under the Agentic AI Foundation. GitHub API check on 2026-05-26 showed 45,883 stars, 4,725 forks, created 2024-08-23, and pushed 2026-05-26. Stack improvement angle: evaluate it as a local agent fallback or comparison point for OpenClaw/Hermes/Codex workflows. Try now: install the CLI, connect only a low-risk provider, and run one repo-reading task with no write permissions.
- **deepsec** - https://github.com/vercel-labs/deepsec - Agent-powered vulnerability scanner for large codebases with resumable scans, matchers, processing, revalidation, and export. GitHub API check on 2026-05-26 showed 2,931 stars, 199 forks, created 2026-04-30, and pushed 2026-05-23. Stack improvement angle: turn agentic code review toward security findings, but with explicit scope and human verification. Try now: run the setup on a small repo or sample app first, then inspect exported findings before trusting it on a large codebase.

## Extra Research Candidates

- **Mistral model lineup and Devstral/Mistral Medium agent positioning** - Primary source: https://docs.mistral.ai/models/overview. Technical depth angle: explain which Mistral models are positioned for coding, agents, embeddings, moderation, audio, and open-weight deployment, and where they could fit behind model routers.
- **OpenAI content provenance work** - Primary source: https://openai.com/news/. Technical depth angle: explain provenance metadata, generated-media transparency, and how content credentials affect agent-generated assets, thumbnails, demos, and podcast/video workflows.
- **OpenAI safe sandboxing for Codex on Windows** - Primary source: https://openai.com/news/. Technical depth angle: explain sandbox isolation, filesystem boundaries, process execution, and why Windows support changes the reachable developer base for local coding agents.

## Show Notes

```md
OpenClaw v2026.5.22 and Claude Code 2.1.149 are the front of EP057. OpenClaw tightens the gateway, plugins, meeting-notes capture, Discord callbacks, media/provider fallbacks, subagent behavior, xAI/Grok search reuse, chat-session navigation, and package integrity. Claude Code adds better usage accounting, diff navigation, task-list rendering, cloud MCP controls, and shell/sandbox fixes. Then the episode moves into AI news that matters to the stack: Gemini managed agents, Codex remote work and hybrid environments, Anthropic's SDK/MCP acquisition, AI security scanning, and GitHub-hosted projects that can improve agent workflows.

[00:00] Opening: release fixes, AI news, and real project radar
This episode starts with OpenClaw v2026.5.22 and Claude Code 2.1.149 because both releases changed machinery agent stacks depend on: gateway startup, plugin metadata, meeting notes, Discord callbacks, provider fallback behavior, cloud MCP connector policy, usage accounting, diffs, and shell safety. Then the AI-news lane covers Google, OpenAI, and Anthropic because each moved a concrete agent infrastructure surface: managed remote sandboxes, mobile-supervised Codex sessions, hybrid/on-prem Codex deployment, SDK/MCP generation, and frontier-model security scanning. The project lane stays focused on GitHub-hosted tools around semantic code context, current docs, model routing, MCP building, local agents, role packs, and security scanners.

[02:00] OpenClaw v2026.5.22 and Claude Code 2.1.149 release readout
OpenClaw's update is wide, but the useful theme is reliability and capability in the places agent stacks usually drag. The gateway leans on process-stable channel catalog reads and plugin metadata snapshot reuse, making startup and status work less wasteful. Startup-idle plugin work is lazier, irrelevant Linuxbrew PATH probes get skipped, and core gateway method handlers plus public-surface alias maps make the gateway path more consistent. Meeting notes get a real upgrade: external plugins and source providers now have a cleaner contract, capture can auto-start from config, manual imports are supported, read-only CLI access exists, and Discord voice is treated as a first live source rather than a side path.

The agent and plugin surfaces move too. OpenClaw trims default subagent bootstrap down to the files that matter most, adds native subagent completion handoff fixes, adds generic channel-message poll sending and session workflow helpers in the plugin SDK, and clarifies embedding-provider capability contracts. The chat control surface gets search and Load More pagination in the session picker, which matters once a gateway has a real backlog. Discord component callbacks now have a bounded TTL, reducing the risk that old review buttons or stale UI callbacks remain live beyond their useful lifetime. Provider handling gets cleaner: xAI OAuth can be reused for Grok web_search, model aliases and operation timeouts improve, Antigravity CLI becomes a lower-priority image/video fallback after configured provider APIs, and Codex API-key image generation uses the native OpenAI Images API. Add the dependency refresh, protobufjs 8.4.0, locked dependency work, catalog pruning, session write-lock cleanup, strict vLLM tool-free turns, Telegram topic fixes, local Chrome/Ollama proxy bypass fixes, and this is a real maintenance-and-capability release.

Claude Code's 2.1.149 update is smaller, but it hits daily use. `/usage` can show limit usage by category, including skills, subagents, plugins, and per-MCP-server cost. `/diff` detail view supports keyboard scrolling. Markdown output renders GitHub-flavored task-list checkboxes. Enterprise admins get an `allowAllClaudeAiMcps` managed setting for loading claude.ai cloud MCP connectors alongside managed MCP config. The fixes are the security story: PowerShell permission bypasses through built-in directory-changing functions, sandbox write allowlists that accidentally covered too much of a git worktree, PowerShell prefix/wildcard rule bugs, stale variable tracking around PWD/OLDPWD/DIRSTACK, a macOS `find` failure that could exhaust file tables on large directories, and several remote-session, managed-settings, telemetry-helper, transcript, and UI fixes. Version 2.1.150 is internal infrastructure only, so the user-facing delta is 2.1.149 even when the installed package is newer.

[10:00] Gemini 3.5 Flash and Gemini API Managed Agents
Google's Gemini 3.5 Flash announcement is worth treating as agent infrastructure news, not just model marketing. Google says 3.5 Flash is built for agentic workflows and coding, with stronger Terminal-Bench, GDPval-AA, MCP Atlas, multimodal, speed, and long-horizon-task claims. The important question is not whether one benchmark wins the week. It is whether a fast model can stay good enough across long, tool-heavy loops where latency and supervision matter.

The Gemini API Managed Agents launch makes that concrete. A single call can spin up an Antigravity-powered agent in an isolated, ephemeral Linux environment. The agent can reason, call tools, execute code, manage files, and browse the web. Follow-up calls can reuse an environment, so state can continue instead of every request becoming a fresh stateless prompt. Developers can define custom agents with instructions, skills, and data in AGENTS.md and SKILL.md-style files. That is directly relevant to local OpenClaw and Hermes thinking: what should stay local because it touches credentials or private code, and what can safely move into a managed sandbox because the environment is controlled, disposable, and easier to scale?

[17:00] Codex remote supervision, access tokens, and hybrid environments
OpenAI's Codex direction is about supervision and deployment shape. Codex in the ChatGPT mobile app lets a user connect to active work running on a Mac or remote environment, see live project state, approve commands, review terminal output, screenshots, test results, and diffs, then redirect the task without being at the host machine. That matters because long-running coding agents do not fail only from lack of intelligence. They fail because they reach a decision point and wait, or they take the wrong fork because a human was not there to give a tiny bit of judgment.

The enterprise side is just as important. Remote SSH is generally available, Codex can work inside managed remote environments, hooks can scan prompts for secrets or run validators, and programmatic access tokens give non-interactive workflows a scoped workspace identity. The Dell partnership points at hybrid and on-prem environments where code, data, policies, and approved compute already live. That is the serious Codex story: a coding agent that can be supervised from anywhere while still running near the files, credentials, and controls it needs.

[24:00] Anthropic Stainless and Project Glasswing
Anthropic acquiring Stainless is an agent-connectivity story. Stainless turns API specs into SDKs, CLIs, and MCP servers across languages, and Anthropic says Stainless has generated official Anthropic SDKs since early in the Claude API. For agents, this matters because an agent is only as useful as the systems it can safely and correctly reach. Clean SDKs, CLIs, and MCP servers are not boring wrapper work; they are the handles agents use to act.

Project Glasswing is the darker side of that same acceleration. Anthropic says Claude Mythos Preview has been used with partners to scan more than a thousand open-source projects and identify large numbers of high- or critical-severity vulnerabilities. The bottleneck shifts from finding issues to verifying, disclosing, and patching them. For an agent stack, the lesson is not "turn every model loose on every repo." It is scope, evidence, verification, and repair flow. AI can increase security throughput, but the human and maintainer process has to absorb the findings without causing chaos.

[32:00] GitHub projects: codebase intelligence for Claude Code, Codex, and Hermes
The best GitHub project lane for this stack starts with codebase intelligence. Serena brings MCP-based semantic retrieval, editing, refactoring, and debugging tools. Claude Context gives Claude Code and other agents semantic code search over large repos. Sourcebot self-hosts code search, navigation, file exploration, and repo Q&A with citations. Understand-Anything turns codebases into interactive graphs that humans and agents can ask questions about. Chunkhound and Code Review Graph push local-first code intelligence and persistent maps.

The practical test is simple: pick one large repo and ask an agent to plan a change twice. First, let it use only built-in search and transcript context. Then give it a semantic map or MCP code-intelligence tool and see whether the plan touches fewer wrong files, asks better questions, and avoids context bloat. If the answer is yes, the stack upgrade is not a bigger prompt. It is a better map.

[39:00] GitHub projects: current docs, model routing, MCP builders, local agents, and security scanners
The second project group changes operation rather than context. Claude Code Router routes requests across providers and models, which is useful when background work, cheap work, long-context work, and high-reasoning work should not all hit the same model. mcp-use helps build and inspect MCP servers and apps in TypeScript or Python. goose is a local desktop/CLI/API agent with multi-provider and MCP extension support. gstack packages Claude Code roles and workflows for review, QA, release, security, and planning. deepsec uses coding agents for vulnerability scanning. context-mode and setup-sync tools try to reduce output noise and keep multi-harness setups consistent across Claude Code, Codex, OpenCode, Gemini CLI, and adjacent agents.

Context7 belongs in this group because current library documentation is one of the quickest ways to reduce stale API hallucinations. Claude Code Router is useful only when provider choice remains visible. mcp-use is strongest when the first tool surface is narrow and inspectable. goose is worth watching as a local agent comparison point. gstack is useful if its roles produce concrete review evidence rather than polished ceremony. deepsec belongs in scoped security work where findings can be verified. These projects are interesting because they sit between the model, the repo, the tools, and the human decision loop.

[46:00] Close
The queue from EP057 is direct. OpenClaw v2026.5.22 makes the gateway, plugins, meeting-notes sources, provider fallbacks, session navigation, and Discord controls more solid. Claude Code 2.1.149 improves usage visibility, diff review, task-list rendering, managed cloud MCP connector policy, and shell/sandbox safety. Gemini Managed Agents show that remote agent sandboxes are becoming productized. Codex is moving toward mobile-supervised, token-scoped, hook-governed, hybrid execution. Anthropic's Stainless and Glasswing work shows SDK/MCP generation and AI security scanning converging. The GitHub radar is the practical layer: code maps, current docs, routers, MCP builders, local agents, role packs, scanners, and setup tools that earn their place only when they make agent work more concrete and verifiable.
```

## Chapters

- 00:00 Release fixes, AI news, and real project radar
- 02:00 OpenClaw v2026.5.22 and Claude Code 2.1.149 release readout
- 10:00 Gemini 3.5 Flash and Gemini API Managed Agents
- 17:00 Codex remote supervision, access tokens, and hybrid environments
- 24:00 Anthropic Stainless and Project Glasswing
- 32:00 GitHub projects: codebase intelligence for Claude Code, Codex, and Hermes
- 39:00 GitHub projects: current docs, model routing, MCP builders, local agents, and security scanners
- 46:00 Close

## Verified Links

- OpenClaw v2026.5.22 release: https://github.com/openclaw/openclaw/releases/tag/v2026.5.22
- Claude Code changelog: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md
- Claude Code npm package: https://www.npmjs.com/package/@anthropic-ai/claude-code
- Gemini 3.5: https://blog.google/intl/en-africa/products/explore-get-answers/gemini-3-5/
- Gemini API Managed Agents: https://blog.google/innovation-and-ai/technology/developers-tools/managed-agents-gemini-api/
- Codex from anywhere: https://openai.com/index/work-with-codex-from-anywhere/
- OpenAI and Dell Codex enterprise partnership: https://openai.com/index/dell-codex-enterprise-partnership/
- Anthropic acquires Stainless: https://www.anthropic.com/news/anthropic-acquires-stainless
- Project Glasswing initial update: https://www.anthropic.com/research/glasswing-initial-update
- Serena: https://github.com/oraios/serena
- Context7: https://github.com/upstash/context7
- Claude Code Router: https://github.com/musistudio/claude-code-router
- Claude Context: https://github.com/zilliztech/claude-context
- Sourcebot: https://github.com/sourcebot-dev/sourcebot
- Understand-Anything: https://github.com/Lum1104/Understand-Anything
- Chunkhound: https://github.com/chunkhound/chunkhound
- Code Review Graph: https://github.com/tirth8205/code-review-graph
- mcp-use: https://github.com/mcp-use/mcp-use
- goose: https://github.com/aaif-goose/goose
- gstack: https://github.com/garrytan/gstack
- deepsec: https://github.com/vercel-labs/deepsec
- context-mode: https://github.com/mksglu/context-mode
- ai-setup: https://github.com/caliber-ai-org/ai-setup
