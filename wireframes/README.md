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
- The wireframe artboards have one toggle (Tweaks → Anotācijas): `showSpecs` shows the blue component chips. Turn it off to present a clean skeleton.
- The canvas shows a page board at most 8000 px tall and gives the page a viewport as tall as the board. Every page is kept under 8000 px at 1440 wide, and no section uses `vh` units (a `60vh` block would grow with the board).
- There is no section of completed project examples anywhere (dropped on 19.10). Pārvākšanās keeps its experience block (Layout 216: offices up to 300 workplaces).

## Sitemap

| Page | Slug | Sections (Relume) |
| --- | --- | --- |
| Sākums | `/` | Navbar 1 · Header 1 · Layout 251 · Stats 13 · Layout 231 · Layout 645 (`#par-mums`) · Testimonial 17 · CTA 1 · FAQ 3 · Contact 5 (`#piedavajums`) · Footer 3 |
| Pakalpojumi uzņēmumiem | `/pakalpojumi-uznemumiem` | Navbar 1 · Header 50 · Stats 8 · Layout 42 · Layout 623 · Layout 231 · Layout 647 · Testimonial 17 · FAQ 3 · Contact 6 (`#pieprasijums`) · Footer 3 |
| Pārvākšanās | `/parvaksanas` | Navbar 1 · Header 1 · Layout 216 · Layout 629 · Layout 671 · Timeline 17 · Testimonial 17 · FAQ 3 · Multi Form 17 (`#pieteikums`) · Banner 3 · Footer 3 |
| Darbs pie mums | `/darbs` | Navbar 1 · Header 5 · Layout 620 · Layout 645 · Career 12 (`#vakances`) · Layout 231 · Testimonial 17 · FAQ 3 · Contact 9 (`#pieteikties`) · Banner 3 · Footer 3 |
| Kontakti | `/kontakti` | Navbar 1 · Contact 14 · Layout 232 · Contact 5 · Footer 3 |
| Darbinieku sadaļa (hidden) | `/darbinieki` | Links 1 only, with no Navbar or Footer: one button that opens the daily report. Set `noindex, nofollow` and leave it out of the menu and of `sitemap.xml` (see below). |

Navbar: Pakalpojumi ▾ (Kurjerpasts uzņēmumiem · Pārvākšanās · Transporta noma) · Par mums · Darbs pie mums · Kontakti, plus one primary button. The button's text and link are component properties, so each page points it at its own form:

| Page | Navbar button | Goes to |
| --- | --- | --- |
| Sākums, Kontakti | Saņemt piedāvājumu | `/#piedavajums` |
| Pakalpojumi uzņēmumiem | Pieprasīt piedāvājumu | `#pieprasijums` |
| Pārvākšanās | Saņemt cenu | `#pieteikums` |
| Darbs pie mums | Pieteikties darbam | `#pieteikties` |

Small deviations from the stock Relume components (all noted on the canvas):

- Layout 251: each service card has its own action link.
- Layout 231: used for the 3-step "how it works", with "1. solis" as the tagline.
- Timeline 17: step numbers instead of dates, 4 items.
- Banner 3: fixed to the bottom of the screen on phones only (under 768px), shown after the hero.
- Contact 5 on `/`: a service radio (Kurjerpasts uzņēmumam / Pārvākšanās / Transports ar šoferi) in place of a plain contact form.
- Contact 5 on `/kontakti`: an added radio "Uzņēmums / Privātpersona" and a topic select.
- Multi Form 17: Postline's 4 steps (below) replace the stock fields.

## Conversion logic

The pages follow the landing-page-design skill (github.com/elayadesign/ai-design-skills), Part A: one offer, one audience and one primary action per page.

| Page | Audience | One primary action | Proof next to it | Objection handling |
| --- | --- | --- | --- | --- |
| Sākums | All three: companies, movers, drivers | Saņemt piedāvājumu (form with a service choice). Drivers get a text link to vacancies, not a competing button. | 300-workplace move under the button; Stats 13 with 2011 / ~20 / ~20 / 300 right after the services | 6-question FAQ, "Pieprasījums neuzliek saistības" under the form |
| Pakalpojumi uzņēmumiem | Companies with regular shipments, tender organisers | Pieprasīt piedāvājumu | Stats 8 straight after the hero, company testimonials just before the form | Problem → solution section (Layout 42), 7-question FAQ, private parcels filtered out |
| Pārvākšanās | Offices, archives, small businesses, homes | Saņemt pārvākšanās cenu (4-step form) | The 300-workplace project moved up to second place | FAQ moved above the form (high-friction offer), "no obligation" next to the button, sticky mobile button |
| Darbs pie mums | Drivers arriving from agency job ads on a phone | Pieteikties darbam | Team since 2011, team quotes | Shorter form (one name field, experience optional, CV optional), 6 driver questions, sticky mobile button |
| Kontakti | Anyone | Call or write | Company details | Three shortcuts to the right form (Layout 232) |

