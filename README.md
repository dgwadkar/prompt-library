# Team Prompt Library

A collaborative prompt library for the engineering team. Browse, search, and contribute AI prompts — all from a zero-dependency static site hosted on GitHub Pages.

![screenshot](screenshot.png)

**Live site:** [https://your-org.github.io/team-prompts/](https://dgwadkar.github.io/prompt-library/)

## What is this?

A single-page static application that reads prompts from a `prompts.json` file and displays them in a searchable, filterable, and sortable card UI. Teammates contribute new prompts by opening a pull request that adds an entry to `prompts.json`.

### Key features

- Full-text search across titles, descriptions, prompt text, tags, and authors
- Category and sort filters (Featured first, Newest, A–Z)
- One-click copy to clipboard
- Dark mode with system preference detection
- "Suggest a prompt" modal that generates a JSON snippet for PRs
- Skeleton loading, empty states, and error handling
- Keyboard shortcuts: `/` to search, `Escape` to close

## Deploy to GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages → Source** and select **Deploy from branch → `main` → `/ (root)`**.
3. Your site is live at `https://<username>.github.io/<repo-name>/`.

No build step. No Jekyll. The `.nojekyll` file is included to skip Jekyll processing.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for full instructions on:

- How to add a new prompt via PR
- The `prompts.json` schema
- Tips for writing effective prompts

**Quick version:** add an entry to the `prompts` array in `prompts.json`, open a PR, done.

## Configuration

Edit the `CONFIG` object at the top of the `<script>` section in `index.html`:

```js
const CONFIG = {
  repoOwner: 'your-org',       // GitHub org or username
  repoName:  'team-prompts',   // Repository name
  repoUrl:   'https://github.com/your-org/team-prompts',
  appTitle:  'Team Prompt Library',
  appTagline:'Shared prompts for the engineering team',
};
```

These values are used in the page header, document title, and the PR link in the suggest modal.

## Local development

No build step required. Just open the file:

```bash
open index.html
```

Or serve it locally for a more realistic experience:

```bash
npx serve .
```

Then open [http://localhost:3000](http://localhost:3000).

## Repository structure

```
/
├── index.html           # Entire application (HTML + CSS + JS inline)
├── prompts.json         # Prompt data (source of truth)
├── CONTRIBUTING.md      # How to add a prompt via PR
├── README.md            # This file
└── .nojekyll            # Skip Jekyll processing on GitHub Pages
```

## Tech stack

- **HTML / CSS / JavaScript** — Vanilla, no frameworks, no dependencies
- **Google Fonts** — Instrument Sans + JetBrains Mono
- **GitHub Pages** — Static hosting, zero config
- **localStorage** — Theme preference
