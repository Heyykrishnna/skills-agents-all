Repository agent instructions
=============================

Complete the user's requested work with the smallest maintainable change. Use the installed skills when their workflows apply, keep code self-explanatory, and verify the result before reporting completion.

Working rules
-------------

- Read the applicable instructions, relevant source files, and existing configuration before editing. More specific directory instructions apply within their scope; system, developer, and explicit user instructions take precedence over skill guidance.
- Inspect the working tree first. Preserve existing user changes and keep edits within the requested scope.
- Resolve facts through repository files, tools, and primary documentation. Ask the user for decisions or information that cannot be obtained from those sources.
- Reuse existing conventions, dependencies, and modules before introducing new ones. Create documentation, configuration, and directories only when the task needs them.
- Read the relevant installed Next.js guide before writing application code, as required by the generated instructions below.

Agent skills
------------

The canonical skill sources are `.agents/skills/<name>/SKILL.md`. The directories under `skills/` and the other agent-specific skill folders are links to the same collection, not separate workflows.

1. Match the requested outcome to the skill directory below. Select every skill needed for that outcome, rather than running the entire collection.
2. Read each selected `SKILL.md` in full before using it. Follow its relevant reference links, templates, prerequisites, checkpoints, and completion criteria. Resolve relative references from that skill's directory.
3. Check the skill's frontmatter. Skills with `disable-model-invocation: true` require an explicit request for that workflow; a natural-language request counts. An authorized parent workflow may require supporting skills. A related keyword alone does not authorize a separate workflow.
4. Use model-invoked skills when their documented triggers apply. State which skill is being used and why when first applying it.
5. Combine skills in dependency order. Load shared references such as `codebase-design`, `domain-modeling`, or `writing-for-agents` when the active workflow needs them; keep each artifact's instructions in its owning skill.
6. Check prerequisites only for the workflow being used. Tracker-dependent workflows need the configured tracker and label mapping. If configuration is missing, explain the missing prerequisite and offer `setup-matt-pocock-skills`; ordinary local edits do not require tracker setup.
7. Use the harness's skill loader when available; otherwise read the local skill file directly. If a required skill, reference, tool, or permission is unavailable, report the specific limitation and complete independent work. Never claim that an unavailable workflow ran.
8. Delegate when the user or the active skill requires it and the harness supports it. Give each agent a bounded task and source pointers, isolate concurrent code edits where required, and integrate and verify the results. Reading the skill directory alone does not activate delegation.

Skill directory
---------------

These are routing pointers. The linked skill and its frontmatter define the actual workflow and invocation requirements.

**Planning and requirements**

| Skill | Use when |
| --- | --- |
| [ask-matt](.agents/skills/ask-matt/SKILL.md) | The user asks which skill or sequence of skills fits their situation. |
| [grilling](.agents/skills/grilling/SKILL.md) | The user wants to stress-test a plan or decision through a structured interview. |
| [grill-me](.agents/skills/grill-me/SKILL.md) | The user requests a stateless design interview without repository documentation. |
| [grill-with-docs](.agents/skills/grill-with-docs/SKILL.md) | The user requests a design interview that records resolved domain terms and significant decisions. Uses `grilling` and `domain-modeling`. |
| [wayfinder](.agents/skills/wayfinder/SKILL.md) | The user needs a decision map for an effort too uncertain or large for one session. Resolve planning questions before handing off to specification and implementation. |
| [to-spec](.agents/skills/to-spec/SKILL.md) | The user wants an existing discussion synthesized into a specification. Reuse settled requirements, check testing seams, and follow the configured tracker workflow. |
| [to-tickets](.agents/skills/to-tickets/SKILL.md) | The user wants a plan or specification split into verifiable vertical slices with explicit blockers. Publish after the skill's breakdown checkpoint. |
| [to-questionnaire](.agents/skills/to-questionnaire/SKILL.md) | Required facts belong to another person and the user wants a questionnaire to collect them. Prepare the document; sending it requires authorization. |
| [loop-me](.agents/skills/loop-me/SKILL.md) | The user wants to identify recurring activities and write workflow specifications. Scheduling or implementation is a separate action. |

**Implementation, diagnosis, and review**

