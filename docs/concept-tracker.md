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
| 1 | Mission Definition: updated brief, success metrics, payload contract, rubric, test cases | 📍 **Current** |
| 2 | Agent team + workflows repo: agents named by job, cross-project standards, templates | ⬜ |
| 3 | Infrastructure: domain, Docker, n8n, Cloudflare Tunnel, Google + Slack credentials | ⬜ |
| 4 | Build 1: n8n-only (intake + master report) | ⬜ |
| 5 | Verification + release: test cases, webhook security, test → production | ⬜ |
| 6 | Front end: Claude Design prompt and handoff | ⬜ |
| 7 | Build 2: hybrid (n8n + Make + Zapier) | ⬜ |
| 8 | Operate + monitor: execution logs, free-tier usage, drift | ⬜ |
| 9 | Decide: solo Make / Zapier builds, verdict | ⬜ |

*Stages 2–9 are a draft order, to be confirmed at the Step 1 plan approval.*

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
