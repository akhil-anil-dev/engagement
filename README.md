# Engagement Invitation — Akhil & Gopika

A single-page invitation for the engagement of **Akhil M Anil** and **Gopika C Shaji**,
Sunday, 20 December 2026, Kanjirappally Club Auditorium.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole invitation — self-contained, no build step, no dependencies |
| `preview.png` | 1200×630 share card used by `og:image` for WhatsApp / iMessage link previews |
| `vercel.json` | Static hosting config — no build, plus cache headers |

Fonts (Marcellus + Lora) load from Google Fonts at runtime; everything else is inline.

## Deploying to Vercel

There is no build step. Import the repo at <https://vercel.com/new> and deploy —
`vercel.json` already sets the framework to none and serves from the repo root, so
every setting can be left at its default.

Or from the CLI:

```bash
npx vercel --prod
```

Cache headers are set so `index.html` always revalidates — edits to the invitation show
up immediately for guests who have opened the link before — while `preview.png` is
cached for a day.

### After the first deploy: make `og:image` absolute

`og:image` is currently the relative path `preview.png`. Browsers resolve it correctly,
but some link crawlers require an absolute URL, and that is what drives the WhatsApp and
iMessage preview card. Once the production domain exists, update both tags in
`index.html`:

```html
<meta property="og:image" content="https://your-domain.example/preview.png" />
<meta property="og:url"   content="https://your-domain.example/" />
```

Then re-share the link. WhatsApp caches previews aggressively, so an already-sent link
may keep showing the old (or empty) card.

## Notes

- The countdown and the "Add to Calendar" link are both pinned to a fixed instant —
  20 Dec 2026, 12:00 IST (06:30 UTC) — so they read the same in every timezone.
- The envelope cover is dismissed with JavaScript; a `<noscript>` block hides it so the
  invitation is still readable with JS disabled.
- There is currently **no RSVP or contact number** on the page. Worth adding to the
  details card before sending it out.
