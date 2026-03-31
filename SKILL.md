---
name: translate-md
description: Translate English Markdown documents to Chinese. Use when user says "translate document", "translate doc", "翻译文档", "翻译文件", or provides a filename and asks for translation. Translates .md files from English to Chinese, preserving original formatting, and saves with -zh suffix in the same directory.
---

# Translate Markdown Document

Translate English Markdown documents to Chinese.

## Workflow

### Step 1: Locate the source file

- Use Glob to find `.md` files matching the user-provided name (fuzzy match)
- Search scope: current project directory
- If multiple matches, list them and ask user to confirm
- If no match found, report and stop

### Step 2: Read and translate

- Read the entire source file
- Translate **sentence by sentence** from English to Chinese
- **Preserve** all Markdown formatting: headings, code blocks, links, images, tables, lists, YAML frontmatter
- **Do not** expand, reduce, or rewrite the original meaning
- **Do not** translate: code within code blocks, URLs, file paths, variable names, CLI commands
- **Do translate**: prose text, comments within code blocks, heading text, table headers and cell text, alt text for images

### Step 3: Write the translated file

- Output path: same directory as source file
- Filename: replace `.md` suffix with `-zh.md`
  - `README.md` → `README-zh.md`
  - `docs/guide.md` → `docs/guide-zh.md`
- Use Write tool to create the file

## Translation rules

1. **Faithful translation** — stay true to original meaning, do not add opinions or omissions
2. **Technical terms** — keep widely-used English terms as-is (e.g., API, Docker, React, CI/CD); translate general concepts into natural Chinese
3. **Formatting** — identical Markdown structure as the source
4. **YAML frontmatter** — translate values only, keep keys in English
