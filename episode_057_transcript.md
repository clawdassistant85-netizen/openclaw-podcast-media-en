# AgentStack Daily EP057: OpenClaw, Claude Code, Gemini Managed Agents, Codex Remote Work, Anthropic Tooling, and Agent-Stack Projects

[NOVA]: I'm NOVA.

[ALLOY]: I'm ALLOY, and this is AgentStack Daily. Today starts with OpenClaw v2026.5.22 and Claude Code 2.1.149, because both releases changed the machinery that agent stacks depend on: gateway startup, plugin metadata, meeting notes, Discord callbacks, cloud MCP connectors, usage accounting, diffs, and shell safety.

[NOVA]: Then the news moves outward. Google is turning Gemini agents into managed remote Linux environments. OpenAI is putting Codex work under mobile supervision and into hybrid enterprise setups. Anthropic bought Stainless and updated Project Glasswing, which puts SDK generation, MCP servers, and AI security scanning in the same conversation.

[ALLOY]: And the GitHub project lane is real today: semantic code maps, current documentation tools, model routers, MCP builders, local agents, role packs, and security scanners. Not repo trivia. Tools that can change what Claude Code, Codex, Hermes, OpenClaw, and MCP clients can actually see and do. [PAUSE]

## [00:00-10:00] OpenClaw v2026.5.22 and Claude Code two point one release readout

[NOVA]: OpenClaw v2026.5.22 is a dense release, but the headline is clean: the gateway gets less brittle, the plugin surface gets more reusable, meeting notes become a better source of agent context, and several provider and media paths get sharper.

[ALLOY]: Start at gateway startup. OpenClaw now uses process-stable channel catalog reads and plugin metadata snapshot reuse. That means the system can lean on stable catalog and metadata state instead of repeatedly rebuilding the same picture of the world. For a local agent host, that matters because startup and status checks are the first friction point. If the host is noisy before the task begins, everything above it feels unreliable.

[NOVA]: Lazy startup-idle plugin work goes in the same bucket. Work that does not need to block the first usable moment can wait. Irrelevant Linuxbrew path probes get skipped. Core gateway method handlers and public-surface alias maps get cleaned up. These are not flashy features, but they change the feel of the control plane: fewer pointless checks, more predictable method names, and less work happening just because the process woke up.

[ALLOY]: Meeting notes get one of the most important capability updates. External meeting-notes plugins and source providers now have a cleaner contract. Capture can auto-start from config. Manual imports are supported. Read-only CLI access exists. Discord voice is treated as a first live source instead of a side entrance.

[NOVA]: That is a real agent-stack feature because a lot of valuable instruction does not arrive as neat typed text. It arrives as a call, a voice note, a quick correction, or a channel discussion. Turning those sources into structured, readable context without giving every tool write access to the source record is the useful part.

[ALLOY]: The plugin SDK also gets more ordinary operations built in: generic channel-message poll sending, session workflow helpers, and clearer embedding-provider capability contracts. That sounds like plumbing, but it is the kind of plumbing that stops every plugin author from inventing a slightly different version of the same tool call.

[NOVA]: Subagents get less wasteful too. The default bootstrap is trimmed down toward the files that matter most, and native subagent completion handoff gets fixes. In practice, a delegated agent needs enough context to do the task and a reliable path to return the answer. Too much inherited context makes the subagent sluggish; a broken handoff makes good work disappear into the wrong place.

[ALLOY]: The chat-session picker gets search and Load More pagination. That is a small UI feature until the system has weeks of real sessions. Then finding an old run becomes part of the work. A gateway with history needs navigation, not just a pile of recent chats.

[NOVA]: Discord component callbacks now have a bounded lifetime. That is a healthy change for review buttons, approvals, and little interactive controls. A button on an old message should not stay live forever just because the message still exists. The interaction surface now has a clearer expiration model.

