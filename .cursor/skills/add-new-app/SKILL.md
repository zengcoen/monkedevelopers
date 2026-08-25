---
name: add-new-app
description: >-
  Add a new app landing page to the Monke Developers site by copying an existing
  app folder and registering it on the home page. Use when creating a new app
  page, adding an app to the list, scaffolding a new app folder, or when the
  user mentions WordleSolver, wordHuntSolver, or copying an existing app page.
---

# Add a New App

New apps are copy-paste of an existing app folder. Do not invent a new page structure.

## Template to copy

Use **`wordHuntSolver/`** as the template (fullest example: landing page, screenshots, App Store badge, privacy policy, terms).

Structure:

```
wordHuntSolver/
├── index.html
├── privacyPolicy/
│   └── index.html
└── tos/
    └── index.html
```

## Steps

1. **Copy the folder**
   - Duplicate `wordHuntSolver/` → `yourAppName/` (camelCase folder name, matching existing apps).

2. **Generate descriptions from the app name**
   - Titles are often not self-explanatory. Use built-in **web search** (and fetch an official or rules page if needed) unless the user already gave full rules. No extra MCP server is required.
   - Prefer any short hint the user gave when it conflicts with a search snippet.
   - Write a **home-tile blurb**: one short sentence, same tone as existing tiles.
   - Write **landing-page copy**: a short intro paragraph, 2–3 feature bullets, and a closing paragraph — same shape as `wordHuntSolver/index.html`.
   - Do not leave Word Hunt Solver placeholder text. Do not ask the user for marketing copy unless they already provided it.

3. **Update the copied files**
   - `yourAppName/index.html`: title, `<h1>`, generated description/features, screenshot paths under `../images/`, App Store download URL (keep a placeholder link if unknown).
   - `yourAppName/privacyPolicy/index.html`: replace every "Word Hunt Solver" mention with the new app name.
   - `yourAppName/tos/index.html`: same app-name replacement.

4. **Add it to the home list**
   - Edit root `index.html`.
   - Inside `<section class="tiles">`, add a new `<article>` (copy any existing tile).
   - Set `href` to `yourAppName/`, the display name, and the generated one-sentence blurb.
   - Place it with the other live apps (before the commented-out placeholder tiles).

5. **Commit and push**
   The live site is GitHub Pages from `origin/main`. A local commit is not enough.

   ```bash
   git add <new-app-folders> index.html
   git commit -m "Add <App Name> landing, privacy, TOS, and home tile."
   git push origin HEAD
   ```

   Do not force-push. Do not add unrelated untracked files (e.g. `Untitled/`). Skip `git add` for files you did not change.

### Tile template

```html
<article class="style2">
	<span class="image">
		<img src="images/pic01.jpg" alt="" />
	</span>
	<a href="yourAppName/">
		<h2>Your App Name</h2>
		<div class="content">
			<p>Generated one-sentence description based on the app name.</p>
		</div>
	</a>
</article>
```

Cycle `style2` / `style3` / `style4` like neighboring tiles. Reuse an existing `images/picXX.jpg` unless a dedicated image is provided.

## Checklist

- [ ] Folder copied from `wordHuntSolver/`
- [ ] Descriptions generated from the app name (tile + landing page)
- [ ] App name updated in landing, privacy, and ToS pages
- [ ] App Store link / screenshots updated when available
- [ ] New `<article>` added in root `index.html` tiles list
- [ ] Changes committed and pushed to `origin/main`