Rules applied everywhere:

- The last section of every page repeats the first action with the same words.
- Button labels say what happens ("Saņemt pārvākšanās cenu", "Nosūtīt pieteikumu"), never "Uzzināt vairāk" or "Nosūtīt".
- Every page has a 3- or 4-step "how it works".
- Every figure on the page is a real one from the brief or the calls. Testimonials stay as placeholders until GoHighLevel collects real ones.
- The "Pieprasījums neuzliek saistības" line is the risk reversal. It only says that a request is not an order, so it needs no extra promise from Artis.

## Forms → GoHighLevel

| Form | Where | Fields |
| --- | --- | --- |
| Pieprasījums (Contact 5) | `/#piedavajums` | pakalpojums (radio: Kurjerpasts uzņēmumam / Pārvākšanās / Transports ar šoferi), vārds, tālrunis, e-pasts, īsi par darbu. The service choice decides the GHL pipeline. |
| Pārvākšanās pieteikums (Multi Form 17) | `/parvaksanas#pieteikums` | 1) Privātpersona / Uzņēmums · 2) no adreses, uz adresi, vēlamais datums · 3) apjoms un apraksts, stāvs un lifts abās vietās, foto augšupielāde · 4) vārds, tālrunis, e-pasts (+ uzņēmums). After sending: automatic confirmation to the client. |
| B2B pieprasījums (Contact 6) | `/pakalpojumi-uznemumiem#pieprasijums` | uzņēmums, kontaktpersona, e-pasts, tālrunis, pakalpojums (select), aptuvenais apjoms (radio), papildu informācija |
| Kontaktforma (Contact 5) | `/kontakti` | vārds, e-pasts, Uzņēmums / Privātpersona, tēma, ziņa |
| Darba pieteikums (Contact 9) | `/darbs#pieteikties` | vārds un uzvārds, tālrunis, vakance, autovadītāja apliecība, pieredze (optional), CV (optional) |

There is no price calculator (removed on 29.09.). Testimonial 17 reads from a CMS collection fed by GHL review requests and stays hidden until the first reviews come in.

## Design concepts (homepage)

