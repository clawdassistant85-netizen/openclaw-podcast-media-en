# AgentStack Daily EP060 - Claude Code 2.1.158, Codex Windows Control, Runtime Instructions, and Local Agent Memory

## Release Coverage Check

- **OpenClaw** - Latest stable verified: `v2026.5.27`, published 2026-05-28T11:41:42Z from GitHub releases. Recent episode version tags detected: `v2026.5.27` and `v2026.5.26`. Selected missing versions: none for the stable lane. The visible `v2026.5.28-beta.4` line remains watch material, not a stable release block.
- **Hermes Agent** - Latest stable verified: `v2026.5.29.2` / `v0.15.2`, published 2026-05-29T13:37:26Z from GitHub releases. Recent episode version tags detected: `v2026.5.29.2`, `v2026.5.29`, `v2026.5.28`, and `v2026.5.16`. Selected missing versions: none.
- **OpenAI Codex app/CLI** - Latest stable verified: `rust-v0.135.0`, published 2026-05-28T17:31:35Z from GitHub releases. Recent episode version tags detected: `rust-v0.135.0` and `rust-v0.134.0`. Selected missing versions: none for the CLI release lane; the May 29 ChatGPT/Codex app update is included as product news.
- **Claude Code CLI** - Latest npm `latest` verified: `2.1.158`, published 2026-05-30T01:12:23Z; npm `stable` dist-tag verified as `2.1.149`. Recent episode version tags detected: `2.1.157`, `2.1.156`, and `2.1.154`. Selected missing version from the npm `latest` lane: `2.1.158`.
- **Candidate verification** - EP060 leads with Claude Code `2.1.158` and the May 29 Codex app update, then moves into runtime-instruction control and local agent-memory projects that make long coding-agent sessions less fragile.

## Runtime Target

42-50 min. Source-verified stories around managed-cloud Claude Code auto mode, Codex Windows remote control, runtime instruction changes, architectural memory, local persistent cognition, local-only coding agents, and graph-driven repair.

## Episode Title

Claude Code 2.1.158, Codex Windows Control, Runtime Instructions, and Local Agent Memory

## Tagline

Claude Code extends auto mode to managed clouds, Codex adds Windows computer use and profile telemetry, Anthropic exposes runtime instruction updates, and the project radar focuses on local memory, architecture graphs, local-only coding agents, and verified code repair.

## Feed Description

Claude Code `2.1.158` on npm `latest` adds auto mode for Bedrock, Vertex, and Foundry when `CLAUDE_CODE_ENABLE_AUTO_MODE=1` is set. OpenAI's May 29 Codex update adds Windows computer use in the Codex app, remote control from mobile or Mac while the Windows host keeps project files and local context, in-app browser infrastructure improvements, and Codex Profiles for identity, activity, usage stats, and token activity. The episode then covers Anthropic's Messages API system entries as a runtime-control surface, plus OpenLore, Mnemo, OpenMonoAgent, and Prometheus as project-radar examples of local architectural memory, persistent agent cognition, local-only coding agents, and graph-backed repair loops.

## Story Slate

### 1. **Claude Code 2.1.158 and Codex Windows control move managed and local agent supervision**
Claude Code `2.1.158` on npm `latest` is small but operationally specific: auto mode is now available on Bedrock, Vertex, and Foundry for Opus 4.7 and Opus 4.8 when `CLAUDE_CODE_ENABLE_AUTO_MODE=1` is set. OpenAI's May 29 Codex app update is the larger product story: eligible users can use computer use on Windows, supervise a Windows-hosted project from iOS, Android, or Mac, get faster and more stable in-app browser behavior, and inspect Codex Profiles with identity, activity, usage, and token information.
Technical depth angle: explain Claude Code auto-mode gating, managed-cloud provider routing, Windows computer-use host boundaries, remote control transport, browser-runtime improvements, and usage-profile telemetry.
Actionability angle: test Claude Code auto mode behind an explicit environment flag; test Codex Windows computer use on a low-risk app before relying on remote supervision for real work.
Listener hook: the story is about control surfaces today: which runtime owns the files, which cloud provider is allowed to classify risk, and where the human can see usage and steer the session.
Primary links: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md, https://www.npmjs.com/package/@anthropic-ai/claude-code, https://help.openai.com/en/articles/6825453-chatgpt-release-notes

