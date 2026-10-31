# ZERO2TWELVE Product School — Website

A complete, responsive marketing site built from the 2026 print brochure
(`brochure_print (1).pdf`), extended with a **Professional Track** of live
soft-skills courses for working professionals.

No build step, no framework, no dependencies. Open `index.html` and it runs.

---

## Pages

| File | Purpose |
|---|---|
| `index.html` | Full landing page — hero, guarantee card, who it's for, 4-week curriculum, payment ladder, guarantee, fee breakdown, why Z2T, Professional Track, FAQ, application form |
| `courses.html` | Professional Track catalogue — 9 detailed soft-skills courses with filters, how it works, enquiry CTA |

## Structure

```
zero2twelve-site/
├─ index.html
├─ courses.html
└─ assets/
   ├─ css/style.css       ← all styling + design tokens
   └─ js/
      ├─ courses.js       ← course catalogue data (edit courses here)
      └─ main.js          ← nav, tabs, filters, reveal, WhatsApp form
```

## Design system

Drawn directly from the brochure's palette and typography:

| Token | Value | Use |
|---|---|---|
| `--paper` | `#F7F6F1` | Page background |
| `--ink` | `#12181F` | Text, dark sections |
| `--gold` | `#C1922E` | Accent lines, buttons, seals |
| `--gold-deep` | `#846210` | Small gold text (AA contrast) |
| `--sage` | `#D6D9D0` | Quiet chips and rules |
| `--green` | `#2B6B52` | "Included" badges |

- Display type: **Fraunces** (serif, italic accents)
- Body: **Inter**
- Labels / eyebrows: **JetBrains Mono** (uppercase, wide tracking) — echoes the
  brochure's Courier labels.

All colours meet WCAG AA; Lighthouse scores **100** for accessibility,
best practices and SEO.

## Editing content

### Courses
Open `assets/js/courses.js` and edit the array. Each course:

```js
{
  id: "negotiation",
  cat: "influence",            // communication | influence | leadership | thinking
  catLabel: "Influence",       // shown on the card
  title: "Negotiation for Professionals",
  dur: "2 weeks",
  level: "Mid–senior",
  blurb: "One-line promise.",
  modules: ["Module 1", "Module 2", "Module 3", "Module 4"],
  included: false              // true → "Included with PM Program" badge
}
```

The homepage grid and the full catalogue both render from this file, so one
edit updates both pages.

### Contact / application
- Phone and WhatsApp number: `+91 91728 97662` (appears in the header, apply
  panel, footer, and in the `wa.me` links in `main.js` / `index.html`).
- The application form validates name + phone, then opens WhatsApp with the
  details pre-filled. Nothing is stored or sent to a server.

### Copy
All brochure content is preserved: guarantee, milestone ladder, ₹1,00,000 fee
split into 4 × ₹25,000, post-placement support, FAQ and the "Ready to ascend?"
CTA. The Professional Track is new content added on request.

## Running locally

```bash
cd zero2twelve-site
python -m http.server 4173
# open http://localhost:4173
```

Or simply double-click `index.html` — everything works from the file system too.

## Deploying

Drag the whole `zero2twelve-site` folder onto Netlify Drop, or push it to a
GitHub repo and enable GitHub Pages / Vercel. It is fully static.

Before going live, update the two placeholder values if they change:
- WhatsApp number in `assets/js/main.js` (`wa.me/919172897662`) and the
  `wa.me` links in both HTML files.
- Any cohort dates or fees, if they differ from the 2026 brochure.

## Notes

- Fonts load from Google Fonts with local serif/sans fallbacks, so the site
  still reads well offline.
- Motion respects `prefers-reduced-motion`.
- Course filtering, curriculum tabs, mobile nav and FAQ accordions are all
  keyboard accessible.
