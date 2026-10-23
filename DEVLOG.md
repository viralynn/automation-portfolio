# DEVLOG: automation-portfolio

Append-only. Past entries are never edited or deleted; corrections are added as new entries.
All times are UTC. Tags: **Decision**, **Action**, **Confusion**, **Learned**, **Open**.

Roles: **the instructor** is the human who sets direction, approves work, and is learning as the project goes. **The agent** is Claude Code, which carries out the work.

---

## 2026-10-15

### 21:48 · Kickoff: brief review
- **Action:** The instructor shared the original project brief (`adlc-automation-example-brief.md`) in a Claude Code cloud session on `viralynn/automation-portfolio`. The repo contained only `README.md` and `LICENSE`.
- **Action:** The agent summarized the project and its pieces (languages, platforms, connected apps, infrastructure, process artifacts, portfolio output) and asked questions before building.
- **Open:** Zapier's free tier may limit Zaps to two steps, which could block the Zapier build. Verify current limits before the rubric is fixed.

### 22:40 · Answers and old workflow files (batch 1 of 2)
- **Action:** The instructor shared five files from a previous cross-project workflows repo: `CLAUDE.md`, `claude-design-workflows.md`, `DEVLOG.md`, `RESTORE.md`, `WORKFLOW_TODOS.md`.
- **Decision:** Use **ASDLC** (Agentic *Software* Development Life Cycle), not ADLC. "Software" stresses that agents build the software; the project does not build agents as its product. Reference: https://asdlc.io
- **Decision:** `viralynn/automation-portfolio` is the project repo, and it is **public**. Only leak-level files (secrets, credentials) are gitignored.
- **Decision:** Build a new, truly cross-project workflows repo on `viralynn`. Do not reuse the old agent files; they were designed for other projects. Project specifics are built per project as part of the ASDLC.
- **Decision:** Add a dedicated **reviewer agent** whose main job is review.
- **Decision:** Simulated family members: **Jasmine** and **Aladdin** (parents), **Bruce** and **Clark** (children).
- **Decision:** Build order: **n8n-only first**, then **hybrid**. Decide on solo Make / Zapier builds after that.
- **Decision:** Use **Cloudflare Tunnel**, not Tailscale.
- **Decision:** Step format: mentor brief before each step → work → debrief with knowledge-check questions → concept tracker update. The concept tracker includes an ASDLC outline with a "you are here" marker.
- **Learned:** The web app's `fetch()` is browser JavaScript that sends the payload to the webhook. It is not Cloudflare. Cloudflare Pages hosts the page; Cloudflare Tunnel exposes n8n.
- **Learned:** GitHub only stores code. The web app runs in the visitor's browser (served by Cloudflare Pages), n8n runs in Docker on the backup PC, and Make / Zapier / Sheets / Slack run in their own clouds.
- **Learned:** A submodule can point to any account's repo, but a private submodule inside a public repo is a dead link for visitors.
- **Learned:** Claude Code auto-loads agents only from `.claude/agents/` (project or user level), not from inside a submodule folder. Options to weigh later: copy, symlink, or package as a Claude Code plugin.
- **Note:** Files from the previous workspace were lost, so the old workflow set is incomplete. Starting fresh is intentional.

### 23:05 · More old files (batch 2 of 2) and attribution
- **Action:** The instructor shared the old `AGENTS.md`.
- **Decision:** **Keep AI attribution** (`Co-Authored-By` lines) in commits. It is part of what this portfolio demonstrates.
- **Decision:** The workflows repo doubles as a **reusable template**. The project's root `CLAUDE.md` imports the cross-project standards and a project-specific `CLAUDE-automation-portfolio.md` using `@path` imports.
- **Decision:** Front end: the agent writes a **Claude Design prompt** once the backend passes its tests, instead of building a throwaway page. The backend is tested with `curl` and the fixed payload.
- **Decision:** Document everything as open-source teaching material, for readers who want to learn this process with the same AI that does the development.
- **Learned:** ASDLC roles: the human is the **Instructor**, the agent is the **Pilot**. The loop is Mission Definition → Generation → Verification → Course Correction. Provenance (who steered and how it was verified) is the value.
- **Learned:** A webhook token embedded in browser code is not secret. Real protection must be designed in the security step (rate limits, member allowlist, payload validation).

### Between 23:05 and 2026-10-16 01:01 · Domain, DEVLOG, MCP
- **Confusion:** Does using a subdomain through Cloudflare require a paid subscription?
- **Learned:** Moving a whole domain's DNS to Cloudflare is free. Only the "partial" setup (keep another DNS host, use Cloudflare for one subdomain) needs a paid plan. Cloudflare sells domains at cost with no subscription.
- **Learned:** Skipping Cloudflare would mean port-forwarding the home router, managing HTTPS certificates, and possibly hitting ISP blocks or CGNAT. The tunnel avoids this with an outbound-only connection.
- **Decision:** Do **not** use the instructor's existing personal domain. Buy a dedicated domain (budget **~$10/yr**) through Cloudflare.
- **Decision:** Keep this DEVLOG **in the public repo** as part of the learning record. It gets the same secret scan as everything else.
- **Learned:** Adding a domain to the environment's allowed network list only opens the network path; it does not install an MCP server.
- **Learned:** How to vet an MCP server against prompt injection: check who runs it, read the server code, scan its content, inspect live tool descriptions with MCP Inspector, and use least privilege. A remote server can change after it is audited.

