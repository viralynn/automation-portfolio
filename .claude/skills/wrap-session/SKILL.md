---
name: wrap-session
description: Close a work session or step - debrief the instructor, run a knowledge check in chat, update the DEVLOG and stage map, and leave nothing only in the container.
disable-model-invocation: true
---

# /wrap-session

Run these in order.

## 1. Debrief (chat)
- **What we did:** a short list of what changed and why
- **What it means:** how this step moved the project through the ASDLC
- **What to watch:** risks, OPEN items, and what comes next

Use concept-tracker levels for every term.

## 2. Knowledge check (chat only)
Ask 3–5 questions about this step's concepts: a mix of "what is", "why did we", and "what would happen if". Wait for the instructor's answers and notes. Give feedback on each answer. Never write questions or answers to any file.

## 3. Concept tracker
- Ask whether any term should change level, based on the answers. Change a level only when the instructor says so.
- Add any new terms from this step at **teach fully**.
- If the stage changed, have `project-planner` move the 📍 marker.

## 4. DEVLOG
Have `technical-writer` append dated UTC entries for this session's decisions, actions, confusions, learnings, and open items. Append only.

## 5. Loose ends
- Ask `process-engineer` whether anything this step should change an agent, skill, or rule. List proposals; don't apply them.
- Check for uncommitted changes, branches without PRs, and open PRs. Nothing important should exist only in this container.
- Every resulting commit still goes through the diff-approval hard stop.
