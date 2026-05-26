# AgentStack Daily EP057: OpenClaw, Claude Code, Gemini Managed Agents, Codex Remote Work, Anthropic Tooling, and Agent-Stack Projects

[NOVA]: I'm NOVA.

[ALLOY]: I'm ALLOY, and this is AgentStack Daily. OpenClaw v2026.5.22 is first today because it touches the gateway, plugins, meeting notes, Discord callbacks, provider fallbacks, subagent handoff, chat session navigation, and package integrity.

[NOVA]: Claude Code also has a real user-facing CLI update: 2.1.149 adds better usage accounting, diff navigation, task-list rendering, cloud MCP controls, and shell and sandbox fixes. Then we get into Gemini managed agents, Codex remote supervision, Anthropic's Stainless and Glasswing work, and GitHub-hosted projects that actually fit this stack.

[ALLOY]: The project names matter today. Serena, Context7, Claude Code Router, Claude Context, Sourcebot, Understand-Anything, mcp-use, goose, gstack, deepsec, context-mode, and ai-setup are not filler. Full links are in the shownotes and YouTube description. The question is which ones are worth testing against OpenClaw, Codex, Claude Code, Hermes, MCP, and local agent work. [PAUSE]

## [00:00-10:00] OpenClaw v2026.5.22 and Claude Code two point one release readout

[NOVA]: OpenClaw v2026.5.22 and Claude Code two point one fix real stack friction. This is the opposite of a vanity release segment. It is about the little pieces that decide whether an agent system feels reliable after the first neat demo.

[ALLOY]: Start with OpenClaw. The gateway work is not glamorous, but it matters. Process-stable channel catalog reads and plugin metadata snapshot reuse reduce the churn around startup and status. Lazy startup-idle plugin work means the gateway can postpone work that does not need to block the first usable moment. Skipping irrelevant Linuxbrew path probes sounds microscopic until you remember how often local tooling gets slowed down by irrelevant environment checks.

[NOVA]: The meeting-notes work is more obviously useful. External plugins and source providers get a cleaner contract. Capture can auto-start from config. Manual imports are supported. Read-only CLI access exists. Discord voice becomes a first live source instead of a side corridor. That matters for agent stacks because a lot of useful context does not arrive as a perfect text prompt. It arrives as a meeting, a voice note, a channel discussion, or a rough spoken correction.

[ALLOY]: The practical move is to treat meeting notes as an input pipeline, not a loose pile of transcripts. If a system can capture from voice, import manually, and expose read-only access, then an agent can use that material without being allowed to mutate the source. That is the right direction. Agents need memory and context, but they should not get a free pass to rewrite the record.

[NOVA]: The plugin SDK changes point the same way. Generic channel-message poll sending, session workflow helpers, and embedding-provider capability contracts make plugin authors less likely to invent the same fragile glue over and over. The agent system gets better when its extension layer has names for ordinary operations: send a poll, continue a session, check what an embedding provider can actually do, and return a result cleanly.

[ALLOY]: Subagents also get cleaner behavior. OpenClaw trims the default subagent bootstrap down to the files that matter most, and native subagent completion handoff gets fixes. That is exactly where local agent stacks can become frustrating. A subagent can do good work and still fail the human if the answer does not return to the right session, or if the spawned agent starts with too much irrelevant context and too little task shape.

[NOVA]: Chat session search and Load More pagination sound mundane, but they become important once the system has real history. If you use agents every day, the session picker becomes operational infrastructure. You need to find the run that mattered, reopen it, compare it with the current state, and avoid losing the thread because the UI only shows the newest handful of sessions.

[ALLOY]: Discord component callbacks now have a bounded lifetime. That is healthy. Buttons, callbacks, and little interactive controls should not live forever just because a message exists forever. A review button that made sense yesterday may be stale tomorrow. Bounded callback lifetimes keep old interaction surfaces from becoming accidental live controls.

