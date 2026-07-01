# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This repo hosts the legal documents for **iSee** (我明了), an iOS cognitive-training app for young learners aged 9–20, operated by iSee Learning Lab｜我明了学习实验室. It currently contains a single deliverable:

- `privacy.html` — the app's privacy policy, served as a standalone static page (e.g., linked from the App Store listing and inside the app).

There is no build system, package manager, test suite, or CI. Changes are made by editing the HTML directly.

## Structure of privacy.html

The file is one self-contained HTML document with two parallel language versions:

- `<section id="zh" lang="zh-CN">` — Chinese version (canonical/original)
- `<section id="en" lang="en">` — English version
- A `.lang-switch` anchor nav at the top links to `#zh` and `#en`; a `.section-divider` `<hr>` separates the sections.

All CSS lives in a single `<style>` block in `<head>`. It uses CSS custom properties on `:root` with a `prefers-color-scheme: dark` override — keep any new styles working in both light and dark mode.

## Key conventions

- **Keep the two language versions in sync.** Any content change to one section must be mirrored in the other (same headings, same list items, same facts). The Chinese text uses full-width punctuation (，。：); the English uses standard punctuation.
- **No external dependencies.** No JavaScript, no external stylesheets, no fonts, no analytics. The page must remain fully self-contained and work offline. `<meta name="referrer" content="no-referrer">` is intentional.
- **Legal accuracy matters more than polish.** Facts stated in the policy (data collected, third-party services — currently only Apple APNs — contact email `roomemeta@gmail.com`, effective date, age range) must reflect what the app actually does. Do not invent or embellish claims; if a factual change is requested, update both languages and consider whether the effective date in each section's `.meta` line needs bumping.
- **External links** use `target="_blank" rel="noopener"`.
- Commit messages are short, lower-case, imperative descriptions (e.g., `add English version`, `update operator name and contact email`).

## Previewing changes

Open the file directly in a browser, or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/privacy.html
```

Check both light and dark mode and both language sections when reviewing visual changes.
