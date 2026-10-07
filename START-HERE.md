# Guided build interview

**Audience:** A parent using a coding assistant to plan a child-facing OpenClaw service.

**Action:** Copy the prompt below into a new coding task. Answer its questions, review its proposed plan, and approve implementation only when the plan matches your family and machine.

```text
I want to plan a small child-facing assistant using a separate OpenClaw profile. First read the reference specification at https://github.com/chearmstrong/moreen-blueprint/blob/main/SPEC.md and briefly name its main safety and isolation boundaries to show you could access it. If you cannot, ask me to provide the file before continuing; do not guess what it says. Then inspect the existing installation read-only. Do not change files, start services, install packages, expose a port, or publish anything during this interview.

Interview me in short groups. Ask only for information that changes the design, and do not ask me to paste passwords, tokens, API keys, a child's full name, or chat transcripts. Cover:

1. The child's approximate age, region, school context if relevant, and whether more than one child will use it.
2. What the assistant should help with, and what needs an offline parent conversation.
3. How the parent will review ordinary requests and chats, who can access the parent area, and how long data should be kept. Do not ask me to name a safe adult. Plan a visible, region-appropriate help option for the child. Detected safeguarding disclosures must not enter the parent queue or ordinary transcript; explain that the host operator may still see data passing through the machine.
4. The assistant's display name, character, colours, tone, help style and interests. Offer the optional default mascot at https://github.com/chearmstrong/moreen-blueprint/blob/main/assets/default-mascot.png, a custom image, or no image, and ask which I prefer. If I choose an image, plan to copy it into the child app's local assets rather than load it from GitHub at runtime. Keep all personalisation separate from the safety policy.
5. The host and child devices, local-network access, HTTPS plan, and whether the service must work beyond the home network. Treat remote access as a separate design decision; never propose exposing the OpenClaw gateway directly.
6. Which model-provider accounts I already have, any model preference, a spending limit, and what should happen when the limit is reached. Check current model availability and pricing before recommending one pinned model; explain its estimated cost, how spending will be monitored or stopped, and separate authentication before asking me to decide. Do not present an alert as a hard spending cap. Do not ask me to paste credentials or assume the adult profile's access transfers.
7. Whether text search, image search or parent-approved teaching notes are wanted. Read the optional Agent Skills and installation sections at https://github.com/chearmstrong/moreen-blueprint/blob/main/README.md, briefly explain the four choices, and ask which, if any, I want installed as part of the initial child setup. If you cannot read those sections, ask me to provide them. Do not install a skill during this interview. Plan to review each selected skill at a recorded commit and compare its complete installed folder with that commit. For factual text search, consider the optional server-side `safe_search` pattern in SPEC.md; installing the research skill does not provide search. Explain each extra capability and its boundary before recommending it.

Use reasonable defaults for minor choices, but ask about choices that affect privacy, cost, external access or safety. Check the installed OpenClaw version and current documentation before giving version-specific commands.

Then produce a reviewable plan with: a plain-English summary; decisions and open questions; a diagram or list of the components and their network boundaries; separate paths and service names; model and effective tool policy; spending estimate and limit behaviour; selected skills, the reviewed commit for each, where they would be installed and how their complete folders and tool boundaries would be checked; request, reply and search policy; data/context limits; parent flow and the fixed safeguarding response, including a help option outside the app and no parent queue or ordinary transcript for disclosures; HTTPS setup; tests and parent acceptance checks before child use; deployment steps; and a rollback plan. Include a table of each data store (app chats, requests, notes, logs, OpenClaw sessions and archives), its retention period, deletion method and how removal will be verified. If more than one child will use it, show how their accounts and chats stay separate. Label what you verified, what you inferred and what remains untested. Include no real secrets or child-identifying information in the plan.

Do not implement until I explicitly ask you to proceed with the reviewed plan. Never claim the result is guaranteed child-safe.
```

This prompt is a planning aid. The builder must still inspect the target machine, implement the policy in code, test the effective runtime boundaries and review the result with the parent.
