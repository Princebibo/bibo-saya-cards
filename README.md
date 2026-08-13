# Bibo Saya Studio — NFC cards & tags

Product site for blank NFC hardware: matte black cards and white tags, sold
to businesses for access control, payment systems, member badges and
inventory.

French by default with an English toggle. Lead generation only — no
checkout; quantity and price are agreed by email.

## Run it

```bash
npx --yes serve@14 .
```

Serve over `http://`, not `file://` — a `file://` origin sends `Origin: null`,
which form providers can reject, making a working form look broken.

## Notes

- **Video**: two 10s clips in `media/`. Sources attach only when the clip is
  near the viewport, so ~4.8 MB is not pulled on load. Autoplay needs
  `muted` + `playsinline`; every clip has a pause control because WCAG 2.2.2
  requires one for anything moving longer than five seconds. Visitors who
  request reduced motion get a paused first frame.
- **Reveals** run on a plain scroll listener, not `requestAnimationFrame` or
  `IntersectionObserver` — neither is reliable in every embedded viewer, and
  content must never depend on them to be visible. A timer forces anything
  still hidden into view as a last resort.
- **Form** posts to the same Formspree form as the review-card site, tagged
  with a `source` field so the two lead streams stay distinguishable.
- **i18n**: French is the source of truth in the HTML; English lives in a
  dictionary. `<option value>` stays English in both languages so submitted
  data is stable.

## Licence

MIT