[NOVA]: Provider handling gets better too. xAI OAuth can be reused for Grok web search. Model aliases and default operation timeouts get cleanup. Antigravity CLI becomes a lower-priority image and video fallback after configured provider APIs. Codex API-key image generation uses the native OpenAI Images API. Local Chrome and local Ollama proxy bypasses get fixes. All of that is a reminder that provider routing is not just "which model is smartest." It is auth, timeout behavior, proxy behavior, media fallbacks, and the difference between a request failing clearly and failing like mist.

[ALLOY]: The dependency side is worth mentioning because agent stacks are huge dependency surfaces. OpenClaw refreshes packages, moves protobufjs to 8.4.0, and tightens locked dependency behavior. That is not exciting audio, but it is exactly the kind of maintenance that keeps a local gateway from aging into a brittle pile of transitive assumptions.

[NOVA]: Now Claude Code. The user-facing update is very practical. The `/usage` command can break down limits by category, including skills, subagents, plugins, and per-MCP-server cost. That is useful because agent work is no longer one neat model call. It is a bundle of tools, skills, servers, and background helpers. If usage is opaque, you cannot tune it.

[ALLOY]: `/diff` detail view gets keyboard scrolling, which is small but humane. If a terminal agent asks you to review a diff, navigation matters. Markdown output now renders GitHub-flavored task-list checkboxes, which helps when agents produce plans, review lists, and completion states. Enterprise admins get a managed setting for loading claude.ai cloud MCP connectors alongside managed MCP config. That gives teams a clearer policy knob instead of everyone improvising connector behavior.

[NOVA]: The fixes are the security story. PowerShell permission bypasses through built-in directory-changing functions are fixed. Sandbox write allowlists in git worktrees stop covering too much of the main repo root. PowerShell prefix and wildcard allow rules get repaired. Variable tracking around PWD, OLDPWD, and DIRSTACK gets corrected. A macOS `find` problem that could exhaust file tables on large directories gets fixed.

[ALLOY]: The lesson is simple: coding agents live in shells, and shells are weird. Permissions can fail through boring edges: a built-in command, a wildcard, a changed directory, a worktree boundary, a file table limit. A serious CLI agent needs these boring edges handled because that is where a safe-looking command turns into a permission surprise.

[NOVA]: The first action is not complicated. Update OpenClaw. Run the status and doctor paths. Check meeting-notes and live-source config. Test chat-session pagination. Try a long-lived Discord review control and make sure stale controls do not behave like fresh controls. In Claude Code, run usage, scroll through a diff, and test one shell-heavy task with the new permission behavior in mind.

[ALLOY]: Codex and Hermes do not have a newer stable release tag for this readout, but they stay in the stack conversation. Codex matters later in the episode because the remote and mobile supervision story is moving quickly. Hermes matters because the project lane includes tools that can connect through MCP, local agents, or codebase intelligence. This episode is not one tool worship. It is the surface area around the working stack. [PAUSE]

[NOVA]: A useful builder workflow here is a release-smoke task. Start with one harmless repo. Ask OpenClaw to start the agent task, have Claude Code inspect the diff or the shell behavior, and keep Codex or Hermes as the comparison path. The goal is not to prove every tool can do everything. The goal is to learn which tool gives the clearest evidence at each step.

[ALLOY]: The workflow should have a tiny success condition: one diagnostic passes, one session can be found again, one review control expires when it should, one usage report explains where cost or limits went, and one shell command stays inside its permission boundary. That is enough. If the stack cannot make a tiny task observable, it is not ready for a sprawling task.

[NOVA]: Another practical pattern is voice-to-action without write power. Capture a short voice note or meeting-note source, let the agent summarize the task, and require a human approval before any change. That tests the new meeting-notes lane without pretending speech input should automatically become code. The win condition is a clean summary, a traceable source, and a clear handoff into a normal coding path.

