# Postline — wireframes and design concepts

Site skeleton and three homepage design directions for the new postline.lv, built from Relume library components so the Webflow build can follow Finsweet Client-First one-to-one.

- **Canvas (live, editable):** https://claude.ai/artifact/Wvq3Z2KfskRVAZDuwknVK4. It is private until shared from the page's Share menu.
- **Brief:** https://claude.ai/artifact/R8htvfrq6hZ6MmWdFk9GhR
- **Source of the canvas:** `wireframes/canvas/`. These are `.dc.html` artboards; images are referenced as `/_blob/…` and only resolve inside the canvas.

Language on the site: Latvian only. Mobile view is the priority, because drivers open the page from job ads on their phones.

## How the wireframes map to Webflow

Every section on the canvas is labelled with its Relume component and its default Relume/Client-First classes. Paste the same component from the Relume Webflow library and you get this structure:

```
page-wrapper
└─ main-wrapper
   └─ section_header1                 ← Relume section class
      └─ padding-global
         └─ container-large
            └─ padding-section-large
               └─ header1_component   ← Relume component class
```

- Navbar 1 and Footer 3 become Webflow Components shared by all public pages.
- Classes prefixed `wf-` in the canvas CSS exist only for the wireframe view. Do not recreate them in Webflow.
- The wireframe artboards have two toggles (Tweaks → Anotācijas): `showSpecs` (blue component chips) and `showTasks` (yellow text tasks for Artis). Turn both off to present a clean skeleton.

## Sitemap

| Page | Slug | Sections (Relume) |
| --- | --- | --- |
| Sākums | `/` | Navbar 1 · Header 1 · Stats 13 · Layout 251 · Layout 645 (`#par-mums`) · Portfolio 11 · Testimonial 17 · CTA 1 · Contact 5 · Footer 3 |
| Pakalpojumi uzņēmumiem | `/pakalpojumi-uznemumiem` | Navbar 1 · Header 50 · Layout 623 · Layout 647 · Stats 8 · FAQ 3 · Contact 6 (`#pieprasijums`) · Footer 3 |
| Pārvākšanās | `/parvaksanas` | Navbar 1 · Header 1 · Layout 629 · Layout 671 · Timeline 17 · Layout 216 · Testimonial 17 · Multi Form 17 (`#pieteikums`) · FAQ 3 · Footer 3 |
| Darbs pie mums | `/darbs` | Navbar 1 · Header 5 · Layout 620 · Layout 645 · Career 12 (`#vakances`) · Contact 9 (`#pieteikties`) · Footer 3 |
| Kontakti | `/kontakti` | Navbar 1 · Contact 14 · Contact 5 · Footer 3 |
| Darbinieku sadaļa (hidden) | `/darbinieki` | Links 1 only, with no Navbar or Footer: one button that opens the daily report. Set `noindex, nofollow` and leave it out of the menu and of `sitemap.xml` (see below). |

Navbar: Pakalpojumi ▾ (Kurjerpakalpojumi uzņēmumiem · Pārvākšanās · Transporta noma) · Par mums · Darbs pie mums · Kontakti, plus the buttons "Sazināties" (secondary) and "Pieteikt pārvākšanos" (primary).

Small deviations from the stock Relume components (all noted on the canvas):

- Layout 251: a link at the bottom of each service card.
- Timeline 17: step numbers instead of dates, 4 items.
- Contact 5 on `/kontakti`: an added radio "Uzņēmums / Privātpersona" and a topic select.
- Multi Form 17: Postline's 4 steps (below) replace the stock fields.

## Forms → GoHighLevel

| Form | Where | Fields |
| --- | --- | --- |
| Pārvākšanās pieteikums (Multi Form 17) | `/parvaksanas#pieteikums` | 1) Privātpersona / Uzņēmums · 2) no adreses, uz adresi, vēlamais datums · 3) apjoms un apraksts, stāvs un lifts abās vietās, foto augšupielāde · 4) vārds, tālrunis, e-pasts (+ uzņēmums). After sending: automatic confirmation to the client. |
| B2B pieprasījums (Contact 6) | `/pakalpojumi-uznemumiem#pieprasijums` | uzņēmums, kontaktpersona, e-pasts, tālrunis, pakalpojums (select), aptuvenais apjoms (radio), papildu informācija |
| Kontaktforma (Contact 5) | `/`, `/kontakti` | vārds, e-pasts, (Kontakti: Uzņēmums / Privātpersona, tēma), ziņa |
| Darba pieteikums (Contact 9) | `/darbs#pieteikties` | vārds, uzvārds, tālrunis, vakance, autovadītāja apliecība, pieredze, CV (optional) |