### 2. **Messages API system entries turn running harness state into editable instructions**
Anthropic's Opus 4.8 launch included a developer-facing API change that matters beyond the model headline: the Messages API now accepts system entries inside the messages array. That gives an agent harness a way to update permissions, token budgets, environment notes, or task context mid-run without forcing the update through a user turn or breaking prompt-cache behavior. In long-running coding sessions, that is a cleaner primitive than stuffing every new policy note into a growing prompt or asking the model to infer state from logs.
Technical depth angle: explain system entries inside message arrays, prompt-cache preservation, mid-task instruction updates, permission state, token-budget state, environment context, and how a harness can separate user intent from runtime policy.
Actionability angle: use runtime system entries for machine-generated context such as sandbox status, tool budget, changed test state, or revoked permissions, while keeping user goals and approvals separate and auditable.
Listener hook: long agent runs fail when the harness cannot tell the model what changed; this gives the runtime a more precise way to update the contract.
Primary links: https://www.anthropic.com/news/claude-opus-4-8

### 3. **OpenLore makes architectural memory queryable through MCP**
OpenLore is a local architectural-memory layer for coding agents. It indexes a codebase into static analysis, call graphs, clusters, living specs, drift detection, and MCP tools such as orientation and graph expansion. The useful stack angle is token discipline: instead of every Codex, Claude Code, Hermes, or OpenClaw-connected session rediscovering the same architecture from raw file reads, the agent can ask for a small graph-backed digest and then expand only the part that matters.
Technical depth angle: explain static analysis, call graphs, architectural clusters, living specs, drift detection, MCP orientation tools, graph expansion, and why queryable structure reduces context waste.
Actionability angle: try it first on one repo where agents repeatedly misidentify entry points; compare an edit plan with and without the orientation output before allowing writes.
Listener hook: better agent memory is not just storing transcripts; it is remembering how the codebase is shaped.
Primary links: https://github.com/clay-good/OpenLore, https://github.com/clay-good/OpenLore/releases/tag/v2.0.5

### 4. **Mnemo treats agent memory as a decaying local knowledge graph**
Mnemo is a local-first memory and knowledge-graph project for coding agents. Its README positions it around persistent engineering cognition: project decisions, hooks, hybrid retrieval, graph search, and memory decay so fresh decisions stay important while stale context fades. That is relevant to agent stacks because a coding assistant does not only need to remember facts; it needs to remember how confident and current those facts are.
Technical depth angle: explain tiered memory, decay, BM25 plus vector plus graph retrieval, lifecycle hooks, local storage, codebase knowledge graphs, and why stale memory should be demoted instead of blindly injected.
Actionability angle: start by capturing decisions, conventions, active tasks, and known failure modes, then audit what Mnemo recalls in a second session before letting it feed high-authority edits.
Listener hook: memory without freshness becomes another source of hallucination; decay is what keeps yesterday's helpful context from becoming tomorrow's bad instruction.
Primary links: https://github.com/Mnemo-mcp/Mnemo, https://github.com/Mnemo-mcp/Mnemo/releases/tag/v0.5.0

### 5. **OpenMonoAgent tests the zero-meter local coding-agent pattern**
OpenMonoAgent is a .NET-based local coding agent built around bundled local inference through llama.cpp, Docker sandboxing, LSP/Roslyn code intelligence, MCP integration, and playbooks. The project pitch is direct: no per-token billing and no code leaving the machine by default. For the agent stack, the interesting part is not replacing every cloud model; it is establishing a local baseline for private repo reading, cheap iteration, sandboxed tool use, and provider fallback comparison.
Technical depth angle: explain local llama.cpp inference, GPU/CPU configuration, Docker sandbox boundaries, LSP and Roslyn code intelligence, MCP integration, terminal-native agent loops, and where local models differ from cloud frontier models.
Actionability angle: use a local-only agent first for repo orientation, mechanical edits, and low-risk refactors, then compare failures against Claude Code, Codex, or Hermes before moving sensitive work to a cloud host.
Listener hook: a local agent does not have to beat every frontier model to be useful; it only has to make the cheap, private, repeatable part of the workflow boring.
Primary links: https://github.com/StartupHakk/OpenMonoAgent.ai