[ALLOY]: For the Claude Code side, use review-before-edit. Run usage so the session starts with visibility. Open a diff and navigate it with the keyboard. Ask the agent to explain the permission boundary before it runs a shell command. That turns the update from "new CLI features" into a daily operator pattern: know the cost, inspect the change, then approve the action.

## [10:00-17:00] Gemini 3.5 Flash and Gemini API Managed Agents

[NOVA]: Gemini 3.5 Flash is the model headline, but the more interesting story is managed agents. Google is pitching Gemini 3.5 Flash for agentic and coding work, with claims around Terminal-Bench, GDPval-AA, MCP Atlas, multimodal performance, speed, and long-horizon tasks. Those names matter because they point at tool-heavy work instead of pure chat.

[ALLOY]: A model can sound brilliant in a conversation and still struggle inside a long tool loop. Coding agents need to read context, pick tools, call them correctly, interpret errors, recover from bad observations, and keep going without turning the transcript into soup. That is why terminal and MCP-style benchmarks are more relevant than another generic "it writes nice answers" claim.

[NOVA]: The Gemini API Managed Agents story is more concrete. Developers can start an Antigravity-powered agent in an isolated, ephemeral Linux environment. The agent can reason, call tools, execute code, manage files, and browse. Follow-up calls can reuse the environment, so a session can continue instead of every request beginning from zero.

[ALLOY]: That session state detail is important. Stateless prompts are easy to scale, but serious agent work often needs continuity. A repo gets cloned. Dependencies get installed. A scratch file gets created. A browser state matters. A partial analysis should not vanish before the follow-up question. Managed environments make that state explicit.

[NOVA]: Google also says custom agents can be defined with instruction files, skills, and data in AGENTS.md and SKILL.md-style files. That is directly relevant to the way modern coding stacks are converging. The agent has a task, but it also has local rules, project conventions, and specialized instructions. The harness is becoming part of the product, not a hidden wrapper around the model.

[ALLOY]: The obvious comparison is local OpenClaw, Hermes, and Codex work. Local agents are close to your files, credentials, browser sessions, audio tools, and private context. Managed agents are easier to scale, easier to isolate, and easier to reset. Neither side wins every task. The decision is about where the risk and state should live.

[NOVA]: A managed sandbox is attractive for throwaway work: reproduce a bug in a clean environment, inspect a public repo, run a data transformation, browse public docs, or test a generated script. A local environment is better when the agent needs private credentials, local-only files, subscribed tools, or a machine-specific setup.

[ALLOY]: The action item is a comparison test. Give Gemini Managed Agents one safe public repo task. Give a local agent the same task. Do not judge only the final prose. Compare setup time, tool evidence, state continuity, error recovery, file changes, and how easy it was to stop or inspect the run.

[NOVA]: The larger signal is that agent infrastructure is now a platform feature. The model, the sandbox, the tool runner, the browsing path, the session state, and the custom instruction files are being sold together. That is good for capability and dangerous for lock-in. The more the environment matters, the more you need to know which environment your task actually ran in.

[ALLOY]: The practical rule is to keep secrets out of the first test. Use a task where failure is cheap. Then decide whether the managed path earns more responsibility. An agent platform should earn trust with boring evidence, not with a launch headline. [PAUSE]

[NOVA]: The builder workflow I would test is a sandbox duplicate of a local task. Choose a public repository, a public issue, or a synthetic data cleanup job. Run it through the managed Gemini agent, then run the same task through a local OpenClaw or Codex path. Compare the workflow, not just the answer. Which one set up faster? Which one exposed tool calls clearly? Which one recovered from an error? Which one made it easier to stop?

[ALLOY]: A second test is state continuation. Ask the managed agent to inspect a repo, create a plan, and stop before editing. Then follow up in the same session and ask it to run a narrow validation. If it remembers the environment and evidence without making you restate everything, the session model is doing useful work. If it forgets or over-assumes, keep it in the experiment lane.

