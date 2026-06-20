# plan.md — Oliver Mesic Recruiting Site

## What we're building

A fast, clean, **single-page recruiting website** for a high school kicker/punter that a college coach can scan in under 30 seconds and find everything they need: who Oliver is, his film, his numbers, his academics, and how to reach him.

This site is the polished landing page Oliver links in coach emails, DMs, and his social bios. It does **not** replace Hudl/NCSA/FieldLevel profiles — it complements them and links out to them.

**The new priority for this build:** a **primary embedded YouTube highlight video** front and center, plus a **gallery of additional YouTube highlight videos** (already posted on YouTube) below it.

---

## Who it's for

A D1 special teams coordinator with a full inbox who spends ~30 seconds deciding whether Oliver is worth a second look. Everything is built around that person. Video first, numbers scannable, contact one click away. No clutter, no fluff, no autoplay-with-sound.

---

## The athlete (real data — use throughout)

| Field | Value |
|---|---|
| Name | Oliver Mesic |
| Position | Kicker / Punter (dual-threat) |
| Class | 2028 |
| High school | Del Norte High School |
| Location | San Diego, CA |
| Height | 5'10" |
| Weight | 145 lbs |
| GPA | 4.07 (weighted) |
| Best field goal | 53 yards |
| Kickoffs | Consistent touchbacks |
| Punt hang time | 4.5 sec |
| Athlete phone | 858-242-7999 |
| Athlete email | oliverkhai@gmail.com |
| Head coach | Nick Barnett — *contact TBD* |

**Placeholders to leave clearly marked** (`[TODO: ...]`) until Oliver supplies them:
- Primary YouTube video URL/ID
- Gallery YouTube video URLs/IDs + titles + dates
- Hudl profile link
- Head coach phone/email
- Action photo / headshot
- Kicking-service star rating (once he attends a Sailer or Kohl's camp)

---

## Page structure (in this order — order matters to coaches)

1. **Hero** — name, "Kicker / Punter • Class of 2028," Del Norte HS / San Diego CA, height/weight, action photo, and a prominent "Watch film" button that jumps to the video. Once earned, a kicking-service star rating/ranking badge lives here too.
2. **Primary highlight video** — large embedded YouTube player. This is the single most important element on the page. Best kick should be in the first 5–10 seconds of the reel itself.
3. **Key stats** — scannable, charted-style numbers (the Kohl's-table lesson): kickoff (touchbacks), best FG (53 yds), punt hang time (4.5s), with "dual-threat" and "D1 baseline" tags. Built so new stats slot in easily.
4. **Video gallery** — responsive grid of additional YouTube highlight videos, each with a clear label and date (e.g., "2026 Season Reel," "Long FG Compilation," "Skills / Charting — June 2026"). Most impressive first. Thumbnails open the video inline (lightbox/modal) or expand in place.
5. **Athletic profile** — height, weight, grad year, GPA. Academics matter for D1 scholarship math — keep GPA visible.
6. **Awards / camp results** — placeholder section for all-state/all-conference honors and kicking-camp results as they come.
7. **Contact** — athlete (phone + email), head coach, and room for parent + kicking coach. Plus social links and links out to Hudl/NCSA. One click to everything.

---

## Design direction

Keep the editorial look we already designed — it reads as serious and uncluttered:

- **Palette:** near-black ink (`#0f0f0e`), warm off-white background (`#fafaf8`), a single gold accent (`#c9a84c`) used sparingly for position tag and highlights. Grays for structure.
- **Type:** a serif display face (Georgia/Times stack) for the name and stat numbers, clean sans-serif (system stack) for body and labels. Big numbers, small labels.
- **Layout:** hairline-ruled grid cells for stats (the "data block" feel from Chris Sailer / Kohl's profiles). Generous whitespace. Hard top rule under the header.
- **Feel, in three words:** **Sparse. Confident. Verifiable.** Every number should be something a coach can look up.

### Hard rules (from the research — what coaches hate)
- No autoplay with sound. No background music on the page.
- No flashy transitions, no slow-motion padding, no walls of text.
- Mobile-first and fast-loading — most coach traffic is mobile.
- Video and contact info must never be buried.
- Every claim is specific and verifiable ("consistent touchbacks," "53-yd FG"), never vague ("powerful leg").

---

## Tech approach (for Claude Code)

- **Single static `index.html`** with embedded CSS (and minimal JS only if needed for the gallery lightbox). No build step, no framework — it needs to be trivially hostable and editable.
- **YouTube embeds** via standard `iframe` (privacy-enhanced `youtube-nocookie.com` domain preferred). Primary video is a full-width responsive 16:9 embed. Gallery uses lightweight thumbnail → click-to-load (load the iframe only on click for fast page load; use `https://img.youtube.com/vi/<ID>/hqdefault.jpg` for thumbnails).
- **Responsive** down to ~360px. CSS Grid for stat cells and the video gallery; collapse to 1–2 columns on mobile.
- **Accessibility:** semantic sections with `aria-label`s, visible keyboard focus, alt text on images, respect `prefers-reduced-motion`.
- **Config block at top of file** (or a small `data.js`/JSON object) holding all of Oliver's data and the video list, so updating stats or adding a video is a one-line edit, not a hunt through markup.
- **Hostable free** on tiiny.host, GitHub Pages, Netlify, or Google Sites. The output is a link Oliver drops in every coach email and his social bios.

---

## Build tasks (suggested order for Claude Code)

1. Scaffold `index.html` with the section skeleton and the data/config block populated with Oliver's real data above.
2. Build the **hero** (name, position tag, meta line, photo placeholder, "Watch film" button).
3. Build the **primary YouTube embed** (responsive 16:9, `[TODO: video ID]`).
4. Build the **key stats** grid (touchbacks / 53-yd FG / 4.5s punt hang, with tags).
5. Build the **video gallery** (click-to-load thumbnails from a JS array of `{id, title, date}`; lightbox or inline expand). Wire it so adding a video = adding one array entry.
6. Build **athletic profile** + **academics** (GPA prominent).
7. Build **awards/camp results** placeholder section.
8. Build **contact** (athlete filled in; coach/parent/kicking-coach + Hudl/NCSA links as placeholders) + social links.
9. Pass for **responsive + accessibility + load speed**; verify all `[TODO]` placeholders are obvious.
10. Write a short `README.md`: how to add a video, update a stat, swap the photo, and where to host.

---

## Out of scope for this build (later stages)
- Attending a Chris Sailer / Kohl's ranking camp and adding the earned star rating/ranking + a charting-table stats block.
- Creating/maintaining the Hudl, NCSA, and FieldLevel profiles the site links to.
- Any backend, CMS, or contact form — keep it static for now.

---

## Definition of done
- Opens fast on mobile, name and film visible without scrolling.
- Primary video plays in one click; gallery videos load on click and are clearly labeled.
- All of Oliver's real data is in place; every missing item is a clearly marked `[TODO]`.
- A coach can find the film, the numbers, and how to contact Oliver without thinking.
- Oliver can add a new highlight video or update a stat by editing one line.
