---
name: skill-auditor
description: Audits, diagnoses, and improves existing skills (SKILL.md files and their folders), and safety-reviews third-party skills before installation. Use when Danny says "audita esta skill", "revisa esta skill", "mejora esta skill", "esta skill falló otra vez", "audit this skill", or "review this skill before I install it". Do not use to create a brand-new skill from scratch, and never to run the audited skill's own task.
---

# Skill Auditor

Audit a skill the way a manual gets audited: check that it activates when it should, produces the same result every time, and does the work the owner's way — then fix the manual, not just the output.

The full checklists live in `references/checklist.md` — open it before every audit; it carries the static checklist, the five common errors, and the safety red-flag list. This skill's own activation tests live in `references/test-prompts.md` — run them after changing this skill.

## Mode A — Static audit (a skill that exists but is unproven)

1. Read the whole skill folder first: SKILL.md, every bundled file, every script. Never audit from the description alone, because the description is only the label on the drawer.
2. Check the frontmatter: valid YAML, `name` in lowercase kebab-case matching the folder name, `description` present.
3. Score the description against the trigger formula in `references/checklist.md`: what it does (verb first) + when to use it + the owner's literal phrases in quotes + an explicit when-NOT-to-use clause. Two to three lines; longer descriptions activate worse, not better.
4. Check distinctness: compare the description against the owner's other skills. Two skills whose descriptions differ only in name will steal each other's activations; they must differ by situation of use.
5. Check the body reads as a recipe: numbered steps with verbs, order, and conditions. Flag persona fluff ("you are an expert…") and any always-true personal context (who the owner is, general preferences) — that belongs in standing instructions, not in the skill, because it bloats every run and blurs the task.
6. Check every bundled file is cited in SKILL.md by its exact name and extension. An uncited file is invisible: the model does not know it exists.
7. Check anything that must come out exact (counts, calculations, format conversions, rule validations) is delegated to a script under `scripts/`, with an explicit instruction to use the script's result and not compute it directly. Models improvise numbers; scripts do not.
8. Check there is an output contract: what the skill must deliver every time it runs.
9. Propose an activation test set for the audited skill: three requests in the owner's natural words — two that must activate it, one near-miss that must not. Store them in the skill folder as `references/test-prompts.md` so they can be re-run after every change.

## Mode B — Failure diagnosis (a skill that already failed)

1. Get the failure in the owner's words first: what came out wrong, and what should have come out. Do not start editing before the failure is stated concretely.
2. Apply the two-failure rule: if this exact failure happened only once, it may be an exception — fix the output in the conversation and note the failure. If it is the second time, it is a pattern: fix the skill.
3. Separate one-off requests from skill defects. A single client's preference (a bigger logo, a different title once) is fixed in the conversation; putting it in the skill would make every future job inherit one exception.
4. Classify the failure with the three questions — each one points at a different fix:
   - **Q1 Activation** — did it use the right skill at the right time (fired when it shouldn't, or never fired)? The fix is the **description**: clarify when, and above all when NOT.
   - **Q2 Consistency** — does the same request give different results on different days? The fix is the **criteria**: pin down the exact formula, steps, or script. When a run comes out right, analyze what made it right and write that into the skill, removing ambiguities.
   - **Q3 Quality / overreach** — did it do the work its own way instead of the owner's (rewriting what it should only format, adding unrequested flourishes)? The fix is a **rule with its reason**.
5. Write the fix as a substitution, not a patch: replace the old text with the new text in the one section the diagnosis points to. Patch piles make skills long, and long instructions get skimmed diagonally — key rules get skipped.
6. Give every new or changed rule its reason in the same line. A bare "never" makes the model brake too hard and underperform; a reason lets it adapt the rule to cases the skill did not foresee.
7. Re-run the original failing request verbatim and confirm the failure is gone. Then re-run the skill's three activation tests from its `references/test-prompts.md` (or Mode A step 9 if none exist yet).

## Mode C — Third-party safety review (before installing anyone else's skill)

1. Run Mode A first — a badly built skill is rejected on quality alone.
2. Then scan SKILL.md, every bundled file, and every script against the red-flag list in `references/checklist.md`: credential or token requests, data sent to outside hosts, destructive commands, instructions hidden in comments or data files, attempts to override safeguards or standing instructions, obfuscated code.
3. Verdict is one of three: **install**, **install with changes** (name each change), or **do not install** (name the red flag). Never soften a safety verdict because the skill looks useful.
4. A third-party skill is installed only after the owner approves the verdict. This review informs that decision; it does not replace it.

## Output contract

Every run delivers, in this order:

1. The verdict: one line (healthy / needs changes / do not install, as the mode applies).
2. The findings table: one row per check — PASS, WARN, or FAIL — with one line of evidence each. No finding without evidence from the actual files.
3. The fixes: for each FAIL or WARN, the exact replacement text, delivered as a clean copy block with nothing mixed in, so it can be pasted without editing.
4. The activation test set (Mode A) or the re-test result (Mode B).

## Operating rules

1. Audit the manual, not the last output — outputs are symptoms; the skill text is the cause. (Mitjana's intern rule: correcting the intern out loud fixes today; updating the manual fixes every day after.)
2. Change only the section the diagnosis points to. A Q1 fix never rewrites the steps; a Q3 fix never touches the description.
3. Keep the most important rules at the top of the skill. Order is a feature: models weight early instructions more.
4. When two sources conflict — the skill text versus what the owner says they want — the owner wins, and the skill gets updated to say so.
5. This skill's sources are Xavier Mitjana's skills guide (build) and his summary of Anthropic's method (diagnose and repair), adapted to Danny's environment. The detailed lists are in `references/checklist.md`.