[NOVA]: The approval path is the key comparison point. Local agents often inherit the machine's messy reality: shell history, local packages, browser state, and credentials. Managed agents inherit platform reality: sandbox defaults, tool lists, session retention, and provider policies. The stronger path is the one where the boundary is obvious before the first risky action.

## [17:00-24:00] Codex remote supervision, access tokens, and hybrid environments

[NOVA]: Codex is moving toward remote supervision. The new mobile and remote story matters because coding agents do not always need a smarter answer. Sometimes they need a human to approve one command, steer one branch, inspect one diff, or say "no, not that file" without being seated at the host machine.

[ALLOY]: Codex in the ChatGPT mobile app lets a user connect to active work running on a Mac or remote environment. The mobile view can show live project state, terminal output, screenshots, test results, and diffs. The human can approve commands and redirect the session. That changes long-running work because the agent is no longer trapped waiting for a desktop user to return.

[NOVA]: The mechanism to watch is secure relay state. The agent still runs near the workspace, but supervision can happen elsewhere. That is a better model than shipping every local secret to a remote chat session. The code, files, and tools can stay in the environment where they belong, while the approval surface moves to the human.

[ALLOY]: Remote SSH being generally available fits the same pattern. A coding agent does not have to be locked to one laptop. It can work where the repo and dependencies live: a remote development machine, a cloud box, a workstation, or a managed enterprise environment. The question becomes less "can the model write code?" and more "where is the right execution boundary?"

[NOVA]: Programmatic access tokens are another serious piece. Browser sessions and hand-entered auth are not enough for automation. Scoped tokens let non-interactive workflows identify themselves, run inside a defined boundary, and be revoked or rotated. If Codex is going to run in CI-like or remote environments, it needs identity that is not just "someone left a browser logged in."

[ALLOY]: Hooks matter because agents need checkpoints. A hook can scan prompts for secrets, run validators, block risky actions, or enforce local policy before a task moves forward. This is where agent systems start looking like software platforms. The model proposes or acts, but policy and validation sit around the action.

[NOVA]: The Dell partnership points at the enterprise version of this story: Codex inside hybrid and on-prem environments. That matters for organizations that cannot casually move source code or data into a public cloud workflow. It also matters for local builders because the architecture question is the same at a smaller scale. Where should the agent execute? Where are the credentials? Where are the logs? What gets approved remotely?

[ALLOY]: A good trial is small. Start a Codex task on a branch, inspect it from mobile, approve one harmless command, review the diff, and redirect one decision. The test is not whether Codex can do a heroic refactor. The test is whether supervision works when the human is not sitting in front of the same terminal.

[NOVA]: The second trial is automation identity. List which workflows currently depend on a logged-in browser, local keychain, or long-lived secret. Then ask whether a scoped token or hook would make the task safer. If the answer is yes, that is a candidate for remote or managed execution. If the answer is no, it may need to stay local and human-supervised.

[ALLOY]: The takeaway is that Codex is becoming less like a single terminal assistant and more like a supervised work system. Mobile review, remote hosts, tokens, hooks, and enterprise deployment all point in the same direction: coding agents that can keep working while the human checks in at decision points. [PAUSE]

[NOVA]: A practical Codex pattern is the commute review. Start a small branch from a desktop session. Let the agent run tests and prepare a diff. Then review from mobile only far enough to approve a safe command, reject a questionable change, and leave one steering instruction. If that feels clear, remote supervision is real. If it feels like poking a black box through a tiny screen, the review path needs more evidence before it becomes daily use.

[ALLOY]: Another pattern is token hygiene. Pick one automation that currently depends on a broad credential or a logged-in session. Redesign it around a scoped access token and a hook. The hook can reject prompts with secrets, enforce a repo boundary, or require validation before the agent moves forward. This is not busywork. It is how a coding agent becomes something you can operate instead of something you merely hope behaves.

[NOVA]: A hybrid pattern is different again. If the code must stay near private compute or on-prem data, the agent's environment should be close to that boundary. The human approval surface can travel, but the sensitive state should not wander casually. Codex moving into remote and hybrid environments is interesting because it separates supervision from execution without pretending location no longer matters.

