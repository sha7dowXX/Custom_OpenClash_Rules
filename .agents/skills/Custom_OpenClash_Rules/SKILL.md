```markdown
# Custom_OpenClash_Rules Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to and maintain the `Custom_OpenClash_Rules` TypeScript codebase, which manages custom routing rules for OpenClash. You'll learn the repository's coding conventions, how to safely add or update routing rules, update submodules, and back up documentation—all following established workflows and command patterns.

## Coding Conventions

- **Language:** TypeScript (no framework)
- **File Naming:** Use camelCase for files, e.g. `customDirectList.ts`
- **Import Style:** Use relative imports.
  ```typescript
  import { generateRules } from './ruleGenerator';
  ```
- **Export Style:** Use named exports.
  ```typescript
  export function generateRules() { ... }
  ```
- **Commit Messages:** Follow [Conventional Commits](https://www.conventionalcommits.org/) with prefixes like `chore` and `feat`.
  - Example: `feat: add support for new domain rule format`
- **Test Files:** Named with `.test.` in the filename, e.g. `ruleGenerator.test.ts`

## Workflows

### Add Direct Domain Rule
**Trigger:** When you want to add a new domain to be routed directly in OpenClash (often via Telegram Bot).  
**Command:** `/add-direct-domain`

1. Edit `rule/Custom_Direct.list` to add the new domain (one per line).
   ```plaintext
   example.com
   ```
2. Auto-generate derived rule files:
   - `rule/Custom_Direct_Domain.yaml`
   - `rule/Custom_Direct_Classical.yaml`
   - `rule/Custom_Direct_Domain.mrs`
3. Commit changes with a descriptive message:
   ```
   feat: add example.com to direct domain rules
   ```
4. Push your changes.

**Example:**
```bash
echo "example.com" >> rule/Custom_Direct.list
# Run the script or bot to regenerate files (if applicable)
git add rule/Custom_Direct.list rule/Custom_Direct_Domain.yaml rule/Custom_Direct_Classical.yaml rule/Custom_Direct_Domain.mrs
git commit -m "feat: add example.com to direct domain rules"
git push
```

---

### Bump OpenClash Overwrite Submodule
**Trigger:** When upstream changes are available for the `OpenClash_Overwrite` submodule.  
**Command:** `/bump-overwrite-submodule`

1. Update the submodule pointer:
   ```bash
   cd overwrite/OpenClash_Overwrite
   git fetch origin
   git checkout <latest-commit>
   cd ../..
   git add overwrite/OpenClash_Overwrite
   git commit -m "chore: bump OpenClash_Overwrite submodule"
   git push
   ```
2. Ensure the repository references the new commit.

---

### Auto Backup Wiki
**Trigger:** When the wiki is updated or on a scheduled backup.  
**Command:** `/backup-wiki`

1. Copy or update the relevant markdown file in the `wiki/` directory.
   ```bash
   cp updated_doc.md wiki/updated_doc.md
   git add wiki/updated_doc.md
   git commit -m "chore: backup wiki/updated_doc.md"
   git push
   ```
2. Repeat as needed for other wiki files.

---

## Testing Patterns

- **Test Files:** Place tests in files matching `*.test.*` (e.g., `ruleGenerator.test.ts`).
- **Framework:** Not explicitly detected; use your preferred TypeScript test framework (e.g., Jest, Mocha).
- **Example Test File:**
  ```typescript
  import { generateRules } from './ruleGenerator';

  test('generates correct rules', () => {
    expect(generateRules(['example.com'])).toContain('example.com');
  });
  ```

## Commands

| Command                | Purpose                                                       |
|------------------------|---------------------------------------------------------------|
| /add-direct-domain     | Add a new domain to direct routing rules and regenerate files  |
| /bump-overwrite-submodule | Update the OpenClash_Overwrite submodule to latest upstream |
| /backup-wiki           | Back up or update wiki markdown files                         |
```