[ALLOY]: Provider handling gets more concrete as well. xAI OAuth can be reused for Grok web search. Model aliases and operation timeouts get cleanup. Antigravity CLI becomes a lower-priority image and video fallback after configured provider APIs. Codex API-key image generation uses the native OpenAI Images API. Local Chrome and local Ollama proxy bypasses get fixes.

[NOVA]: That is the real provider story: not just which model answers, but how auth is reused, how long calls are allowed to run, which fallback wins, and whether local services are accidentally routed through the wrong proxy. Agent stacks fail at those edges as often as they fail at reasoning.

[ALLOY]: OpenClaw also refreshes dependencies, moves protobufjs to 8.4.0, tightens locked dependency work, prunes catalogs, cleans up session write locks, adds stricter behavior for vLLM tool-free turns, and fixes Telegram topic handling. This is a maintenance release with a long tail, but the shape is coherent: startup, source capture, plugin reuse, provider correctness, session navigation, and dependency hygiene.

[NOVA]: The Claude Code update is smaller, but it lands in daily use. The `/usage` command can break down limit usage by category: skills, subagents, plugins, and per-MCP-server cost. That is a meaningful change because coding-agent sessions are no longer one model call. They are tool calls, MCP calls, helper agents, skills, plugins, and sometimes background work. Usage needs a map.

[ALLOY]: `/diff` detail view gets keyboard scrolling. Markdown output renders GitHub-flavored task-list checkboxes. Those are ergonomic fixes, but terminal agents live and die on review surfaces. A better diff view and clearer task lists mean less friction when a human is deciding whether the agent actually did the thing.

[NOVA]: Enterprise admins get `allowAllClaudeAiMcps`, a managed setting for loading claude.ai cloud MCP connectors alongside managed MCP config. That is the policy side of the MCP story. Cloud connectors are useful, but organizations need a clear switch for which connector surfaces are allowed instead of letting every user improvise.

[ALLOY]: The fixes are the more serious part. Claude Code repairs PowerShell permission bypasses through built-in directory-changing functions. It fixes sandbox write allowlists that could cover too much of a git worktree. It fixes PowerShell prefix and wildcard rule bugs. It corrects stale variable tracking around PWD, OLDPWD, and DIRSTACK. It fixes a macOS `find` problem that could exhaust file tables on large directories.

[NOVA]: That is a shell-safety release note, not just a bug list. Coding agents run commands in messy environments. Directory-changing builtins, wildcard rules, worktrees, environment variables, and file-descriptor limits are exactly where a safe-looking policy can leak. A CLI agent that takes permissions seriously has to handle those boring edges.

[ALLOY]: The next patch is on npm latest, but its changelog entry is internal infrastructure only. So the user-facing delta is the earlier patch we just covered. That distinction matters: install numbers can move, while the feature story belongs to the release that actually changed behavior.

[NOVA]: Codex and Hermes do not have newer stable tags for this release readout, but they stay in the episode because the news around remote Codex supervision, MCP tooling, local agents, and code-intelligence repos affects the same stack. The release segment is the foundation; the rest of the episode is where the environment around that foundation is moving. [PAUSE]

[ALLOY]: The strongest use case for this OpenClaw release is a gateway that has to host several real surfaces at once: chat, voice, plugins, media generation, search, and subagents. A toy setup can survive awkward startup behavior. A daily build cannot. When channel catalogs, plugin metadata, source capture, and provider fallbacks all get cleaner in the same release, the agent host becomes less of a pile of lucky paths.

[NOVA]: The strongest use case for the Claude Code update is a team that has moved beyond one terminal and one model call. Usage by category tells you whether skills, plugins, subagents, or MCP servers are driving limits. Better diff navigation makes code review less painful. Cloud MCP policy gives administrators a clearer build surface. The PowerShell and sandbox fixes are the guardrails that make those features less scary in real shells.

[ALLOY]: Put together, the release news is not just "update your tools." It is that the local gateway and the coding CLI are both absorbing the hard lessons of agent work: context comes from messy sources, tools need policy, provider behavior needs names, and shell boundaries need to be precise. That is the build direction to watch.

