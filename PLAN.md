# PLAN.md — Oliver Mesic Recruiting Site (v2)

## What we're building

A fast, **single-page recruiting site** for a high school kicker/punter that a college special-teams coach can scan in ten seconds and immediately get: can this kid kick, is it real, and how do I reach him. Everything else is secondary.

This is the link Oliver drops in coach emails, DMs, and social bios. It complements — does not replace — his Hudl/film profiles and links out to them.

**Design goal for this build:** make it read like an **editorial press kit, not a web template.** Sparse but crafted. The previous version was clean but boring; this version steps up the typography and layout so it looks professional without being flashy.

---

## Who it's for

A college special-teams coordinator with a full inbox who spends ~10 seconds deciding whether to keep watching. Film first, numbers verifiable, contact one click away. No autoplay, no music, no clutter, no marketing language.

**Important context:** Oliver is an **upcoming junior (Class of 2028)**. Active recruiting is still ~a year out. The job of this site right now is to **build a credible frame** that new film and game numbers drop into over time — not to oversell where he is today. An honest early-stage site beats an inflated one. Build everything to be updated with one-line edits.

---

## The athlete (real data — use throughout)

| Field | Value |
|---|---|
| Name | Oliver Mesic |
| Position | Kicker / Punter |
| Class | 2028 (upcoming junior) |
| High school | Del Norte High School |
| Location | San Diego, CA |
| Height | 5'10" |
| Weight | 145 lbs |
| GPA | 4.07 (weighted) |
| Best FG | 53 yards — **practice, charted by Nick Novak** |
| Kickoffs | Consistent touchbacks (practice) |
| Punt hang time | 4.5 sec (practice) |
| Kicking coach | **Nick Novak — 12-yr NFL kicker (ongoing trainer)** |
| Athlete phone | 858-242-7999 |
| Athlete email | oliverkhai@gmail.com |
| Head coach | Nick Barnett — *contact TBD* |

**Numbers honesty rule:** every stat is labeled with its context and date — "practice," "game," "charted by Novak [month]." Unlabeled numbers read as inflated and a coach discounts the whole section. Labeled honestly, the same numbers build trust. Never present a practice number as if it were a game number.

**Placeholders — leave clearly marked `[TODO: ...]`:**
- Primary YouTube highlight video ID
- Additional gallery video IDs + titles + dates
- Hudl / film profile link
- Head coach contact
- Confirmation that Novak is OK being listed as a reference (get his nod before publishing his contact)
- Action photo / headshot
- Game field-goal numbers (coming as the season produces them)

---

## Page structure — FOUR sections, in this order (order is the strategy)

Cut down from the old seven. Removed: standalone athletic-profile block, empty awards section, marketing tags. They added length, not credibility.

### 1. Hero = name + film (do NOT separate them)
The reel is the first impression, not a thing you click to reach. Combine the hero and the primary video.
- Name (large serif display).
- Meta line, plain and factual: **"Kicker / Punter · Class of 2028 · Del Norte HS · San Diego, CA · 5'10\" / 145"**
- Lead with the **film**, not a number — the strong *game* numbers are still coming, so the film and the source carry the hero.
- Credential line under the reel: **"Trained by Nick Novak · 12-yr NFL kicker."** This is a recognizable name and a credibility shortcut — surface it, don't bury it. State it plainly, don't oversell.
- Primary video is a full-width responsive 16:9 embed.
- Do NOT frame the grad year apologetically ("2 more years," "still developing"). Just state "Class of 2028." The coach does the timeline math; a plain grad year reads as confident.

### 2. Measurables
- The verifiable leg numbers, each with context + date: FG 53 (practice, charted by Novak), consistent touchbacks, 4.5s punt hang.
- "Data sheet" presentation: hairline-ruled cells, big serif numbers, small uppercase labels, tabular figures that align in columns.
- Built so a new stat = one new row/array entry. Game numbers slot in here as they come and become the lead once they exist.

### 3. Academics
- GPA 4.07 — **one clean line**, not its own headed section. Real asset for D1 scholarship math, but it's a filter a coach applies later, not a ten-second hook. Keep it visible, keep it small.

### 4. Contact
- Athlete (phone + email), Coach Barnett, and **Nick Novak as kicking-coach reference** — listed only once Novak confirms he's OK with it. A contact field implies "call this person," so the relationship must be real (it is — ongoing trainer) and consented.
- Links out to Hudl / film profiles. One click to everything.

---

## The one interactive feature

**A click-to-load, expanding film gallery** below the measurables — additional highlight videos as labeled thumbnails (title + date) that load the iframe only on click and expand inline / in a lightbox. This is the *only* interactive feature that earns its place: it serves the actual job (more film, fast load) and is built to grow.

**Explicitly rejected as gimmicks:** stat-hover tooltips (no coach taps them on mobile), smooth-scroll nav (pointless on a single short page), flashy transitions. Don't build them.

---

## Design direction — "editorial press kit, not web template"

