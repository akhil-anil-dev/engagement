# Engagement Invitation — Akhil & Gopika

A single-page invitation for the engagement of **Akhil M Anil** and **Gopika C Shaji**,
Sunday, 20 December 2026, Kanjirappally Club Auditorium.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole invitation — self-contained, no build step, no dependencies |
| `preview.png` | 1200×630 share card used by `og:image` for WhatsApp / iMessage link previews |

Fonts (Marcellus + Lora) load from Google Fonts at runtime; everything else is inline.

## Hosting

No build required. Upload both files to any static host, keeping them in the same directory:

- **Netlify Drop** — drag the folder onto <https://app.netlify.com/drop>
- **Cloudflare Pages / Vercel** — point at this repo, no build command, output directory `.`
- **GitHub Pages** — Settings → Pages → deploy from this branch, root folder

### After you know the final URL

`og:image` is currently a relative path, which browsers resolve correctly but some link
crawlers do not. Once the domain is fixed, make it absolute so previews are reliable:

```html
<meta property="og:image" content="https://your-domain.example/preview.png" />
```

The same applies to adding an `og:url` tag, which some crawlers use for canonicalisation.

## Notes

- The countdown and the "Add to Calendar" link are both pinned to a fixed instant —
  20 Dec 2026, 12:00 IST (06:30 UTC) — so they read the same in every timezone.
- The envelope cover is dismissed with JavaScript; a `<noscript>` block hides it so the
  invitation is still readable with JS disabled.
- There is currently **no RSVP or contact number** on the page. Worth adding to the
  details card before sending it out.