## [10:00-17:00] Gemini 3.5 Flash and Gemini API Managed Agents

[ALLOY]: Google's Gemini story has two layers. The first is the model: Gemini 3.5 Flash is positioned for agentic work and coding, with claims around Terminal-Bench, GDPval-AA, MCP Atlas, multimodal speed, and long-horizon tasks.

[NOVA]: Those benchmark names matter because they point at tool-heavy work. A model can be charming in chat and still fall apart when it has to use a terminal, call tools, inspect files, recover from bad observations, and keep state across a long task. Google is explicitly trying to sell Flash as fast enough for loops and capable enough for agent work.

[ALLOY]: The second layer is more important: Gemini API Managed Agents. Developers can start an Antigravity-powered agent inside an isolated, ephemeral Linux environment. The agent can reason, call tools, execute code, manage files, and browse the web. Follow-up calls can reuse the environment, so a task can continue with actual session state instead of pretending every request starts from nowhere.

[NOVA]: That environment model is the product. It is not only "send a prompt to a model." It is a remote Linux workspace with tools, files, browsing, continuation, and agent instructions. Google also says custom agents can be defined with AGENTS.md and SKILL.md-style files, plus extra data. That is a clear signal that the harness around the model is becoming a first-class API surface.

[ALLOY]: For OpenClaw, Hermes, Codex, and Claude Code users, the interesting comparison is not local versus cloud as a slogan. It is what the environment is allowed to know and do. A managed sandbox is useful when the task is public, disposable, or easy to reset: inspect an open-source repo, run a clean reproduction, browse docs, transform a non-sensitive dataset, or build a prototype in a controlled workspace.

[NOVA]: Local agents still have the advantage when the work depends on private files, local credentials, subscribed tools, a real browser profile, device access, or a machine-specific setup. The managed-agent news does not erase the local stack. It gives builders another execution shape: disposable remote state instead of personal workstation state.

[ALLOY]: The feature delta to remember is stateful managed execution. A remote agent that can keep files, continue a session, and browse inside an isolated Linux environment is different from a stateless model endpoint. It can accumulate evidence. It can install dependencies. It can leave behind artifacts for the next call. It can also create lock-in around the platform's sandbox and tool model.

[NOVA]: That is why the custom instruction-file support matters. AGENTS.md and SKILL.md-style files let the environment carry project rules and specialized behavior. The same trend shows up across coding agents: the model is only one part. The rules, tools, filesystem, browser, policy, and continuation model decide whether the agent can work like software or only talk about software.

[ALLOY]: The practical recommendation is short: use managed Gemini agents first where isolation is the point. Public repo triage, clean bug reproduction, generated scripts, and doc-backed research are natural fits. Keep secrets, private repos, and machine-specific workflows in local or tightly controlled environments until the managed boundary is clearly understood.

[NOVA]: The bigger industry signal is that agent infrastructure is now being sold directly. Not hidden as internal orchestration, not bolted on as a demo. The sandbox, tool runner, browsing layer, session store, and custom agent files are part of the developer product. [PAUSE]

[ALLOY]: One use case jumps out immediately: reproducible investigation. A managed agent can start from a clean Linux environment, fetch a public issue, build the reproduction, and leave a stateful trail for a follow-up call. That is different from asking a chatbot what might be wrong. The environment can contain the actual checkout, logs, generated artifacts, and commands that produced them.

[NOVA]: Another use case is disposable automation around public data. A managed agent can browse, execute code, and keep session state without touching a personal laptop. That is useful for research tasks, generated examples, public benchmark checks, and small data transforms. It is not the right place for every private build, but it is exactly the right shape for work where clean isolation is an advantage.

[ALLOY]: The build implication is that AGENTS.md and SKILL.md-style files are becoming portable agent packaging. A project can carry its own rules, tool preferences, and conventions into a remote agent environment. That makes the instruction layer more durable than a one-off prompt and more inspectable than an invisible product preset.

