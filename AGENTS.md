# AGENTS.md

Repository-wide instructions for coding agents.

## Working style

- Read only the repository files and documentation relevant to the current task.
- Inspect the existing implementation and tests before changing behavior.
- Prefer the smallest coherent change that solves the task; do not expand scope "while here".
- Run the most relevant available checks before handing work off.
- If a non-trivial attempt fails for a non-obvious reason, diagnose from evidence and escalate model/reasoning instead of repeating speculative patches.

## Model routing

The operator chooses the model outside the repository. Use this common routing policy for new work:

- **Default:** GPT-6.1 Sol / Medium.
- **Mechanical tasks only:** GPT-6 Luna / Low — obvious rename, formatting, typo, simple fixture/documentation edit or similarly narrow low-risk work.
- **Complex tasks:** GPT-6.1 Sol / High — cross-file debugging, non-obvious regressions, integrations, migrations, security-sensitive or stateful changes.
- **Critical/hard tasks:** GPT-6.1 Sol / Max — architecture, difficult multi-system changes, irreversible-data risk, production/deployment/rollback logic, or a hard problem unresolved at High.
- **Independent critical review only:** GPT-6 Astra / High or Max. Astra is not the default implementation model.

Do not use legacy GPT-5.x models or older GPT-6 Sol as the normal recommendation for new work when GPT-6.1 Sol is available.

## Escalation rule

Do not save budget by retrying a weak model many times.

- Luna gets one serious attempt only on a genuinely mechanical task; otherwise move to GPT-6.1 Sol / Medium.
- If Medium exposes hidden complexity, move to High.
- If one evidence-driven High attempt still fails on a hard task, move to Max.
- Use Astra only for an independent critical review.

If the selected tier is clearly too weak, report:

`ESCALATE: <recommended model/reasoning> — <one-line reason>`

Historical references to older models may remain as history; they are not future model recommendations.