### 6. **Prometheus uses code graphs and verification loops for repair**
EuniAI's Prometheus is another project in the codebase-understanding lane, but it frames the problem around graph-driven repair rather than chat-driven edits. The repository describes a knowledge-graph-driven agent that maps, understands, and repairs complex codebases. In a stack that already has Codex, Claude Code, Hermes, and OpenClaw, this is useful as a research target for how agents should move from code maps to evidence-backed fixes instead of jumping from a prompt directly to patches.
Technical depth angle: explain knowledge graphs, codebase mapping, repair loops, verification, autonomous code agents, and how graph context can constrain patch generation.
Actionability angle: evaluate it on a disposable repo or benchmark task, then inspect whether the graph evidence actually changes patch quality, test selection, and failure recovery.
Listener hook: the next coding-agent jump may be less about a single bigger model and more about making the repair loop prove what it understood.
Primary links: https://github.com/EuniAI/Prometheus

## GitHub Project Radar

- **OpenLore** - https://github.com/clay-good/OpenLore - Local architectural memory for AI coding agents with static analysis, living specs, drift detection, and graph-native MCP tools. GitHub API check on 2026-05-30 showed 141 stars and a push on 2026-05-30; latest release `v2.0.5` shipped 2026-05-29. Stack improvement angle: give Codex, Claude Code, OpenClaw, and Hermes a compact architectural orientation layer before they spend context on raw file reads. Try now: run it on one repo and compare its orientation output against a plain text-search planning session.
- **Mnemo** - https://github.com/Mnemo-mcp/Mnemo - Local-first persistent engineering cognition with MCP tools, codebase knowledge graphs, hybrid retrieval, hooks, and memory decay. GitHub API check on 2026-05-30 showed 18 stars, 4 forks, created 2026-05-08, and updated 2026-05-30. Stack improvement angle: store decisions and project memory outside one agent transcript while letting stale memories cool down. Try now: capture one decision, one convention, and one known failure, then start a second session and inspect exactly what is recalled.
- **OpenMonoAgent.ai** - https://github.com/StartupHakk/OpenMonoAgent.ai - Local-first terminal coding agent powered by .NET, llama.cpp, Docker sandboxing, LSP/Roslyn code intelligence, and MCP. GitHub API check on 2026-05-30 showed 1,408 stars, 174 forks, created 2026-04-30, pushed 2026-05-29, and updated 2026-05-30. Stack improvement angle: establish a private no-meter baseline for local repo reading, low-risk edits, and tool-loop experiments. Try now: run it against a disposable repo with no cloud provider configured and compare its plan against a cloud coding agent.
- **Prometheus** - https://github.com/EuniAI/Prometheus - Knowledge-graph-driven software agent for mapping, understanding, and repairing complex codebases. GitHub API check on 2026-05-30 showed 992 stars, 61 forks, and a push on 2026-05-25. Stack improvement angle: study how graph context can constrain autonomous repair instead of letting patch generation start from a flat prompt. Try now: run the project on a sample codebase and inspect whether graph evidence points to the same files a human maintainer would check first.

## Extra Research Candidates

- **AWS Agent Toolkit for AWS** - Primary source: https://aws.amazon.com/about-aws/whats-new/2026/05/agent-toolkit/. Technical depth angle: explain managed MCP, IAM guardrails, CloudWatch/CloudTrail observability, sandboxed multi-step operations, and more than 40 validated skills for infrastructure, analytics, serverless, containers, and AI services.
- **OpenClaw prerelease tracker** - Primary source: https://github.com/openclaw/openclaw/releases. Technical depth angle: track the beta line for app-server recovery, channel identity, provider/media additions, malformed callback rejection, and Discord recovered-tool warnings without treating it as a stable release.
- **Claude Opus 4.8 system card and eval methodology** - Primary source: https://www.anthropic.com/news/claude-opus-4-8. Technical depth angle: compare effort controls, fast-mode pricing, tool efficiency, honesty claims, alignment assessment, and coding-agent benchmark framing against actual harness behavior.