## [17:00-24:00] Codex remote supervision, access tokens, and hybrid environments

[ALLOY]: OpenAI's Codex news is about where coding-agent work lives and how humans supervise it. Codex in the ChatGPT mobile app can connect to active work running on a Mac or remote environment. The mobile view can show live project state, terminal output, screenshots, test results, and diffs. The user can approve commands and redirect the task.

[NOVA]: That changes the shape of long-running coding work. The agent can keep running near the workspace, while the approval surface moves to the human. A session does not have to stall just because the person left the desk. The important part is not mobile novelty. It is separating execution location from supervision location.

[ALLOY]: Secure relay state is the architecture to watch. The code, credentials, dependencies, and tools stay where the agent is actually running. The human receives enough live state to make decisions elsewhere. That is a better pattern than dragging every local secret into a remote chat surface.

[NOVA]: Remote SSH being generally available fits the same direction. Codex can work against a remote host where the repo and dependencies already live. That could be a development box, a cloud VM, a workstation, or a managed enterprise environment. The execution boundary becomes a deployment choice, not a side effect of where the chat window is open.

[ALLOY]: Programmatic access tokens are another important piece. Coding agents that run in automation need scoped identity. A browser session or a long-lived personal secret is a shaky basis for non-interactive work. Tokens give agent workflows a narrower, revocable way to act inside a workspace.

[NOVA]: Hooks add policy around that action. They can scan prompts for secrets, run validators, block risky operations, or enforce local rules before work moves forward. This is where Codex starts to look less like a clever terminal helper and more like an agent work system with checkpoints.

[ALLOY]: The Dell partnership points at the enterprise version: Codex in hybrid and on-prem environments. Some organizations cannot casually move source code, logs, or data into a public cloud coding loop. Hybrid Codex is about letting the agent operate closer to approved compute, storage, and policy boundaries.

[NOVA]: The concrete Codex capability shift is this: mobile supervision, remote hosts, scoped tokens, hooks, and hybrid environments all point to coding agents that can run near the data while being supervised from somewhere else. That is the useful framing. Not "agent on my laptop" versus "agent in the cloud," but "where should this task execute, and where should the human approve it?"

[ALLOY]: There is also a human-factors change. Diffs, screenshots, terminal output, and test results are becoming review objects that travel. If those objects are clear, remote supervision feels like control. If they are vague, mobile supervision becomes a tiny window into a black box.

[NOVA]: So the recommendation is not to throw big refactors at a phone. Use mobile Codex supervision for narrow decision points: approve a safe command, inspect a diff summary, redirect a branch choice, stop a task that took the wrong path. The heavy evidence still has to be good enough to trust.

[ALLOY]: The enterprise recommendation is similar. Use tokens and hooks for the automations that need non-interactive identity. Keep the execution environment close to the repo, secrets, and policy it needs. Codex is moving toward a world where agent work can be remote, supervised, and governed without pretending location no longer matters. [PAUSE]

[NOVA]: The immediate use case is remote review of a long-running coding session. The agent has already built a branch, run tests, and prepared a diff. The human is away from the desk, but can still see enough evidence to approve a command, reject a risky direction, or stop the session. That turns idle waiting time into a supervised checkpoint.

[ALLOY]: The enterprise use case is controlled execution. A Codex environment can live near the codebase, internal dependencies, and approved compute. Mobile or remote supervision can happen outside that boundary, but the files and credentials do not have to move with the reviewer. That is the architectural difference between convenient remote control and reckless remote access.

[NOVA]: Hooks make this more than remote screen-peeking. A hook can block a secret from entering the prompt, require a validator before a patch is considered ready, or enforce a repo boundary before the agent acts. Programmatic tokens give those jobs a scoped identity. Together, they make Codex look more like a governable build system for agent work.

## [24:00-32:00] Anthropic Stainless and Project Glasswing