| Skill | Use when |
| --- | --- |
| [implement](.agents/skills/implement/SKILL.md) | The user requests the spec or ticket implementation workflow. Use `tdd` where applicable, validate the change, and finish with `code-review`. |
| [implement-spec](.agents/skills/implement-spec/SKILL.md) | The user requests implementation of an entire ticketed spec through parallel implementers and an integration branch. Requires the task graph, tracker configuration, and final review. |
| [tdd](.agents/skills/tdd/SKILL.md) | The user requests test-first development or integration tests, or an active implementation workflow requires it. Use agreed public seams and one failing behavior test followed by its minimal implementation. |
| [diagnosing-bugs](.agents/skills/diagnosing-bugs/SKILL.md) | The user reports a failure, intermittent bug, or performance regression. Establish a symptom-specific feedback loop, reproduce and minimize, test hypotheses, then verify the fix and remove instrumentation. |
| [code-review](.agents/skills/code-review/SKILL.md) | A branch, PR, or change needs review against a fixed point. Review documented standards and specification compliance separately using the skill's independent reviewers. |
| [pr](.agents/skills/pr/SKILL.md) | Writing or updating a PR body. Use its summary, before/after evidence, and reversibility guidance. |
| [migrate-to-shoehorn](.agents/skills/migrate-to-shoehorn/SKILL.md) | Migrating test assertions or constructing partial test data with Shoehorn. Keep the helpers in tests. |
| [triage](.agents/skills/triage/SKILL.md) | The user requests evaluation of incoming issues or configured external PRs. Verify claims, use configured roles, and produce durable briefs; tickets already produced by `to-tickets` are ready for implementation. |

**Architecture and investigation**

| Skill | Use when |
| --- | --- |
| [codebase-design](.agents/skills/codebase-design/SKILL.md) | Designing a module's interface, placing testing seams, or reducing architectural friction. Use its deep-module vocabulary and principles. |
| [domain-modeling](.agents/skills/domain-modeling/SKILL.md) | Defining or correcting domain terminology, editing a glossary, or recording a consequential architectural trade-off. Create records only when there is something substantive to record. |
| [improve-codebase-architecture](.agents/skills/improve-codebase-architecture/SKILL.md) | The user requests an architectural survey. Present evidenced deepening opportunities in the skill's visual report, then explore the selected candidate. |
| [prototype](.agents/skills/prototype/SKILL.md) | A concrete UI or logic experiment is needed to answer a design question. Select the relevant branch, keep it runnable and explicitly temporary, and capture the conclusion. |
| [research](.agents/skills/research/SKILL.md) | The user needs documentation, API facts, or another question investigated. Delegate reading to a background agent and capture findings with primary-source citations. |
| [retro](.agents/skills/retro/SKILL.md) | The user requests a retrospective. Use session evidence to recommend improvements to tooling, checks, navigation, and agent instructions. |

**Setup and human procedures**

| Skill | Use when |
| --- | --- |
| [setup-matt-pocock-skills](.agents/skills/setup-matt-pocock-skills/SKILL.md) | The user requests repository workflow setup or a tracker-dependent workflow lacks configuration. Configure the tracker, triage vocabulary, and domain-document pointers through its checkpoints. |
| [setup-pre-commit](.agents/skills/setup-pre-commit/SKILL.md) | The user requests Husky, lint-staged, formatting, or commit-time checks. Adapt to existing scripts and merge existing configuration. |
| [setup-ts-deep-modules](.agents/skills/setup-ts-deep-modules/SKILL.md) | The user requests enforced TypeScript package entry points. Configure dependency-cruiser and demonstrate pass/fail/pass behavior for its rules. |
| [git-guardrails-claude-code](.agents/skills/git-guardrails-claude-code/SKILL.md) | The user requests Claude Code hooks that block dangerous Git commands. Establish project or global scope and verify the hook. |
| [wizard](.agents/skills/wizard/SKILL.md) | A procedure contains steps only a human can perform, such as credential entry or dashboard actions. Build and validate the guided script using the supplied template. |

**Coordination and communication**

