# Sambridge — Landing Page Content Form

نموذج تجميع محتوى الـ Landing Page من العميل. صفحة ثابتة (static) بالكامل — لا يوجد باك إند.

## What it is

A single-page Arabic (RTL) intake form with 52 fields across 14 sections. The client
fills it in, their answers autosave to their browser's `localStorage`, and the
"تحميل الإجابات" button downloads everything as a plain `.txt` file they send back
over WhatsApp or email.

- **No backend, no database, no API keys.** Nothing leaves the client's browser.
- **Autosave**: answers are keyed by section title + field label, so reordering
  sections or inserting new fields later won't scramble a client's saved answers.
- **noindex**: both a `<meta name="robots">` tag and an `X-Robots-Tag` header, plus
  `robots.txt`. The page is public but won't show up in search results.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire form — markup, styles, and script in one file |
| `vercel.json` | Clean URLs, security + noindex headers, no-cache on the HTML |
| `robots.txt` | Blocks crawlers |

## Local preview

Just open `index.html` in a browser. Or serve it:

```bash
npx serve .
```

## Deploy

Connected to Vercel via GitHub — **every push to `main` redeploys automatically.**

```bash
git add -A
git commit -m "Update form"
git push
```

First-time setup in Vercel: New Project → import this repo → Framework Preset
**Other** → leave build & output settings empty → Deploy.

## Editing the form questions

All questions live in the `DATA` array inside `index.html`. Each field is:

```js
{label:"اسم الحقل | Field Name", inst:"التوضيح", ex:"مثال"}
```

Add, remove, or reorder freely — the field count and progress bar update themselves.
Changing a field's `label` or its section `title` orphans any answer a client had
already saved for it, so avoid renaming once you've sent the link out.