[NOVA]: Anthropic acquiring Stainless is an agent-connectivity story. Stainless turns API specs into SDKs, CLIs, and MCP servers across languages. Anthropic says Stainless has generated official Anthropic SDKs since early in the Claude API.

[ALLOY]: That matters because agents need handles. An agent that can only read text is limited. An agent that can call a typed SDK, invoke a CLI, or use an MCP server can act on real systems. The quality of those generated surfaces decides whether the action is safe, predictable, and understandable.

[NOVA]: API specs are becoming agent infrastructure. A clean spec can become documentation, client libraries, command-line tools, and MCP tool surfaces. A vague spec becomes a vague agent tool. If the method names are unclear, auth is underspecified, pagination is inconsistent, or errors are noisy, the agent inherits that ambiguity.

[ALLOY]: Stainless inside Anthropic makes that tool-generation path more central to the Claude ecosystem. It is not hard to imagine a future where creating a good API spec also creates a good Claude-facing tool surface: SDK for application code, CLI for humans and automation, MCP server for agents.

[NOVA]: The short builder implication is simple: if an internal API should be used by agents, the spec quality now matters more. Types, auth scopes, read-only methods, mutating methods, pagination, rate limits, and errors are no longer only developer-experience details. They are the difference between an agent that can call the system cleanly and an agent that improvises.

[ALLOY]: Project Glasswing is the other half. Anthropic says Claude Mythos Preview has been used with partners across more than a thousand open-source projects and found large numbers of high- and critical-severity vulnerabilities. The headline is not only "AI finds bugs." It is that frontier models can increase the rate of vulnerability discovery enough that verification and disclosure become the bottleneck.

[NOVA]: That is a very different pressure than ordinary code review. A model may surface a real exploit path, a partial issue, a false positive, or a finding that needs careful disclosure. Finding more possible issues is useful only if maintainers can verify, prioritize, patch, and communicate responsibly.

[ALLOY]: This connects directly to MCP and SDK generation. Better generated tools give agents more reach into systems. Better security models give agents more ability to inspect those systems. The same acceleration makes both productivity and risk larger.

[NOVA]: The practical recommendation is to treat agent-assisted security scanning as a scoped activity, not a casual background hobby. Use it where the repository, evidence requirements, disclosure path, and repair owner are clear. The output should be a finding with evidence and a patch direction, not a dramatic pile of claims.

[ALLOY]: Anthropic's week, taken together, says agents need better interfaces and better brakes. Stainless is the interface story: turn specs into SDKs, CLIs, and MCP servers. Glasswing is the brake story: faster discovery needs verification, disclosure, and repair capacity.

[NOVA]: The strongest version of this stack is not an agent with unlimited reach. It is an agent with well-described tools, narrow permissions, visible logs, and enough security help to find real flaws without flooding maintainers with noise. [PAUSE]

[ALLOY]: The Stainless use case is straightforward: turn a service description into tools that both people and agents can actually use. A clean API spec can produce a typed SDK for application code, a CLI for scripts and humans, and an MCP server for agent calls. That creates one source of interface truth instead of three drifting wrappers.

[NOVA]: The Glasswing use case is not casual bug hunting. It is targeted security discovery backed by evidence. A model that can inspect large codebases and find high-severity issues changes the economics of vulnerability research. But the useful output is still a verified finding, a minimal repair path, and a disclosure decision. Without that, faster discovery just creates a larger queue of uncertainty.

[ALLOY]: The strategic point is that connectivity and security now accelerate together. The easier it gets to build tool surfaces, the easier it gets for agents to act. The stronger the models get at vulnerability discovery, the more those tool surfaces need narrow permissions and auditability. Stainless and Glasswing are two sides of the same agent-infrastructure build.

## [32:00-39:00] GitHub projects: codebase intelligence for Claude Code, Codex, and Hermes

[ALLOY]: The first GitHub project group gives coding agents better eyes. The names are Serena, Claude Context, Sourcebot, Understand-Anything, Chunkhound, and Code Review Graph.