| Skill | Use when |
| --- | --- |
| [chief-of-staff](.agents/skills/chief-of-staff/SKILL.md) | The user requests long-running coordination through subagents. Use its delegation discipline; create schedules only when authorized. |
| [handoff](.agents/skills/handoff/SKILL.md) | The user requests a portable summary for another agent, directory, or harness. Save it to the OS temporary directory, redact secrets, and reference existing artifacts. |
| [claude-handoff](.agents/skills/claude-handoff/SKILL.md) | The user requests immediate continuation in a fresh Claude background agent and the Claude CLI is available. Prepare the redacted handoff before launching. |
| [wait-what](.agents/skills/wait-what/SKILL.md) | The user asks for the previous explanation to be restated with missing context and simpler language. |

**Writing and teaching**

| Skill | Use when |
| --- | --- |
| [writing-for-agents](.agents/skills/writing-for-agents/SKILL.md) | Creating or editing agent instructions, skills, or reference documents agents consume. Keep pointers precise and instructions concise and verifiable. |
| [writing-fragments](.agents/skills/writing-fragments/SKILL.md) | The user requests exploration of raw writing material without committing to an outline. Preserve user edits and append fragments to the agreed file. |
| [writing-shape](.agents/skills/writing-shape/SKILL.md) | The user wants existing raw material shaped into a separate article, one agreed block at a time. Preserve the input file. |
| [writing-beats](.agents/skills/writing-beats/SKILL.md) | The user wants a guided choice of narrative beats from existing material. Ground concepts before using them and append one chosen beat at a time. |
| [teach](.agents/skills/teach/SKILL.md) | The user requests ongoing teaching in a persistent workspace. Ground lessons in their mission, trusted resources, and recorded progress. |
| [scaffold-exercises](.agents/skills/scaffold-exercises/SKILL.md) | The user requests course exercise structures with problem, solution, or explainer variants. Use the course conventions and its validator when installed. |

Code quality
------------

- Write self-explanatory code with precise names and clear control flow. Keep authored code free of explanatory comments, commented-out code, TODO/FIXME notes, and decorative hash or separator banners. Preserve required language syntax, shebangs, legal notices, framework directives, and generated markers.
- Keep modules focused on one responsibility. Co-locate behavior that changes together, separate domain logic from presentation and external I/O where needed, and expose small interfaces that hide useful implementation detail.
- Prefer straightforward functions and composition. Introduce helpers, interfaces, layers, and shared abstractions only when they remove demonstrated complexity or duplication.
- Implement the requested use cases and the validation and failure handling needed to make them correct. Exclude speculative features, unused options, unrelated refactors, placeholder flows, and dependencies without a current purpose.
- Use strict, meaningful types. Validate untrusted input at entry points and narrow it before use. Avoid `any`, double casts, non-null assertions, and suppression directives that conceal an unresolved type problem.
- Keep state minimal and derive values when practical. Handle asynchronous failures deliberately; surface actionable errors and clean up resources and subscriptions.
- Match the project's formatting, import, naming, and file-layout conventions. Remove dead code, unused imports, duplicate logic, temporary debugging output, and unnecessary exports from touched code.
- For UI work, use semantic elements, accessible names, keyboard interaction, and appropriate loading, empty, and error states for the requested behavior.
- Keep secrets out of source files, logs, examples, and reports. Redact diagnostic artifacts before sharing them.

Verification and completion
---------------------------

- Read `package.json`, the lockfile, and relevant tool configuration before choosing commands. Use the existing package manager and installed tooling; do not assume a test or typecheck script exists.
- For code changes, run the configured lint command, TypeScript checking when applicable, and relevant behavior tests when available. Run a production build when the change affects application or build behavior. Report missing tooling or failing checks accurately.
- Tests should observe behavior through appropriate public interfaces, use independently justified expected results, and exercise meaningful requirements or regressions. Documentation-only changes need link, coverage, and diff checks rather than new application tests.
- Review the final diff for requirement coverage, unintended edits, unnecessary abstractions, comments or banners introduced into authored code, and temporary artifacts.
- Stage only task-owned files when committing under an authorized workflow. Preserve unrelated changes; push, publish, send messages, or perform destructive operations only within the user's authorization.
- Report the outcome, the files changed, the checks actually run, and any remaining limitation. Completion requires the requested artifact to exist and its applicable checks to be accounted for.

Maintaining these instructions
------------------------------

When adding, renaming, or removing a local skill, update its routing pointer here and verify the target exists. Keep detailed procedures in their `SKILL.md` files. Preserve the Next.js-managed block below, including its generated markers.

<!-- BEGIN:nextjs-agent-rules -->

## This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->
