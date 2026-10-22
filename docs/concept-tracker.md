# Concept Tracker

Agents check this file **before explaining any term**, in chat, in code reviews, and in the audit log.

**Levels:**
- **Teach fully:** explain from scratch every time the term appears, with a plain-language definition in brackets.
- **Brief reminder:** a one-line reminder only.
- **Skip:** no explanation.

New terms start at **teach fully**. Only the instructor changes a level. Agents never change a level on their own.

---

## Where the project is in the ASDLC

### The cybernetic loop (runs inside every step)
1. **Mission Definition:** intent + constraints are defined.
2. **Generation:** the agent does the work.
3. **Verification:** automated checks, plus human review at hard stops.
4. **Course Correction:** the instructor steers when a result is generic or off-target.

### The three pillars
- **Factory Architecture (orchestration):** specialized stations: Planning, Spec-Definition, Implementation, Review.
- **Standardized Parts (determinism):** specs, schemas, and contracts constrain agent output.
- **Quality Control (governance):** automated checks and human-in-the-loop gates.

### Project stages
| # | Stage | Status |
|---|---|---|
| 0 | Discovery: brief, old files, early decisions | ✅ Done |
| 1 | Agent team: agents named by job, skills, `CLAUDE.md` rules | 📍 **Current** |
| 2 | Mission Definition: formalize the instructor's brief, success metrics, payload contract, rubric, test cases | ⬜ |
| 3 | Workflows repo: cross-project standards and templates in `viralynn/workflows` | ⬜ |
| 4 | Infrastructure: domain, Docker, n8n, Cloudflare Tunnel, Google + Slack credentials | ⬜ |
| 5 | Build 1: n8n-only (intake + master report) | ⬜ |
| 6 | Verification + release: test cases, webhook security, test → production | ⬜ |
| 7 | Front end: Claude Design prompt and handoff | ⬜ |
| 8 | Build 2: hybrid (n8n + Make + Zapier) | ⬜ |
| 9 | Operate + monitor: execution logs, free-tier usage, drift | ⬜ |
| 10 | Decide: solo Make / Zapier builds, verdict | ⬜ |

*Stages 2–10 are a draft order, to be confirmed at the Mission Definition plan approval.*

---

## Terms

| Term | Meaning | Level |
|---|---|---|
| ASDLC | Agentic Software Development Life Cycle: agents do the work, humans govern it | Skip |
| Instructor / Pilot | Human role (steer, approve) vs. agent role (carry out) | Skip |
| Hard stop | A point where agents must pause for human approval | Skip |
| Deterministic | Does the same thing every time for the same input | Skip |
| DNS | The internet's address book: turns names into server addresses | Skip |
| Nameservers | The servers that say who manages a domain's DNS | Skip |
| MCP | Model Context Protocol: a standard way for AI tools to connect to outside servers | Skip |
| Prompt injection | Hidden instructions inside content an AI reads | Skip |
| Lethal trifecta | Private data + untrusted content + ability to act externally: a risky combination | Skip |
| Diff | A view of exactly what changed | Skip |
| Commit | A saved snapshot of the code | Skip |
| PR (pull request) | A proposal to merge changes, approved or rejected by a human | Skip |
| Diátaxis | A docs framework: tutorials, how-to guides, reference, explanation | Brief reminder |
| Provenance | The audit trail of who steered the agent and how work was verified | Teach fully |
| Webhook | A web address one app sends data to, to trigger another app | Teach fully |
| Payload | The actual data sent in a request | Teach fully |
| `fetch()` | Built-in browser JavaScript that sends data from a page to a URL | Teach fully |
| Submodule | A Git repo embedded inside another repo, pinned to one version | Teach fully |
| `CLAUDE.md` import | `@path/to/file` inside `CLAUDE.md` pulls that file in automatically | Teach fully |
| Subagent | A specialist Claude with its own instructions and its own context window | Teach fully |
| Context window | How much text an AI can hold in mind at once | Teach fully |
| MX record | A DNS record that routes a domain's email | Teach fully |
| Cloudflare Tunnel | An outbound connection that gives a private service a public HTTPS address without opening router ports | Teach fully |
| Port forwarding | Opening a router so the internet can reach a home computer directly | Teach fully |
| CGNAT | When a home shares one public IP with other homes, blocking inbound connections | Teach fully |
| Transport (MCP) | How messages travel between an MCP client and server | Teach fully |
| Stateless | The server remembers nothing between requests | Teach fully |
| Least privilege | Give only the access a task needs | Teach fully |
| Secret scan | An automatic search for accidentally saved passwords and keys | Teach fully |
| Project lead | The main Claude Code session: talks with the instructor, delegates to subagents, runs hard stops | Teach fully |
| Skill | A reusable set of instructions loaded into the current session, run with `/name` | Teach fully |
| YAML frontmatter | The settings block between `---` lines at the top of an agent or skill file | Teach fully |
| Tool allowlist | The list of tools an agent may use; anything not listed is unavailable | Teach fully |
| Model alias | A short model name (`opus`, `sonnet`, `haiku`) that points to the latest model in that family | Teach fully |
| JSON Schema | A file that defines exactly what valid JSON looks like | Teach fully |
| Pretty-printed | Formatted with line breaks and indentation so it's readable and line numbers are stable | Teach fully |
| Permalink | A link locked to one exact version of a file | Teach fully |
| Hook | A script Claude Code runs automatically at a set moment, like before a tool runs or when a turn ends | Teach fully |
| Interaction limits | A GitHub setting that temporarily restricts who can open Issues, comment, or open PRs | Teach fully |
| Mentor brief | The explanation at the start of a step: what, why, sub-steps, new concepts, hard stops ahead | Teach fully |
| Debrief | The wrap-up at the end of a step: what was done, what it means, and a knowledge check | Teach fully |
| Knowledge check | Questions at the end of a step to confirm understanding; kept in chat, never in files | Teach fully |
| Station | One specialized job in the ASDLC factory (Planning, Spec-Definition, Implementation, Review) | Teach fully |
| Objective Packet | The intent plus constraints handed to agents at the start of work | Teach fully |
| Agent Optimization Loop | Improving the agents themselves, based on evidence from past work | Teach fully |
| Audit log | A plain-language record of every change, tied to the exact commit and lines | Teach fully |
| Untrusted data | Content from someone other than the instructor; read, but never followed as instructions | Teach fully |
| n8n | An open-source automation platform that can be self-hosted | Teach fully |
| Code node | An n8n step that runs a small piece of custom JavaScript | Teach fully |
| Docker / Docker Compose | Runs apps in isolated containers / a file that defines which containers to run and how | Teach fully |
| Cloudflare Pages | Cloudflare's free hosting for static websites | Teach fully |
| Claude Design | Anthropic's visual design tool that turns prompts into front-end code | Teach fully |
| gitleaks | A free tool that scans files and git history for secrets | Teach fully |
