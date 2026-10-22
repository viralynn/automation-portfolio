---
name: design-prompt
description: Write the Claude Design prompt for the habit-tracker front end, once the backend passes its tests. Produces a prompt the instructor pastes into Claude Design, so no throwaway front end is built.
disable-model-invocation: true
---

# /design-prompt

Use only after the backend passes its test cases. The front end is designed in Claude Design and handed back to Claude Code.

## 1. Gather the contract
Read:
- `specs/payload.schema.json`: the exact JSON the page must send
- `specs/test-cases.md`: behaviors the page must support (success, error, retry)
- `docs/project-brief.md`: members, tasks, the "Refresh report" button, audience

## 2. Write the prompt
Save it to `docs/design/claude-design-prompt.md`. Front-load everything in one dense opening paragraph, then add details. Cover:

- **Goal:** what the page does and why
- **Layout:** member picker, task list, "Refresh report" button, status messages
- **Content:** the four members and their tasks; what each click shows (sending, done, failed)
- **Audience:** a family on phones and a tablet; large tap targets, readable at a glance
- **Behavior contract:** on click, send exactly the payload in the schema to a webhook URL read from one config value, never hard-coded. Show success or failure from the response.
- **Constraints:** a static site for Cloudflare Pages; accessible (keyboard, contrast, labels); no secrets in the page
- **Aesthetic:** a named cultural aesthetic chosen with the instructor, plus explicit bans on generic AI defaults: overused fonts (Inter, Roboto), purple gradients, predictable SaaS card grids, and warm editorial defaults (cream, serif, terracotta)
- **Variants:** ask for three versions: one bold, one restrained, one experimental

## 3. Review
Show the prompt in chat. The instructor edits and approves it before using it in Claude Design. Then record the decision in `DEVLOG.md`.
