# Contributing to Team Prompt Library

Thanks for helping grow the team's prompt library! This guide walks you through adding a new prompt via pull request.

## Getting started

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-org/team-prompts.git
   cd team-prompts
   ```

2. **Create a branch** using the naming convention `prompt/your-prompt-id`:
   ```bash
   git checkout -b prompt/my-new-prompt
   ```

3. **Open `index.html`** locally to preview the site:
   ```bash
   open index.html
   # or
   npx serve .
   ```

## The `prompts.json` schema

Every prompt in the `prompts` array must follow this schema:

```json
{
  "id": "string (kebab-case, unique, stable — never change once merged)",
  "title": "string",
  "description": "string (one sentence — what is this prompt good for?)",
  "prompt": "string (the full prompt text, use \\n for line breaks)",
  "category": "Java | Angular | Testing | Architecture | Git | Debug | General",
  "tags": ["string"],
  "author": "string (GitHub username or your name)",
  "created": "ISO 8601 date string, e.g. 2025-03-15",
  "featured": false
}
```

### Field rules

| Field | Required | Notes |
|-------|----------|-------|
| `id` | Yes | Kebab-case, unique across all prompts. Once merged, **never change it** — it is used as a stable identifier. |
| `title` | Yes | Short, descriptive name. |
| `description` | Yes | One sentence explaining what the prompt is good for. |
| `prompt` | Yes | The full prompt text. Use `\n` for line breaks within the JSON string. |
| `category` | Yes | Must be one of: `Java`, `Angular`, `Testing`, `Architecture`, `Git`, `Debug`, `General`. |
| `tags` | No | Array of lowercase freeform strings (e.g. `["spring-boot", "dto"]`). Defaults to `[]`. |
| `author` | Yes | Your GitHub username or name. |
| `created` | Yes | ISO 8601 date (YYYY-MM-DD). |
| `featured` | No | Defaults to `false`. See "Featured prompts" below. |

## How to pick an `id`

- Use **kebab-case**: lowercase letters, numbers, and hyphens only.
- Make it **descriptive**: `java-stream-refactor`, not `prompt-42`.
- Keep it **concise**: 2–4 words is ideal.
- It must be **unique** across the entire `prompts.json` file.
- **Never change an existing `id`** after it has been merged — it is used as a stable identifier.

## Writing a good prompt

Great prompts share these qualities:

1. **Be specific** — Don't write "Help me with Java." Instead, specify the exact task, constraints, and expected output format.
2. **Use placeholders** — Mark where the user should paste their own content: `[paste your Java class here]`, `[describe the component]`.
3. **Include context** — Mention the tech stack, version, and conventions (e.g. "Spring Boot 3+", "Angular 17+ standalone components").
4. **Target senior engineers** — Assume the reader knows the basics. Focus on architecture, best practices, edge cases, and production readiness.
5. **Structure the output** — Tell the AI what sections or format to use in its response.
6. **Set constraints** — Specify coding standards: SOLID, AAA pattern, conventional commits, data-cy selectors, etc.

## Opening a pull request

1. Add your prompt entry to the `prompts` array in `prompts.json`.
2. Validate the JSON (e.g. paste it into [jsonlint.com](https://jsonlint.com)).
3. Commit and push:
   ```bash
   git add prompts.json
   git commit -m "prompt: add my-new-prompt"
   git push -u origin prompt/my-new-prompt
   ```
4. Open a PR against `main`. In the PR description, briefly explain what the prompt does and why it's useful.

## Featured prompts

A prompt can be marked `"featured": true` when:

- It is considered high-quality and broadly useful by the team.
- A **team lead** approves the featured status.

Featured prompts appear at the top when sorted by "Featured first" and display a badge on their card. Don't set `featured: true` on your own prompt — a team lead will update it after review.

## Questions?

Open an issue or ask in the team Slack channel. Happy prompting!