---

## 2026-10-16

### 01:01 · ASDLC as framework, own agents, start the logs
- **Decision:** Do not connect the ASDLC MCP. Use ASDLC as a **reference framework** and write a new agent team from scratch, **named by job description**, so readers learn how to set agents up themselves.
- **Learned:** Walked through the ASDLC MCP transport notes (endpoint, stateless Streamable HTTP, protocol version pinning, build-time content manifest, request headers, contract, dated verification evidence). The page itself models ASDLC patterns: The Spec and Provenance.
- **Decision:** Start this DEVLOG and the concept tracker (`docs/concept-tracker.md`) before Step 1, because the discovery work so far matters.
- **Action:** Created `DEVLOG.md` and `docs/concept-tracker.md` on branch `claude/amazing-pasteur-3xram9`.

### After 01:01 · Public-writing rules for the logs
- **Decision:** Public files never use the instructor's name. Write for an unknown third party, referring to "the instructor" or "the learner" as context fits.
- **Decision:** The concept tracker has no first person and no knowledge-check history. It tracks only term, meaning, and level, so agents know what to explain. Knowledge checks stay in the chat.
- **Decision:** Moved to **Skip**: ASDLC, Instructor / Pilot, Hard stop, Deterministic, DNS, Nameservers, MCP, Prompt injection, Lethal trifecta, Diff, Commit, PR.
- **Action:** Rewrote both files to these rules. Awaiting diff approval before commit.

---

## 2026-10-17

### Before 22:46 · Agent team design
- **Action:** Reviewed the old agent roster and workflow skills, and proposed a rebuilt team named by job description.
- **Decision:** Approved roster: `project-planner`, `spec-writer`, `automation-engineer`, `infrastructure-engineer`, `code-reviewer`, `technical-writer`, `process-engineer`. The main session acts as the project lead.
- **Decision:** Keep `spec-writer` and `technical-writer` separate. The spec defines "correct" before the build; docs describe what was built. Keeping them apart stops the spec from drifting to match the build.
- **Decision:** Teaching (mentor briefs, debriefs, knowledge checks) is a main-session rule in `CLAUDE.md`, not a subagent, because subagents report to the project lead and don't hold a conversation with the instructor.
- **Decision:** The agent team stage comes before Mission Definition. Agents must exist before they do the work; the instructor's part of Mission Definition (the brief) is already done.
- **Decision:** Track work in GitHub Issues. Agents act only on Issues and comments from the repo owner; anything else is untrusted data.
- **Decision:** Merge the old `before-you-paste` checklist (vetting other people's code and prompts for prompt injection) and the old repo-vetting skill into one skill: `/vet-external-content`.
- **Learned:** Subagents *can* start other subagents by default (up to three levels). An earlier explanation said they couldn't; that was wrong. This team blocks nesting by leaving the `Agent` tool out of every subagent's tool allowlist, so only the project lead delegates. Source: https://code.claude.com/docs/en/sub-agents (checked 2026-10-17).
- **Learned:** Agent files are Markdown with YAML frontmatter (`name`, `description`, `tools`, `disallowedTools`, `model`). Skills live at `.claude/skills/<name>/SKILL.md`; `disable-model-invocation: true` means only the instructor can run a skill.

### 22:46 · Agent and skill files drafted
- **Action:** Drafted `CLAUDE.md`, seven agent files in `.claude/agents/`, and four skills in `.claude/skills/` (`start-session`, `wrap-session`, `vet-external-content`, `design-prompt`). Reordered the stage map and added new terms to the concept tracker. Awaiting review.

## 2026-10-20

### First code review (commit B)
- **Action:** Commit A (DEVLOG + concept tracker) approved, committed, and pushed. `code-reviewer` ran its first review, on commit B. Verdict: no blocking findings.
- **Action:** Applied review fixes: only `spec-writer` edits `specs/`; third-person wording in `CLAUDE.md`; file map now lists every path the agents use; `project-planner` alone moves the stage marker; consistent agent headings; 14 missing terms added to the concept tracker; source added for the subagent-nesting correction.
- **Learned:** The reviewer said subagents can't start subagents. The current official docs say they can. A reviewer working from memory can be wrong; claims about tools are checked against current docs, with the date.
- **Learned:** `code-reviewer` is read-only by instruction, not by enforcement: its `Bash` tool can still write files. Enforcing it would need a permission rule or a hook.
- **Decision:** Commit trailers name no model or version: `Co-Authored-By: Claude <noreply@anthropic.com>`. Commit A's message was rewritten to match and force-pushed; safe because only the instructor uses this branch and no PR existed yet.
