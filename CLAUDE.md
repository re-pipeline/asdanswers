# CLAUDE.md: ASD Answers (asdanswers.com)

## What this is
A 1-page hub that links out to other websites for autism families. Plain static HTML, no build step, no framework, no database.

**The person asking for changes (usually Alex) is not a programmer.** Use plain language, never show code unless asked, and just make the change. After each change, say in 1 or 2 sentences what changed and that it will be live on asdanswers.com in about 1 minute.

## How changes go live
1. Code: `github.com/re-pipeline/asdanswers` (public, so Vercel deploys everyone's commits on the free plan; never put secrets or private info in it), branch `main`. Owner: RE pipeline account (Dr. Bogner). Alex (`azaharakis1`) is a collaborator.
2. Hosting: Vercel project `asdanswers`. **Every push to `main` deploys automatically.** Nothing else to run.
3. On Claude Code on the web (claude.ai/code): commit the change and push it to `main` directly, unless the person asks for a review first. Do not leave work on a side branch; a side branch does NOT go live.
4. Undo: revert the last commit and push. Vercel also keeps every past version (Deployments, "Promote").

## Files
- `index.html`: the whole site. Colors are at the top of the `<style>` block (`:root`, with a dark mode copy below it).
- `favicon.svg`: the browser tab icon.
- `og.png`: the preview image shown when the link is shared in texts or social media.
- `vercel.json`: hosting settings. Leave it alone.

## How the page is organized
- **Hero** (top): title, 1 sentence, and jump buttons to each section.
- **Featured**: 3 big cards (Autism is Biomedical, Bogner Health, GutBalancing).
- **Sections**, each marked by a comment `<!-- === SECTION: Name === -->`: Testing, Learn, Family stories, Products and care, Follow.
- Each link is 1 `<a class="card">` block: an icon, a title (`h3`), a short line (`p`), and the website name (`.host`).

### Adding a link
Copy an existing card in the right section, then change the `href`, title, short line and `.host`. Reuse an icon from a similar card (play triangle for videos, audio bars for audio, and so on). Keep `target="_blank" rel="noopener"`.

### Adding a section
Copy a whole `<section class="group">` block, give it a new `id`, and add a matching button in the hero's `.jump` nav.

## Rules
- **Never invent a link.** Use only URLs the person gives you. Before adding one, check it loads (a 200 response). Facebook and X often block automated checks, which is fine.
- **Never invent claims**, numbers or medical statements. Use the person's wording or the linked page's own title.
- Known wrong URLs, never use: `autismisbiomedical.org` (use `.com`), `twitter.com/DrBogner` (use `x.com/MakeAmericaHA`), `rumble.com/c/AutismisBiomedical` (use `rumble.com/user/ResearchedElements`), `gutbalancing.com/1` (404).
- No patient names, patient files or private groups on this public page.
- Writing style: US spelling, no em or en dashes, numerals for numbers.
- The page must keep working on phones (check that nothing is wider than the screen) and in dark mode.
- Keep it 1 static file. No frameworks, trackers or pop-ups without asking Dr. Bogner.