Three different directions for the same homepage. Each keeps the orange "P" logo (#F05223 with the white line-drawn P) as it is, takes one more thing from the current postline.lv, and follows the homepage order without the projects section:

1. Nav and hero
2. Services
3. Numbers
4. How it works
5. About
6. Testimonials
7. Careers
8. FAQ
9. Quote form
10. Footer

How they were made:

- **taste-skill** (github.com/leonxlnx/taste-skill) dealt the directions: *Loud and flat* (seed 11), *The printed annual* (seed 37) and *One motif* (seed 23).
- **tastemaker** (github.com/codeswithroh/tastemaker) set the hero rules (one promise, one action, one visual) and the copy rules (no template headlines, no em dashes).
- **frontend-design** (github.com/anthropics/skills) supplied the plan-then-critique pass.
- **UI/UX Pro Max** (github.com/nextlevelbuilder/ui-ux-pro-max-skill) drove the 19.10 restructure:
  - Hierarchy through size, weight, spacing and contrast.
  - One header pattern per section (label, H2, short intro) and one 1280 px container.
  - Equal cards with the same internal order.
  - Numbered step indicators for the process.
  - One primary button per screen.
  - Text contrast of at least 4.5:1 and touch targets of at least 44 px.
  - Its "Corporate Trust" pairing (body font Source Sans 3) replaced the serif in B.

| | A — Plakāts (bold) | B — Gada pārskats (elevated) | C — Maršruts (modern) |
| --- | --- | --- | --- |
| Idea | A street poster: flat fields of colour, heavy uppercase type, tilted photo stickers | A printed annual report: greyscale photos, black ink, Postline orange as the only colour, square tiles with 8 px gaps | Clean and modern; the line of the Postline "P" returns as the footer mark |
| Taken from postline.lv | Signal orange #F05223 as the whole hero field | Raleway, the current site's typeface | Blue grey #263238 and coral #FF8A65 from the old site |
| Hero | Three service chips, "Kurjerpasts un pārvākšana", subhead, black button, 300-workplace proof line, van photo as a sticker | Tile board: "Postline" with what it does and the button, two photos, and an index of the three services as link tiles | "Mēs to aizvedīsim." over four equal tabs (three services + jobs); every tab opens a panel with the same structure |
| Services | Three equal cards (lime, orange, white): photo, title, "Kam", three bullets, link | Three aligned columns: photo, title, "Kam", "Iekļauts" list, link | Inside the hero tabs |
| Numbers | Giant "300" with a "Ko tas nozīmē" panel and four stats below | Ink section: intro on the left, 2×2 stat tiles on the right, 300 in orange | Four equal stat cards, 300 in coral |
| How it works | Three coloured panels with step numbers and time labels | Horizontal stepper with orange numbered circles | Horizontal stepper with numbered circles on a coral line |
| About | Paragraph with highlighted facts | Photo with a "Kopš 2011. gada" badge, lead text and three fact tiles | Paragraph with small photos inside the words, three fact cards |
| Testimonials | Three torn paper slips | One featured quote and two smaller ones | Three equal cards, the middle one dark |
| Careers | Benefits checklist and driver photo sticker | Photo, "Ko piedāvājam" and "Kā pieteikties" in three columns | Pale coral panel with photo and three benefit cards |
| Quote form | White form panel on orange | Inverted black closing page | Clip-out coupon |
| Colours | #F05223, sky #4DB3FF, lime #C5F53D, near-black #161615, text #111111 | white, tone #F1F1EE, ink #121212, Postline orange | #263238, #37474F, #CFD8DC, #ECEFF1, coral #FF8A65, pale coral #FFE0D6 |
| Type | Unbounded 800 (uppercase display) + Onest | Raleway 500/600 + Source Sans 3 | Geist |
| Shapes | Square, panels edge to edge | Square tiles, 8 px gaps | 16 px radius, pill buttons |
| Height at 1440 | 7,201 px | 7,316 px | 6,718 px |

Contrast note: white text on #F05223 is only 3.5:1, so every orange or coral button uses dark text.

Motion is described rather than built into the canvas: hover lifts, tab changes and accordion openings, all respecting `prefers-reduced-motion`.

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
- text for each block (see the list below)
- B2B details: regions, volumes, vehicle types
- photos and short descriptions of the largest projects
- vacancies: title, duties, requirements, workload, pay
- the link to the daily report system
- the office address
- domain, DNS and e-mail access at Starflix

## Text tasks for Artis

What each block needs, in the order the sections appear on the page. Square brackets on the canvas mark the same gaps.

**Sākums**
- Header 1: check the headline and the one-line description (we can propose alternatives).
- Layout 251: 1–2 sentences per service, saying who it is for and what is included.
- Layout 645 (`#par-mums`): 3 values in one line each. Courier partners are mentioned only neutrally.
- FAQ 3: answers to the 6 questions, 1–3 sentences each.

**Pakalpojumi uzņēmumiem**
- Stats 8: 1–2 sentences on why companies choose Postline.
- Layout 42: 1–2 sentences on how the regular route and one contact work in practice.
- Layout 623: the 3 services for companies, 1–2 sentences each.
- Layout 647: regions, volumes, vehicle types and form of cooperation, 1 line each.
- FAQ 3: answers to the 7 questions.

**Pārvākšanās**
- Layout 216: 2 sentences on the largest projects (what, when, how fast) and photos from them.
- Layout 629: 1 sentence per client group.
- Layout 671: what is included in the price, what costs extra, and which vehicles are available.
- FAQ 3: answers to the 7 questions.

**Darbs pie mums**
- Layout 620: 1 sentence about working with the company vans.
- Layout 645: pay, schedule, place of work, training.
- Career 12: current vacancies with title, duties, requirements and workload.
- Testimonial 17: two short quotes from drivers or couriers, with the year they joined.
- FAQ 3: answers to the 6 driver questions.

Testimonials on Sākums, Pakalpojumi uzņēmumiem and Pārvākšanās need no text: GoHighLevel collects them automatically after each job.