## Show Notes

```md
Claude Code `2.1.158` extends auto mode to Bedrock, Vertex, and Foundry for Opus 4.7 and Opus 4.8 when `CLAUDE_CODE_ENABLE_AUTO_MODE=1` is enabled. OpenAI's May 29 Codex app update adds computer use on Windows, remote control from mobile or Mac while the Windows machine remains the host, faster and more stable in-app browser behavior, and Codex Profiles for identity, activity, usage stats, and token activity. Then the episode moves into Anthropic's Messages API system entries and a project radar around local architectural memory, persistent agent cognition, local-only coding agents, and graph-backed repair.

[00:00] Opening: releases, control surfaces, and memory
The useful AgentStack Daily lane today is control. Claude Code is exposing auto mode across managed cloud providers, but only behind an explicit environment variable. Codex is extending computer use to Windows while keeping project files, shell, app server, and local context on the Windows host. OpenAI is surfacing profile and token activity so agent usage becomes inspectable. Anthropic is giving harness builders a way to update system instructions inside a running message sequence. The project radar then asks the same question at the repo level: how do agents remember architecture, decisions, and repair evidence without dumping everything into the next prompt?

[03:00] Claude Code 2.1.158 and Codex Windows control
Claude Code `2.1.158` adds auto mode support on Bedrock, Vertex, and Foundry for Opus 4.7 and Opus 4.8 when `CLAUDE_CODE_ENABLE_AUTO_MODE=1` is set.

That small release is worth explaining because auto mode is a policy and routing surface, not just a convenience toggle. When a coding agent decides whether an action is safe enough to run automatically, the provider boundary matters. Bedrock, Vertex, and Foundry deployments often exist because a team wants model access inside a managed cloud environment with its own identity, logging, and compliance rules. Making auto mode available there means the automatic-action classifier can be tested in the same managed lane as the rest of the enterprise agent run.

OpenAI's May 29 Codex app update is the other front-of-episode item. Codex computer use now supports Windows for eligible users, so Codex can see, click, and type in Windows applications while testing, debugging, and refining a build. The remote-control shape matters: a user can start work on a Windows machine, then use ChatGPT on iOS or Android, or Codex on Mac, to check progress, respond to prompts, and steer the thread while away from the desk. The Windows machine remains the host for project files, shell, app server, and local context. That is the right boundary for many local workflows: supervision can move, but execution stays near the repo and running app.

Codex Profiles add another inspectability layer. Identity, activity over time, profile details, usage stats, and token activity give eligible users more of the operational surface that long-running agents need. When a daily job fails, when a remote session uses unexpected tokens, or when a profile is tied to the wrong identity, usage evidence is not a luxury. It is how the stack becomes debuggable.

[13:00] Runtime instructions become editable state
Anthropic's Opus 4.8 announcement included a developer API change that deserves its own segment: the Messages API now accepts system entries inside the messages array. For a coding-agent harness, that is a useful primitive. The user goal can stay in the user lane, while runtime facts can be added as system entries when the environment changes.

Think about what changes during a real agent run. A sandbox may become locked down. A token budget may shrink. A test suite may move from failing to passing. A background worker may finish. A tool may be revoked. A repository may switch from one worktree to another. Without a structured way to update runtime state, harnesses tend to stuff these details into ordinary text or ask the model to infer them from logs. System entries inside the message array let the harness say, more precisely, "the operating contract changed."

The prompt-cache angle is also important. Long sessions are expensive because repeating the whole contract burns tokens and makes context heavy. If a harness can update specific system facts without breaking cache behavior, it can keep the agent current without constantly rebuilding the entire prompt. That is especially useful for OpenClaw, Hermes, Codex, Claude Code, and any scheduler that needs to keep a long-running job aligned with current permissions.

[21:00] OpenLore and Mnemo: memory with structure and freshness
OpenLore attacks the orientation problem. Coding agents waste a lot of context rediscovering the same project structure: entry points, call paths, modules, clusters, architectural decisions, and drift. OpenLore turns that into a local graph and MCP-accessible orientation layer. The agent can ask for a compact architecture digest, then expand only the part of the graph relevant to the current task. That is better than reading a directory tree, several files, a README, and a transcript every time a session starts.

Mnemo takes the memory problem in a complementary direction. It focuses on persistent engineering cognition with local-first storage, hybrid retrieval, knowledge graphs, lifecycle hooks, and memory decay. The decay part is the interesting operational detail. Agent memory should not treat every old decision as equally authoritative forever. A fresh convention, an active task, and a known failure mode should be easy to recall. A stale workaround from three weeks ago should cool down unless it is reinforced.

Together these projects point at a better memory layer for agent stacks. OpenLore remembers how the code is shaped. Mnemo remembers what the project learned and how fresh that knowledge is. Both are more useful than dumping old transcripts into every prompt, because both give the harness a way to retrieve smaller, more relevant context.

[31:00] OpenMonoAgent and Prometheus: local agents and graph-backed repair
OpenMonoAgent is a useful local-agent experiment because it is explicit about the no-meter, no-cloud baseline. It runs as a terminal-native coding agent with local inference through llama.cpp, Docker sandboxing, LSP and Roslyn code intelligence, MCP support, and playbooks. It does not need to beat every frontier model to earn a place in the stack. It needs to make private repo reading, mechanical edits, repeatable low-risk refactors, and local tool-loop experiments cheap enough to run often.

The tradeoff is clear. Local models may struggle on harder reasoning and broad synthesis compared with Claude Code, Codex, or a stronger hosted model. But local execution gives a team a useful comparison point: what can be handled without sending code or prompts out, what needs a stronger model, and what should be split into local orientation plus cloud reasoning.

Prometheus sits in the graph-backed repair lane. Its repository describes a knowledge-graph-driven agent for mapping, understanding, and repairing complex codebases. That matters because autonomous repair is where coding agents often get too confident. A graph can constrain the repair loop: which files are connected, which call paths matter, which tests should be selected, and what evidence supports the patch. The goal is not to make a graph magical. The goal is to force the repair step to carry evidence from structure into the patch and verification plan.

[40:00] What to try next
The practical queue from EP060 is specific. Test Claude Code auto mode only behind the explicit environment flag and only in the managed cloud lane where it will actually run. Test Codex Windows computer use on a harmless app before relying on remote supervision for important work. Treat Codex Profiles as operational evidence for identity, usage, and token activity. For harness builders, study system entries inside the Messages API as a cleaner way to update runtime state during long jobs.

Then pick one memory experiment. Use OpenLore when the pain is architectural rediscovery. Use Mnemo when the pain is forgotten decisions and stale context. Use OpenMonoAgent when the pain is privacy, cost, or local repeatability. Use Prometheus when the research question is graph-constrained repair. The daily lesson is simple: agent stacks are becoming more capable, but the durable advantage is still control, evidence, and context that stays small enough to use.
```

