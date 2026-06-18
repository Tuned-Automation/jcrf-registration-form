# JCRF Registration Form

The team-registration form embedded on the Junior Community Rugby Festivals
Squarespace site. It's hosted here once and loaded onto every festival page via
[jsDelivr](https://www.jsdelivr.com/), so a single edit here updates all pages.

## Files

| File | Role |
| --- | --- |
| `sq-rugby-registration-form.js` | **The hosted file** that pages load. Auto-generated — don't hand-edit. |
| `sq-rugby-registration-form.html` | The editable **source** (and a standalone local preview). |
| `build.js` | Regenerates the `.js` bundle from the `.html`. Run `node build.js`. |

## How it's wired up

Each Squarespace page's **Page Header Code Injection** carries just two lines —
the page's section ID, plus the shared link:

```html
<script>window.SQ_RUGBY_FORM_CONFIG = { targetSectionId: "THIS_PAGE_SECTION_ID" };</script>
<script src="https://cdn.jsdelivr.net/gh/Tuned-Automation/jcrf-registration-form@main/sq-rugby-registration-form.js"></script>
```

Everything else (styling, logic, Make.com/Airtable endpoints, fallback options)
lives inside the hosted `.js`.

### Per-page header blocks

Paste the matching block into each festival page (Page Settings → Advanced →
Page Header Code Injection). Only the section ID differs between pages.

| Festival | Section ID |
| --- | --- |
| Gisborne | `69a24f61ecb2f10afca89643` |
| Harbour | `698fa5cfb3641a103f32acc5` |
| Wellington | `69a252d01e78662f87f27042` |
| Canterbury | `69a2461bc45b7b6c9c8665fc` |
| Bay of Plenty | `69a25414c49a460051a9a966` |
| Counties | `69a2555b21b61a184af0d076` |
| Hawke's Bay | `69a2570fb1ea275054d57a36` |
| Waikato | `69a25802e0d3fc5bec87683c` |
| Girls only | `69a258841dd62e1334fffc36` |

## Updating the form

1. Edit `sq-rugby-registration-form.html`.
2. `node build.js` to regenerate `sq-rugby-registration-form.js`.
3. Commit and push to `main`.
4. **Purge the jsDelivr cache** so the change goes live within ~minutes:
   ```
   https://purge.jsdelivr.net/gh/Tuned-Automation/jcrf-registration-form@main/sq-rugby-registration-form.js
   ```
   (Open it in a browser or `curl` it.) Without this, jsDelivr can keep serving
   the previous copy for a while.

The pages themselves never need touching again once the two lines are in place.