[NOVA]: Serena is the most direct MCP-flavored upgrade here. It gives coding agents semantic retrieval, editing, refactoring, and debugging tools that behave more like IDE capabilities. The important feature is symbol-level work: definitions, references, relationships, and refactor paths instead of only text matches.

[ALLOY]: That matters because grep is not code understanding. It is a fast flashlight. A coding agent needs to know where a symbol is defined, where it is used, what depends on it, and what tests cover the path. Serena tries to put those IDE-like moves behind a tool surface an agent can use.

[NOVA]: Claude Context is a semantic code-search MCP for Claude Code and other agents. Its job is to make large repos searchable by meaning without stuffing huge directories into the prompt. That is useful when the code name does not match the human description, or when the relevant logic is scattered across files.

[ALLOY]: Sourcebot is the self-hosted code search and understanding surface. It offers repo search, navigation, file exploration, and Ask Sourcebot Q&A with citations. The self-hosted part matters because code intelligence often touches private repositories. A shared, cited search surface can help humans and agents argue from the same evidence instead of from vibes.

[NOVA]: Understand-Anything turns codebases into interactive knowledge graphs with search and Q&A, and it explicitly positions itself for Claude Code, Codex, Cursor, Copilot, Gemini CLI, and related tools. A graph is not magic, but it can show architecture shape before an agent starts editing a system it barely understands.

[ALLOY]: Chunkhound and Code Review Graph push the local-first and persistent-map angle. That is the right category for teams that want semantic or graph context without sending the whole repo somewhere else. A persistent code map can reduce context waste by feeding the agent the few relationships that matter instead of a giant transcript dump.

[NOVA]: The recommendation for this group is to choose based on what the agent is missing. If it misses symbols and references, look at Serena. If it needs semantic search inside Claude Code, look at Claude Context. If humans and agents need a shared self-hosted code browser, look at Sourcebot. If architecture shape is the problem, Understand-Anything is interesting. If local indexing and persistent code maps matter most, Chunkhound and Code Review Graph belong on the shortlist.

[ALLOY]: The reason this is a news lane, not just a tools list, is that code context is becoming its own layer in the stack. Bigger context windows help, but they do not replace retrieval quality. A model that sees a better map can make a smaller, more accurate edit. That is often more valuable than handing it another thousand irrelevant files.

[NOVA]: This is where Hermes, OpenClaw, Codex, and Claude Code all benefit from common tool surfaces. If code intelligence is available through MCP, local indexes, or self-hosted search, it can sit below several agents. The agent changes; the repo map stays useful.

[ALLOY]: The short recommendation is: add one code-intelligence layer only where repo size justifies it. A one-file script does not need a semantic graph. A mature codebase with scattered behavior probably does. [PAUSE]

[NOVA]: Serena's best use case is symbol-aware editing. A refactor that crosses definitions, references, and tests benefits from an MCP tool that understands code relationships. Claude Context's best use case is semantic retrieval when the prompt describes behavior but the code uses different names. Sourcebot's best use case is a self-hosted search surface where humans and agents can share citations.

[ALLOY]: Understand-Anything is stronger when architecture shape matters: unfamiliar services, hidden dependencies, or a repo where the call graph explains more than filenames do. Chunkhound and Code Review Graph fit the local-first use case, where persistent maps are valuable but code cannot casually leave the machine or trusted network.

[NOVA]: The build trend is clear: code context is becoming a reusable substrate. The agent harness may be Claude Code today, Codex tomorrow, Hermes next week, and OpenClaw around all of it. A good repo map can serve all of those surfaces if it is exposed through MCP, a local index, or a self-hosted search layer.

[ALLOY]: That is why this project lane matters. It is not only about making one model smarter. It is about giving every coding agent a better starting point: fewer irrelevant files, more exact references, clearer architecture, and a shorter path from question to evidence.

## [39:00-46:00] GitHub projects: model routing, MCP builders, local agents, and security scanners

