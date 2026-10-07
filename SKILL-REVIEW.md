# Standalone skill review

**Audience:** The repository maintainer and parents considering these optional skills.

**Decision:** The four local copies pass the skill-judge **instruction-design** threshold for A. The repository has an MIT licence. An A grade does not establish that a child-facing deployment is safe.

## Method and result

I read every `SKILL.md` and its references and applied the eight-dimension rubric in the local `skill-judge` skill. The earlier prototype-specific files scored B when assessed for standalone use because they assumed a particular private app, child age and search tool. The copies in this repository were revised and rescored. These scores are a documented review judgement, not an automated safety test.

| Standalone skill | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | Total |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| [England Year 5 learning](skills/england-year5-learning/SKILL.md) | 17 | 14 | 14 | 15 | 15 | 14 | 9 | 14 | **112/120 (A)** |
| [Everyday advice](skills/child-everyday-advice/SKILL.md) | 16 | 14 | 15 | 15 | 15 | 14 | 9 | 12 | **110/120 (A)** |
| [School research](skills/child-school-research/SKILL.md) | 17 | 14 | 15 | 15 | 15 | 14 | 9 | 13 | **112/120 (A)** |
| [Beginner Japanese](skills/beginner-japanese-for-children/SKILL.md) | 16 | 14 | 14 | 15 | 15 | 14 | 9 | 13 | **110/120 (A)** |

D1 is knowledge value (20 points); D2 expert thinking (15); D3 specific anti-patterns (15); D4 specification and activation description (15); D5 reference loading (15); D6 appropriate freedom (15); D7 structure (10); and D8 practical use (15). The rubric grades A at 108/120 or above.

The short bodies use a navigation pattern: a decision table or rule chooses the next move and loads only the relevant reference. On a rough expert:activation:redundant reading, each is about 75–80:15–20:0–5. The ratio is an editorial estimate, not a token measurement. Year 5 learning earns its stronger D8 from the explicit wrong-step, unclear-reason and second-explanation routes. Everyday advice's lower D8 reflects the limit of a skill when the host lacks a safety route. Research earns D1 and D3 from its evidence table, no-result path and rule against obeying source instructions. Japanese earns D5 and D6 from its single conditional phrase reference and one-step practice choices.

## Feedback addressed

- **Year 5 learning:** Removed the private child's timing and gender assumptions and the web-app dependency. Kept the attempt → representation → check → different explanation route, with examples across subjects. Its reference is selected by subject rather than loaded indiscriminately.
- **Everyday advice:** Removed the assumption that the prototype's parent queue exists. The skill now separates ordinary friendship coaching from fear, repeated harm, unsafe homes and immediate danger, and says explicitly that a child-facing host needs its own tested safety route. It cannot identify every urgent case; this is the main practical limitation behind its lower D8 score.
- **School research:** Removed the `safe_search` tool name, fixed site allow-list assumption and chapter-specific behaviour. It distinguishes a suggested site from a visible result that can support a citation, gives a no-result path, and treats source instructions as untrusted. The optional server-side `safe_search` pattern belongs in [SPEC.md](SPEC.md), not in the standalone skill.
- **Beginner Japanese:** Removed the prototype's persona, precise age and note-process assumptions. Kept its small phrase bank, conditional reference loading, rōmaji-to-kana bridge, and honest text-only limits.

All four skills have a directory name matching their frontmatter `name`, a concrete `description` with use cases, short bodies and explicit reference-loading triggers. They contain no scripts, model-specific commands or `allowed-tools` metadata. They guide responses but grant no capability.

## Source and publication checks

The copies link to Department for Education curricula, the Education Endowment Foundation, Childline, NSPCC, Japan Foundation and other named sources. I reopened the main official references and replaced a UK Safer Internet Centre link that did not load with a working article. National Geographic Kids and Natural History Museum links now use their current landing pages. BBC Bitesize returned HTTP 200 and a page heading of “BBC Bitesize” on 7 October 2026. These notes paraphrase sources; the linked third-party pages and artwork are not bundled.

The repository uses the [MIT licence](LICENSE). A scoped audit found no bundled third-party pages or artwork, private paths, credentials or child chat records. This is a maintainer review, not an independent legal opinion. The `skills` CLI discovered all four local skills, and each installed on its own into a disposable project with its reference files; each also installed separately from the public GitHub repository into a disposable project. The installed skill and reference files matched the source exactly. The private prototype installation and its safety policy remain separate and unchanged.
