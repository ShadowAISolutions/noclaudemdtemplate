# Project Rules

## Skill Protection Policy

**Imported skills must NEVER be modified.** Only their location pointers (paths, references) may be updated.

- **Imported skills**: Read-only. Do not edit, rewrite, rename, or alter the content of any imported skill file. The only permitted change to an imported skill is updating its location pointer (e.g., file path or reference URL) if the skill is moved or reorganized.
- **Custom skills**: May be freely created, edited, or deleted.

This separation ensures clear traceability — you can always determine which skill (imported vs. custom) is responsible for any given action. If a change is needed to an imported skill's behavior, create a new custom skill instead of modifying the imported one.