## [24:00-32:00] Anthropic Stainless and Project Glasswing

[NOVA]: Anthropic acquiring Stainless is an agent-connectivity story. Stainless turns API specs into SDKs, CLIs, and MCP servers across languages. Anthropic says Stainless has generated official Anthropic SDKs since early in the Claude API. That is not wrapper trivia. It is the machinery that gives agents clean handles on real systems.

[ALLOY]: Agents need tools. Tools need interfaces. Interfaces need types, schemas, docs, auth, errors, retries, pagination, and compatibility. If every agent integration is a hand-written one-off, the stack becomes fragile. If API specs can generate usable SDKs, CLIs, and MCP servers, then more services can become safe tool surfaces.

[NOVA]: MCP is especially important here because it gives agents a standard way to discover and call tools. But a bad MCP server is still a bad tool. The generated surface needs good method names, safe defaults, clear permissions, useful error messages, and documentation that an agent can actually follow. Stainless being inside Anthropic makes the tool-generation path more central to the Claude ecosystem.

[ALLOY]: The action item for builders is to look at internal APIs differently. If an API has a clean OpenAPI spec, it may be closer to becoming an SDK, CLI, or MCP tool than it looks. If the spec is vague, stale, or missing, then the agent surface will inherit that mess. Better specs are not only for humans reading docs. They are for agents trying to act correctly.

[NOVA]: Project Glasswing is the other half of the story. Anthropic says Claude Mythos Preview has been used with partners across more than a thousand open-source projects and found a large number of high- and critical-severity vulnerabilities. The important part is not just the count. The bottleneck shifts from finding problems to verifying, disclosing, and patching them.

[ALLOY]: Security scanning with frontier models is powerful, but it can create operational pressure. A model may find a subtle issue. It may also produce false positives, partial evidence, or findings that require careful disclosure. If the process around the model is weak, the result can be noise, panic, or irresponsible release of exploit details.

[NOVA]: That means agent-assisted security work needs a narrow scope. Which repository is allowed? Which files are in scope? Are generated findings private? Who verifies them? How are maintainers contacted? What evidence is enough before a finding becomes a report? What repair path exists after confirmation?

[ALLOY]: This connects back to Stainless because connectivity and security are not separate worlds. The same clean tool surface that lets an agent act on systems also lets an agent inspect systems at scale. Better SDKs and MCP servers make agents more useful. They also increase the need for permissions, audit logs, and deliberate disclosure rules.

[NOVA]: The first practical step is internal. Pick one API that agents touch or should touch. Check whether it has a current spec, clear auth, and safe read-only methods. Then pick one security scanning target that is safe and small. Run the scan as an experiment, verify manually, and write down how the finding would be handled if it were real.

[ALLOY]: Do not start by turning a model loose on everything. Start by proving the pipeline: scope, scan, evidence, human verification, fix, and disclosure. A faster vulnerability finder is valuable only if the team can process what it finds. [PAUSE]

[NOVA]: The Stainless pattern is API-to-tool. Take one internal service and ask whether it has the ingredients an agent would need: a current spec, consistent errors, pagination rules, auth that can be scoped, and a safe read-only path. If the answer is no, the next builder step is not "add an agent." It is clean up the interface so an agent has something trustworthy to call.

[ALLOY]: For Glasswing, use a finding-to-fix loop. A security agent should not end at "I found something." It should produce a finding, cite evidence, suggest a minimal patch, and mark what still needs human verification. Then a reviewer decides whether the issue is real, whether disclosure is needed, and whether the fix belongs in a patch release. The model accelerates the search; the response loop protects the outcome.

[NOVA]: The connection between these stories is practical. SDKs, CLIs, and MCP servers make systems easier for agents to use. Security scanning makes those systems easier for agents to inspect. Both workflows need the same discipline: scope the action, log the evidence, verify the result, and avoid giving a model a broader surface than the task requires.

