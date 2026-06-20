# Oliver Mesic — Recruiting Site

A single static `index.html` recruiting page for a HS kicker/punter. No build step, no framework — open the file or host it anywhere.

## Everything lives in one config block

Open `index.html` and find the `<script>` block near the top (marked **CONFIG**). All of Oliver's data and the video list are there.

### Add a highlight video to the gallery
Append one entry to the `GALLERY` array:
```js
const GALLERY = [
  { id: "-HE5mQYDSqo", title: "Punting Highlights", date: "2026 Season" },
  { id: "NEW_VIDEO_ID", title: "Long FG Compilation", date: "Fall 2026" }  // <- new line
];
```
The `id` is the part after `youtu.be/` or `watch?v=` in the YouTube URL.

### Swap the hero (primary) video
The hero is an **Instagram embed**. To change it, open the reel/post on Instagram → **⋯ → Embed → Copy embed code**, then replace the `<blockquote class="instagram-media">…</blockquote>` inside the `.ig-embed` div in the **PRIMARY HIGHLIGHT VIDEO** section. The `embed.js` script at the bottom of the file renders it automatically — no other change needed.

### Update a stat or profile field
Stats live in the **KEY STATS** and **ATHLETIC PROFILE** sections of the HTML — edit the number in place. Athlete contact details are in the `ATHLETE` config object and the **CONTACT** section.

### Swap the photo
The hero currently leads with the video. To add an action photo, drop an `<img>` into the `.hero` block in the HTML.

## Open `[TODO]` items
Search the file for `[TODO` — each is a clearly marked placeholder (Hudl link, coach contact, social links, additional gallery videos, awards).

## Hosting (free)
Drag-and-drop `index.html` to **tiiny.host** or **Netlify Drop**, or push to **GitHub Pages**. The result is a link to drop in coach emails and social bios.

## Design notes
- Palette: ink `#0f0f0e`, off-white `#fafaf8`, gold accent `#c9a84c`.
- Videos load on click (fast page load) via privacy-enhanced `youtube-nocookie.com` embeds.
- Mobile-first, accessible (semantic sections, keyboard focus, reduced-motion respected). No autoplay-with-sound.