There is no price calculator (removed on 29.09.). Testimonial 17 reads from a CMS collection fed by GHL review requests and stays hidden until the first reviews come in.

## Design concepts (homepage)

All three keep the existing orange "P" logo (#F05223, white line-drawn P) from postline.lv and the same section structure. Only the hero component, colours and type change.

| | A — Signāllīnija | B — Grafīts | C — Uzticības zils |
| --- | --- | --- | --- |
| Idea | Evolution of the current site: white, signal orange, the big orange "P" panel from the old homepage | Dark, industrial, night-shift logistics | Calm, corporate, rounded; built from the old site's slate and coral |
| Hero | Header 1 | Header 5 (full-bleed photo) | Header 15 (image below heading) |
| Background | #FFFFFF / #F5F4F2 | #111315 / #191C1F | #F2F4F5 / #FFFFFF |
| Text | #161616, muted #555555 | #F2F1EE, muted #A7ADB2 | #1F2B31, muted #4F5D65 |
| Primary button | #F05223 with #161616 text | #F05223 with #111315 text | #263238 with white text |
| Accent | #F05223 (stats on light grey: #C43C12) | #F05223 | #FF8A65 (decorative only, never for text) |
| Fonts | Raleway 800 headings (the current site's font) + Lato | Archivo (expanded, uppercase headings) + IBM Plex Mono labels | Manrope |
| Corners | square | 2px | 20px cards, pill buttons |

Contrast note: white text on #F05223 is only 3.5:1, so the orange buttons use dark text.

## Images

Stock photos in the concepts are from Unsplash (free licence) and are meant to be replaced later, ideally after a ~100 € photo session. None show any courier brand.

| Use | Unsplash photo |
| --- | --- |
| Fleet of white vans | `photo-1587813369290-091c9d432daf` |
| White van by a brick building | `photo-1641199788912-9a7385a35c82` |
| Box truck at dusk | `photo-1614976523626-d598aafd4fda` |
| Worker with a cart on a cobbled street | `photo-1764696745397-42701a7efd3f` |
| Smiling van driver | `photo-1762095996527-126e49ef9d72` |
| Parcel handover | `photo-1566576721346-d4a3b4eaeb55` |
| Man carrying boxes | `photo-1543499459-d1460946bdc6` |
| Archive boxes | `photo-1757837593538-b4a8654132f1` |
| Open-plan offices | `photo-1577412647305-991150c7d163`, `photo-1631193816258-28b44b21e78b` |

## The hidden staff page (`/darbinieki`)

Discussed on the 30.09 call (https://fathom.video/calls/843688534, near the end):

- Artis runs the company's daily work in a tool built in Google Apps Script. Every driver fills in a daily report in Google Forms and opens it through a personal link.
- Artis wants drivers to reach the report through postline.lv, so that they visit the company site every day and feel part of the company, not only of the job.
- Clients must not see it. Jānis proposed a hidden address such as `postline.lv/darbinieki`, or, as an alternative, a small admin panel built by our developers. The call ended without a choice; the canvas shows the hidden page, which is the simpler of the two.

How to build it: a Webflow page from Links 1 with one button that leads to the existing report. The Google system stays as it is. A hidden address keeps clients out but is not protection: anyone with the link can open it. If the report links must stay private, turn on Webflow page password protection, which is built in.

## Content still to come from Artis

Text in square brackets on the canvas is a placeholder for these:

- logo vector file
- text for each block (the yellow tasks on the canvas)
- B2B details: regions, volumes, vehicle types
- photos and short descriptions of the largest projects
- vacancies: title, duties, requirements, workload, pay
- the link to the daily report system
- the office address
- domain, DNS and e-mail access at Starflix
