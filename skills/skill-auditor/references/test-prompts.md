# Skill Auditor — Activation Tests

Run these three requests verbatim in a fresh chat after any change to this skill. Expected: tests 1 and 2 activate skill-auditor; test 3 must NOT.

## Test 1 — FIRE (Mode C, third-party review)
"Revisa esta skill que encontré en GitHub antes de instalarla, te paso el SKILL.md."
Expected: Mode C runs — static audit plus the safety red-flag scan, verdict install / install with changes / do not install.

## Test 2 — FIRE (Mode B, failure diagnosis)
"La skill de presentaciones falló otra vez: me cambió el texto que le di para maquetar."
Expected: Mode B runs — the failure is classified (Q3 overreach), the two-failure rule is checked, and a minimal substitution fix with a reasoned rule is proposed.

## Test 3 — NO FIRE (near miss)
"Hazme una presentación de ventas con estas notas."
Expected: skill-auditor does NOT activate. This is an execution task for the presentations skill itself, not an audit of it.