## Chapters

- 00:00 Releases, control surfaces, and memory
- 03:00 Claude Code 2.1.158 and Codex Windows control
- 13:00 Runtime instructions become editable state
- 21:00 OpenLore and Mnemo: memory with structure and freshness
- 31:00 OpenMonoAgent and Prometheus: local agents and graph-backed repair
- 40:00 What to try next

## Verified Links

- Claude Code changelog: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md
- Claude Code npm package: https://www.npmjs.com/package/@anthropic-ai/claude-code
- ChatGPT / Codex release notes: https://help.openai.com/en/articles/6825453-chatgpt-release-notes
- Claude Opus 4.8 / Messages API update: https://www.anthropic.com/news/claude-opus-4-8
- OpenLore: https://github.com/clay-good/OpenLore
- OpenLore v2.0.5: https://github.com/clay-good/OpenLore/releases/tag/v2.0.5
- Mnemo: https://github.com/Mnemo-mcp/Mnemo
- Mnemo v0.5.0: https://github.com/Mnemo-mcp/Mnemo/releases/tag/v0.5.0
- OpenMonoAgent.ai: https://github.com/StartupHakk/OpenMonoAgent.ai
- Prometheus: https://github.com/EuniAI/Prometheus
- AWS Agent Toolkit for AWS: https://aws.amazon.com/about-aws/whats-new/2026/05/agent-toolkit/
