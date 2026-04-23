test八股： https://tangerine-tarsier-adf28d.netlify.app/

## Interview Question Bank

A static, single-page study aid that loads every question from `faq.json` and lets you drill into them with filters, favorites, and a timed-mock workflow. All data is read client-side from one JSON file; progress (favorites and 熟/不熟 marks) is stored in the browser's `localStorage`.

### Features

**Search by keyword.** The rounded search bar at the top matches against both questions and answer text, so you can find items by concept rather than exact wording.

**Categorized dropdown.** The "Select a category" dropdown is pre-sorted into the four tags present in the data: **ANGULAR**, **BQ**, **MERN**, and **JAVA**. Picking one narrows the list down to that tag immediately.

**Top Questions.** The blue **TOP QUESTIONS** button filters to items flagged `isTop: true` in `faq.json` — the highest-priority interview questions. Click it again to turn the filter off. Combine it with a category to see that category's top picks.

**Expand All.** The grey **EXPAND ALL** button opens every answer on the page at once (and toggles back to "Collapse All"). Useful when you want a reading pass instead of clicking each question.

**Mock Mode.** The teal **MOCK MODE** button requires a category first, then randomly draws **25 questions** from that tag for a quick mock-interview set. A banner appears at the top with two controls: **Reshuffle** to draw a fresh 25 from the same tag, or **Exit Mock Mode** to return to the full list. Changing the category or the Top Questions filter automatically exits Mock Mode so the draw never gets out of sync with what you're looking at.

**Favorites and marks.** Each answer has ⭐ to save and ✔ 熟 / ❌ 不熟 to mark how comfortable you feel. The **All status** dropdown lets you filter down to just favorites, just "熟", or just "不熟". Everything persists across page reloads via `localStorage` under the keys `fav` and `stats`.

### Files

- `index.html` — the whole UI (HTML + CSS + JS in one file, no build step).
- `faq.json` — the data source; each entry has `id`, `question`, `answer` (HTML), `category`, `keyword`, `frequency`, and `isTop`.
- `README.md` — this file.

### Running locally

Because `index.html` uses `fetch('faq.json')`, serve the folder over HTTP rather than opening the file directly:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just visit the deployed site above.

### Adding or editing questions

Edit `faq.json` directly. To promote a question into the TOP QUESTIONS view, set `"isTop": true`. To add a new category, add entries with a new `category` value and add a matching `<option>` in the category dropdown in `index.html`.