## [32:00-39:00] GitHub projects: codebase intelligence for Claude Code, Codex, and Hermes

[NOVA]: Now the GitHub projects. The first group is codebase intelligence, because a coding agent that cannot find the right code is just an expensive guesser. The names are Serena, Claude Context, Sourcebot, Understand-Anything, Chunkhound, and Code Review Graph. Full links are in the shownotes and YouTube description.

[ALLOY]: Serena is the most direct MCP-style upgrade in this group. It gives coding agents semantic retrieval, editing, refactoring, and debugging tools that behave more like IDE capabilities. The important phrase is symbol-level. Line search is useful, but codebases are made of definitions, references, types, call paths, and relationships. A tool that can navigate those relationships gives an agent a better map.

[NOVA]: The try-now path for Serena is a single refactor. Do not begin with "rewrite this app." Ask an agent to trace a symbol, find references, explain the dependency path, and plan the edit before it changes anything. If the plan is sharper than the same request with ordinary search, Serena earns more testing.

[ALLOY]: Claude Context is a semantic code-search MCP for Claude Code and other agents. The value proposition is straightforward: make the whole codebase searchable by meaning without stuffing the entire repo into context. That matters for large projects where the right files are scattered and the literal words in the prompt do not match the names in the code.

[NOVA]: Sourcebot is the self-hosted option to watch. It gives code search, navigation, file exploration, and natural-language questions grounded in code citations. This is useful because humans and agents can share the same evidence surface. Instead of the agent saying "I think the auth code is over there," it can point to navigable results.

[ALLOY]: Understand-Anything is more visual and exploratory. It turns codebases into interactive knowledge graphs with search and Q&A. That can help before a planning session, especially on unfamiliar repos. A graph does not replace reading code, but it can show the shape of a system before an agent starts cutting through it.

[NOVA]: Chunkhound and Code Review Graph are in the local-first code intelligence category. This matters for private code. If a project can build a persistent map locally, reduce context waste, and feed only relevant sections into an agent, it may improve both quality and cost. The best agent context is not always more context. Often it is less context, chosen better.

[ALLOY]: The comparison test is simple. Pick one real repo. Ask a coding agent to plan a change using only built-in search. Save the plan. Then give it one of these tools: Serena, Claude Context, Sourcebot, Understand-Anything, Chunkhound, or Code Review Graph. Ask for the same plan again. Compare file selection, assumptions, missed dependencies, and confidence.

[NOVA]: If the second plan touches fewer wrong files and asks better questions, that is a stack upgrade. If it does not, discard the tool or use it only for specific repo shapes. The goal is not to collect shiny project names. The goal is to improve agent accuracy before edits happen.

[ALLOY]: This is also where Hermes fits. Hermes, OpenClaw, Codex, Claude Code, and other harnesses become stronger when code intelligence is available through a standard tool layer. MCP-based or local-first code maps can sit below several agents instead of being trapped inside one chat product.

[NOVA]: The caution is setup cost. Some tools need indexing, embeddings, containers, or a service. That cost is fine if the repo is large or the work repeats. It is probably overkill for a one-file script. Use the smallest tool that gives the agent enough eyes. [PAUSE]

[ALLOY]: A good workflow for this group is the three-pass planning test. Pass one is blind: let the agent use its built-in tools. Pass two adds a semantic search tool like Serena or Claude Context. Pass three adds a human-readable map from Sourcebot, Understand-Anything, Chunkhound, or Code Review Graph. The winner is the workflow that produces a smaller, more correct plan with fewer guesses.

[NOVA]: The metrics can be simple. Count how many relevant modules the agent finds. Count how many irrelevant paths it wants to edit. Count whether it names a validation step. Count whether it can explain why the chosen code paths matter. You do not need a research lab for this. You need the same task run under different context workflows.

