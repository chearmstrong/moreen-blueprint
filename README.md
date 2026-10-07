# Build an AI assistant for children with OpenClaw

**Audience:** Parents and builders who want an assistant designed for children, with guard rails they can inspect and test.

Children can use the resulting app directly to ask questions, work through school topics, research a project or talk through an everyday problem. Parents set the boundaries and can review ordinary chats. This blueprint helps you and a coding assistant plan that child-focused experience around a separate OpenClaw profile, with clear limits on access, tools, search and stored conversations.

The finished assistant has its own child-facing web app, with separate child and parent areas. OpenClaw runs behind that app as the AI backend: the browser talks to the web app, and the web app talks to the child-only OpenClaw gateway on the server. Children do not use OpenClaw’s interface or connect to its gateway directly.

This repository contains a [guided interview](START-HERE.md), a [reference specification](SPEC.md), optional response skills and a default mascot. The interview helps a coding assistant inspect your machine, ask for family choices and produce a plan you can review. The builder can then implement and test that plan. **This is a starting point, not a working app or installer.**

## What it helps build

The intended setup has:

- A child-facing web app for separate chats, with a protected parent area for reviewing ordinary chats and requests.
- A dedicated OpenClaw profile and gateway with separate configuration, state, workspace, credentials and logs. The gateway listens only on the host machine; the web app is the part available to approved devices.
- A testable policy check before model or search calls, one chosen model, restricted tools and bounded conversation context.
- Optional, server-controlled search and small parent-approved teaching notes, if the family chooses them.
- Optional Agent Skills that guide explanations, everyday advice, school research and beginner Japanese. Skills guide replies; they do not enforce the app's safety rules.

These are design requirements for a future build, not claims about a running service.

## Start a build plan

1. Open [the guided interview](START-HERE.md) and copy the prompt inside its code block into a new task with your coding assistant. The prompt links directly to [the specification](SPEC.md).
2. Check that the assistant briefly names the main boundaries from the specification before it starts the interview. If it cannot open the link, give it the `SPEC.md` file or a local copy of this repository. You do not need to clone the repository when the link works.
3. Answer the assistant's questions, then review its plan for your family and machine. Ask it to implement only after you are happy with that plan.
4. Before your child uses the finished app, ask the builder to demonstrate the [minimum checks](SPEC.md#minimum-verification-before-child-use) on your child's device. Keep child access closed until these pass, including child and parent sign-in, HTTPS trust, blocked tools, search controls, the fixed safeguarding response and the visible help option.

A model prompt or Agent Skill cannot enforce access controls. The builder must implement and test the boundaries in the web app and OpenClaw configuration. This blueprint is not a child-safety certification.

**Chat visibility:** A parent can read ordinary chats. Detected safeguarding disclosures must not enter the parent queue or ordinary transcript; the app should give a fixed help response and point the child to an adult outside the situation or an independent support service. A visible help option remains available because detection can miss a disclosure; ordinary chats remain parent-readable. Someone who runs the machine may also see data passing through it, so do not promise secrecy. See the [access rules](SPEC.md#isolation-and-access).

## Optional default mascot

<img src="assets/default-mascot.png" alt="Friendly robot mascot with a star antenna" width="180">

The [default mascot](assets/default-mascot.png) is an original, optional starting image for the assistant's avatar. The guided interview offers it alongside a custom image or no image. If chosen, copy the image into the child app's local assets; do not load it from GitHub in the running app. Its appearance is personalisation only; it must not change the safety policy or tool permissions.

## Optional Agent Skills

An [Agent Skill](https://agentskills.io/specification) is a folder of instructions (`SKILL.md`) and optional reference files that a compatible agent can read when a relevant request arises. These four skills guide *how the agent responds*.

The [guided build interview](START-HERE.md) asks which, if any, to include in the initial child setup; it puts installation and checks in the plan, but does not install anything during the interview. Each skill can also be installed on its own in another compatible agent project without building this web app.

| Skill | Use it when a child… | What it guides |
| --- | --- | --- |
| [England Year 5 learning](skills/england-year5-learning/SKILL.md) | Is stuck on maths, reading, writing, science, history or geography at roughly England Year 5 level. | Start from the child's attempt, use a purposeful diagram or smaller example, then check understanding without rushing ahead. |
| [Everyday advice for children](skills/child-everyday-advice/SKILL.md) | Wants help with an ordinary friendship or feelings question. | Listen, avoid guessing motives, offer a small choice or words to try, and direct worrying situations towards a safe adult. |
| [School research](skills/child-school-research/SKILL.md) | Has a project to investigate or needs help checking a source. | Break the task into questions, distinguish checked evidence from suggested sources, and help the child make their own notes. |
| [Beginner Japanese for children](skills/beginner-japanese-for-children/SKILL.md) | Wants a simple phrase, kana reading or short practice exchange. | Give a small, contextual answer and gentle practice using checked starter references; it cannot assess speech. |

The `references/` files provide supporting material when needed, so keep the whole skill folder together. [The skill review](SKILL-REVIEW.md) records the instruction-design assessment; it is not a safety certification.

### Install one skill

Choose only the skills relevant to your agent. Review each `SKILL.md` and its `references/` files at a specific repository commit and note its SHA. After installation, compare the complete installed skill folder with that reviewed commit before using it; the `main` branch can change between review and installation.

**With `npx skills` (Codex example):** Run this from your project directory, replacing the skill name if needed. Choose project scope if prompted:

```sh
npx skills add chearmstrong/moreen-blueprint --skill child-school-research --agent codex
```

**With your coding agent:** Give it the link to the chosen skill directory and ask:

> Install only this Agent Skill in this project using your supported skill installer: https://github.com/chearmstrong/moreen-blueprint/tree/main/skills/child-school-research. Read its `SKILL.md` and references at a recorded commit first. Compare every installed file with that commit and tell me where you put them; stop if they differ. Do not install it globally or change tool permissions.

Installing a skill provides guidance for responses. It does **not** provide the web app's safety controls, parent review, search restrictions or memory limits. A child-facing host must implement and test those boundaries separately.

## Sources

- [OpenClaw: multiple gateways and isolation](https://docs.openclaw.ai/gateway/multiple-gateways)
- [OpenClaw: tool permissions](https://docs.openclaw.ai/gateway/security/tool-permissions)
- [Agent Skills specification](https://agentskills.io/specification)

## Licence

This repository’s original specification, prompt, skill text, examples and default mascot are available under the [MIT licence](LICENSE). Linked third-party material remains subject to its own terms. The private prototype app, child data, credentials and artwork are not included.