[NOVA]: The second project group changes how the stack runs. Context7, Claude Code Router, mcp-use, goose, gstack, deepsec, context-mode, and ai-setup all sit between the model, the repo, the tools, and the human.

[ALLOY]: Context7 handles current documentation. Coding agents often fail because their library memory is stale. Context7 gives LLMs and coding agents up-to-date library docs through CLI, skills, or MCP. It is especially useful for fast-moving JavaScript, Python, AI SDK, and framework tasks where old examples look plausible but break.

[NOVA]: Claude Code Router is about provider and model routing. It can route Claude Code requests across OpenRouter, DeepSeek, Ollama, Gemini, and other backends, with transformers and route-specific model choices. The value is matching the backend to the work: cheap summaries, local experiments, long-context reads, or high-reasoning reviews.

[ALLOY]: The risk is accountability. A router is only helpful if the route is visible enough that the user knows which provider and model handled the task. Hidden routing can save money and create confusion at the same time.

[NOVA]: mcp-use is a framework for building MCP apps and servers in TypeScript and Python, with inspection and deployment paths. That is important because MCP is moving from novelty to integration layer. Teams need a faster way to build small tools, inspect calls, and package them for agents without hand-rolling every server.

[ALLOY]: goose is a local AI agent with desktop, CLI, API, multi-provider support, ACP paths, and MCP extensions. It is now under the Agentic AI Foundation, and it is worth watching as a local agent fallback or comparison point. The interesting part is not whether it replaces everything. It is whether its provider and extension model makes some local tasks easier to run outside a heavier stack.

[NOVA]: gstack packages Claude Code roles and workflows for review, QA, release, security, planning, and product work. Role packs can become theater if they only rename ordinary prompts, but they are useful when they encode repeatable review behavior, expected evidence, and consistent output shapes.

[ALLOY]: deepsec is the security scanner in this lane. It uses coding agents for vulnerability scanning across large codebases, with resumable scans, matchers, processing, revalidation, and export. That puts it in the same universe as Glasswing, but as a GitHub-hosted tool builders can inspect and run in scoped settings.

[NOVA]: context-mode and ai-setup aim at two everyday problems: output noise and setup drift. Once a stack includes Claude Code, Codex, OpenCode, Gemini CLI, Hermes, OpenClaw, local models, MCP servers, and routers, configuration can become the hidden failure mode. Tools that keep context tight and setup consistent can be more useful than another model picker.

[ALLOY]: The recommendation for this group is also job-based. Use Context7 when current docs are the missing piece. Use Claude Code Router when provider choice really matters. Use mcp-use when a private capability should become an MCP tool. Use goose when a local agent with extensions is the right comparison. Use gstack when repeatable review roles matter. Use deepsec only when security findings can be verified and handled.

[NOVA]: The larger trend is that the agent stack is filling in the middle. We already have models and chat surfaces. The new activity is in routers, docs retrieval, MCP builders, local agent shells, role packs, code maps, and scanners. That is where agent work becomes more controllable.

[ALLOY]: It also makes discipline more important. Every extra tool adds authority, configuration, or another place for evidence to disappear. A good project earns its place by making the task clearer: better docs, better code context, clearer provider routing, narrower tool access, or more verifiable security findings. [PAUSE]

[NOVA]: Context7's core use case is fast-moving libraries. When a framework, AI SDK, or database client changes quickly, stale model memory produces code that looks right and fails at runtime. Current docs in the agent loop are a simple way to improve the build without changing models.

[ALLOY]: Claude Code Router's use case is workload separation. A cheap model can summarize logs. A local model can handle private background reading. A stronger model can review a risky patch. The router is useful when those choices are explicit; it is dangerous when routing becomes invisible.

[NOVA]: mcp-use is the build tool in this group. It lowers the cost of turning a small capability into an MCP server or app, especially in TypeScript and Python. The first good use case is usually read-only: status lookup, documentation search, inventory query, or a narrow internal report. Once the shape is understandable, write actions can be treated as a separate privilege.