[ALLOY]: Another useful pattern is onboarding a repo. Before asking for a feature, ask the tool to build a map: main entry points, data paths, test paths, risk areas, and unknowns. Then hand that map to Claude Code, Codex, or Hermes and ask for a plan. This prevents the agent from spending the first ten minutes rediscovering architecture through fragile searches.

[NOVA]: For private code, local-first workflows matter. If the code should not leave the machine or trusted network, prioritize tools that index locally or can be self-hosted. Sourcebot, Chunkhound, and Code Review Graph are interesting for that reason. The question is not only "does it work?" It is "where does the index live, who can query it, and how do I delete or rebuild it?"

## [39:00-46:00] GitHub projects: model routing, MCP builders, local agents, and security scanners

[NOVA]: The second project group changes how the stack runs. The names are Context7, Claude Code Router, mcp-use, goose, gstack, deepsec, context-mode, and ai-setup. Full links are in the shownotes and YouTube description.

[ALLOY]: Context7 is about current documentation. Coding agents hallucinate APIs when their library memory is stale. Context7 gives agents a way to fetch up-to-date, version-specific docs through CLI skills or MCP. That is not glamorous, but stale library usage is one of the most common ways an agent produces code that looks plausible and fails immediately.

[NOVA]: A good Context7 test is a fast-moving library. Ask an agent to implement something version-specific. First, do it without current docs. Then require Context7. If the second answer avoids deprecated calls or wrong options, the value is obvious.

[ALLOY]: Claude Code Router is about model routing. It can route Claude Code requests across providers and models, with transformers and route-specific choices. The appeal is not "never use the main model." The appeal is choosing the right backend for the right class of work: cheap background tasks, long-context reads, local Ollama experiments, or high-reasoning reviews.

[NOVA]: The safe test is a low-risk background route. Route a summarization or repo-reading task, not a production edit. Compare quality, latency, logging, and whether the provider path is obvious. If you cannot tell which model handled the request, do not use the route for important work yet.

[ALLOY]: mcp-use is about building MCP servers and apps. It gives TypeScript and Python paths, inspection, and deployment options. The right first project is read-only. Build a small internal lookup tool, inspect every call, and only then consider write actions. MCP is powerful because it gives agents tools. That is also why the first tool should be boring and scoped.

[NOVA]: goose is the local agent comparison point. It has a desktop app, CLI, API, provider support, subscription and ACP paths, and MCP extensions. The useful question is whether goose can serve as a local fallback or a specialized harness for tasks that do not need the full OpenClaw setup. Test it with no write permissions first. Let it inspect, summarize, or gather evidence before giving it edit power.

[ALLOY]: gstack is a Claude Code role and workflow pack. It packages review, QA, release, security, planning, and product roles into slash-command style workflows. The risk with role packs is theater: many titles, little evidence. The test is a real branch. Run review or QA and see whether it finds concrete issues, not just polished advice.

[NOVA]: deepsec is the sharper security project. It uses coding agents for vulnerability scanning, with resumable scans, matchers, processing, revalidation, and export. It should not be treated casually. Start with a small repo or sample app. Inspect findings manually. Treat cost, scope, and false positives as part of the evaluation.

[ALLOY]: context-mode and ai-setup address a different pain: keeping agents from drowning in tool output and keeping multi-harness setups consistent. If you use Claude Code, Codex, OpenCode, Gemini CLI, Hermes, or OpenClaw together, configuration drift becomes real. A setup-sync tool can help if it makes the system more predictable. It hurts if it hides too much.

[NOVA]: The operating rule for this whole project group is one tool at a time. Pick one context tool and one operations tool. Test each on a harmless repo. Measure whether it reduces context waste, model lock-in, setup drift, or review pain. Keep the winners. Ignore the rest.

[ALLOY]: The worst outcome would be installing ten agent tools and making the stack harder to understand. The best outcome is boring: one semantic code map that improves planning, one docs tool that prevents API hallucinations, one router that makes cheap background work possible, and one MCP builder that turns a private read-only workflow into a clean tool. [PAUSE]