The old version was clean but boring. Boring = default fonts at similar sizes with even spacing. The fix is craft, not flash. In order of impact:

1. **Brutal typographic contrast.** Biggest lever. Name enormous (~64px+), labels tiny (~11px uppercase, letter-spaced). Dramatic scale jumps read "designed"; everything at 16–24px reads boring. Big serif numbers for stats, small-caps labels above them.
2. **Drop the default Georgia/Times stack for one real serif webfont** for the name and stat numbers (e.g. Fraunces, Newsreader, or Spectral), kept on a clean system sans for body/labels. This single move kills "boring" fastest and stays professional. Load one font only — keep it fast.
3. **Left-aligned, asymmetric editorial layout** on a baseline grid with generous, uneven whitespace. Centered-everything reads amateur; this reads like a press kit.
4. **Tabular numbers + hairline rules.** `font-variant-numeric: tabular-nums` so figures align; 1px hairline rules between cells, not boxes or cards. The Sailer/Kohl's "data sheet" look that signals seriousness.
5. **One accent, used twice.** Gold (`#c9a84c`) appears maybe twice on the whole page (position tag + one rule). Restraint looks expensive; a sprinkled accent looks like a school project.
6. **Quiet motion only.** Subtle fade-and-rise as sections enter the viewport; respect `prefers-reduced-motion`. Motion felt, not noticed. No bounce, no slide-ins.

**Palette:** near-black ink (`#0f0f0e`), warm off-white background (`#fafaf8`), single gold accent (`#c9a84c`) used sparingly, grays for structure.

**Feel, in three words:** Sparse. Confident. Verifiable. Every number is something a coach could look up.

### Hard rules (what coaches hate)
- No autoplay with sound, no background music.
- No flashy transitions, no slow-motion padding, no walls of text.
- Mobile-first and fast — most coach traffic is mobile.
- Film and contact never buried.
- Every claim specific and verifiable ("FG 53, practice, charted by Novak"), never vague ("powerful leg").
- No apologetic "still developing / 2 years out" language anywhere.

---

## Tech approach (for Claude Code)

- **Single static `index.html`** with embedded CSS and minimal JS (only for the film gallery). No build step, no framework — trivially hostable and editable.
- **One webfont** loaded for the display serif (preconnect + `font-display: swap`); system sans for the rest.
- **YouTube embeds** via privacy-enhanced `youtube-nocookie.com`. Primary video = full-width responsive 16:9. Gallery = `https://img.youtube.com/vi/<ID>/hqdefault.jpg` thumbnails that load the iframe only on click (fast page load).
- **Responsive** down to ~360px. CSS Grid for stat cells and the gallery; collapse to 1–2 columns on mobile.
- **Accessibility:** semantic sections with `aria-label`s, visible keyboard focus, alt text, `prefers-reduced-motion` respected.
- **Config block at top of file** (a single JS object / JSON) holding ALL of Oliver's data and the video list, so updating a stat or adding a video is a one-line edit, not a hunt through markup.
- **Hostable free** on tiiny.host, GitHub Pages, Netlify, or Google Sites.

---

## Build tasks (suggested order for Claude Code)

1. Scaffold `index.html` with the four-section skeleton and a config block populated with the real data above.
2. Build the **hero**: name (large serif), factual meta line, primary 16:9 YouTube embed `[TODO: video ID]`, Novak credential line.
3. Build the **measurables** data sheet: hairline cells, tabular serif numbers, every stat labeled with context + date. Built for one-line additions.
4. Build the **academics** one-liner (GPA prominent but not headed-section-sized).
5. Build the **film gallery**: click-to-load thumbnails from a JS array of `{id, title, date}`, inline expand / lightbox. Adding a video = one array entry.
6. Build **contact**: athlete filled in; Coach Barnett + Novak (reference, pending his OK) + Hudl/film links as `[TODO]`.
7. Apply the **design language**: type scale, serif webfont, left-aligned grid, hairline rules, tabular nums, single accent, quiet section-entry motion.
8. Pass for **responsive + accessibility + load speed**; verify all `[TODO]`s are obvious.
9. Update `README.md`: how to add a video, update/label a stat, swap the photo, list a reference, and where to host.

---

## Out of scope (later stages)
- Awards / camp-results section — add the day a real honor exists, not before. Empty placeholder sections hurt credibility.
- Attending a Sailer/Kohl's ranking camp and adding an earned star rating + charting block.
- Creating/maintaining the Hudl/film profiles the site links to.
- Any backend, CMS, or contact form — keep it static.

---

## Definition of done
- Opens fast on mobile; name and film visible without scrolling.
- Reads like an editorial press kit, not a template — strong type contrast, real serif, hairline data sheet.
- Primary video plays in one click; gallery videos load on click, clearly labeled.
- Every stat is honestly labeled (practice/game + date); no inflated or vague claims.
- Novak surfaced as a credential in the hero and (pending his OK) a reference in contact.
- All real data in place; every missing item a clearly marked `[TODO]`.
- Oliver can add a video or update a stat by editing one line of the config block.