[ALLOY]: goose is the local-agent use case. It gives builders another desktop, CLI, and API surface with provider and MCP extension support. gstack is the repeatable-role use case: review, QA, release, planning, and security prompts that behave consistently enough to be judged. deepsec is the security use case, with resumable scans and exported findings. context-mode and ai-setup are the consistency use case, keeping output and configuration from sprawling as the stack grows.

[NOVA]: The useful pattern across all of them is not procedure for its own sake. It is choosing the tool that changes the outcome: fewer stale APIs, clearer provider choice, a narrower MCP surface, a local agent that can run without the heavy stack, a review role that finds concrete bugs, or a scanner that produces evidence instead of noise.

[ALLOY]: There is one more stack-level point in this project lane. These tools are not competing only on model quality. They are competing on context quality, routing clarity, interface shape, and evidence. Context7 improves the documentation input. Serena and Sourcebot improve the code input. Claude Code Router changes the model path. mcp-use changes the tool interface. goose changes the local execution shell. deepsec changes the security lens. Those are different layers, and mixing them up makes the stack harder to reason about.

[NOVA]: The best use case for this whole lane is a builder who already has a capable model and still gets mediocre results because the surrounding system is weak. The agent reads stale docs. It misses the right file. It uses the expensive model for a cheap summary. It cannot call the internal system cleanly. It produces a security claim with no evidence. The projects in this lane attack those failure modes directly.

[ALLOY]: That is why this is more interesting than a star-count roundup. A repo earns attention when it changes one of the hard surfaces around agent work: what the model knows, which model answers, what tools are callable, where execution happens, how code is mapped, or how findings are verified. That is a concrete stack upgrade, not a new badge for the README.

[NOVA]: The strongest builds will combine these layers carefully. Current docs for fast libraries. Semantic code maps for large repos. Visible routing for provider choice. Small MCP servers for private capabilities. Local agents for sensitive execution. Security scanners where the evidence can be handled. The value is not having every tool installed. The value is knowing which layer is weak and adding only the piece that strengthens it.

## [46:00-50:00] Close

[NOVA]: EP057's stack update is straightforward. OpenClaw v2026.5.22 makes the gateway, plugin layer, meeting-notes sources, provider fallback behavior, session navigation, and Discord controls more solid. Claude Code improves usage visibility, diff review, task-list rendering, managed cloud MCP connector policy, and several shell and sandbox safety edges. The following patch is internal-only.

[ALLOY]: Google's Gemini news says managed agent environments are now a product surface: remote Linux execution, tools, browsing, files, session continuation, and custom agent instruction files. OpenAI's Codex news says coding-agent work is becoming remote, mobile-supervised, token-scoped, hook-governed, and enterprise-deployable.

[NOVA]: Anthropic's Stainless acquisition says SDKs, CLIs, and MCP servers are becoming core agent infrastructure. Project Glasswing says frontier models can find vulnerabilities quickly enough that verification and disclosure become the bottleneck.

[ALLOY]: The GitHub project radar says the useful stack upgrades are not all models. Serena, Claude Context, Sourcebot, Understand-Anything, Chunkhound, and Code Review Graph improve what agents can understand about code. Context7, Claude Code Router, mcp-use, goose, gstack, deepsec, context-mode, and ai-setup improve docs, routing, MCP tooling, local execution, repeatable roles, security scanning, and setup consistency.

[NOVA]: The short recommendation is to update the core tools, then add only the projects that solve a visible problem. Better code maps for large repos. Current docs for fast-moving libraries. Model routing where provider choice matters. MCP builders for scoped tools. Security scanners where there is a real verification path.

[ALLOY]: That is the useful version of agent news: not a pile of names, and not process for its own sake. Concrete releases, concrete capabilities, and a clearer picture of where the stack is heading.

[NOVA]: Full notes and source links are in the episode notes at Toby On Fitness Tech dot com.

[ALLOY]: Thanks for listening to AgentStack Daily. We'll be back soon.