[NOVA]: Here is a practical stack workflow using these projects without turning the machine into a museum. Use Context7 when the task depends on a fast-moving library. Use Claude Code Router only for a low-risk class of work where provider choice is visible. Use mcp-use to build one read-only tool. Use goose as a comparison agent on a task with no write permission. Use gstack when you want a repeatable review, QA, release, or security role. Use deepsec only when you are ready to handle real security findings.

[ALLOY]: The approval workflow should be the same across all of them. Read-only first. Then narrow write action. Then validation. Then human review. If a project cannot explain what it called, what changed, what provider answered, or what evidence supports the result, it should not get more authority. Agent tools are useful when they make the workflow more legible.

[NOVA]: Model routing deserves extra care. A router can save money and latency, but it can also blur accountability. The workflow needs a visible route decision: background summary went to one provider, high-stakes code review went to another, local-only task stayed local. Without that visibility, model routing becomes another source of confusion.

[ALLOY]: MCP builders deserve the same caution. The fastest way to make an agent powerful is to expose a tool. The fastest way to make an agent dangerous is to expose a tool too broadly. A good MCP workflow starts with a small read-only method, clear input schema, narrow output, and a log line that a human can understand. Then it grows only after the boring version works.

## [46:00-50:00] Close

[NOVA]: The queue from this episode is direct. Update OpenClaw. Read the Claude Code changelog. Test usage accounting, diff navigation, shell permissions, and sandbox behavior. Try Gemini Managed Agents only on a safe sandbox task. Test Codex remote supervision on a small branch. Watch Anthropic's Stainless and Glasswing work because tool generation and AI security scanning are converging.

[ALLOY]: Then choose projects by job, not hype. For codebase intelligence, start with Serena, Claude Context, Sourcebot, Understand-Anything, Chunkhound, or Code Review Graph. For stack operation, test Context7, Claude Code Router, mcp-use, goose, gstack, deepsec, context-mode, or ai-setup. Again, the full links are in the shownotes and YouTube description.

[NOVA]: The practical test is whether a tool changes an outcome. Did the agent find the right files faster? Did it stop hallucinating library APIs? Did it route cheap work without hiding the provider? Did the MCP tool stay scoped and auditable? Did the security scanner produce verifiable findings instead of noise?

[ALLOY]: If the answer is yes, keep it. If the answer is no, skip it. Agent stacks are already complicated enough. A project earns its place when it makes the model, the repo, the tools, or the human approval loop clearer.

[NOVA]: There is also a cleanup rhythm here. After each test, write down three facts: what the tool did better than the default path, what it made harder, and what authority it needed. A docs tool that only reads public docs is low-risk. A router that sends code to another provider needs visibility. A security scanner needs scope. An MCP server needs a permission model. A local agent needs a boundary around writes.

[ALLOY]: That rhythm keeps the stack from becoming a pile of exciting names. Every project gets one job, one test, and one decision. Promote it only when the result is clear. The goal is not to have the most tools. The goal is to have a smaller number of tools that make agent work faster to verify and easier to reverse.

[NOVA]: That is the version of AI news that is actually useful: fewer mystery boxes, more evidence, and better control over where the agent acts.

[ALLOY]: The safest sequence is update, observe, compare, and then adopt. Update the core tools first. Observe one task with the new diagnostics. Compare one managed agent against one local agent. Compare one code-intelligence workflow against built-in search. Compare one model-routing workflow against the default path. Adopt only the piece that wins a real test.

[ALLOY]: That makes the episode practical rather than decorative. The release block tells you what changed in OpenClaw and Claude Code. The AI-news block tells you where Google, OpenAI, and Anthropic are moving agent infrastructure. The project block gives you names to test, not a demand to install everything.

[NOVA]: Full source links are in the shownotes and YouTube description. Thanks for listening to AgentStack Daily.

[ALLOY]: We'll be back soon. [PAUSE]
