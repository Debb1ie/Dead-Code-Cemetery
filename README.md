# Dead Code Cemetery

A single-file browser application for commemorating deprecated, deleted, and forsaken code. Built for developers who believe every function deserves a proper farewell.

---

## Overview

Dead Code Cemetery is a dark-themed, self-contained HTML application that lets you create memorial headstones for dead code — functions, variables, stylesheets, entire modules — anything that once ran and no longer does. Each burial is stored locally in the browser and persists across sessions.

The project has no build step, no dependencies, and no server. Open the HTML file and it works.

---

## Features

### Burial Form
- Enter the name of the deceased function, variable, or file
- Select the programming language or technology
- Record the year it was written
- Choose a cause of death from a predefined list of common code fatalities
- Optionally paste a code snippet into the tomb
- Optionally write a eulogy describing what the code did and why it mattered
- Generate a randomized epitaph, or click repeatedly until one fits

### Cemetery Grounds
- All buried code is displayed as headstone cards in a responsive grid
- Each headstone shows the language, name, lifespan, cause of death, and epitaph
- Cards animate upward when rendered
- Hover reveals a ghost indicator
- Click any headstone to open the full memorial modal

### Memorial Modal
- Displays the complete record for a buried piece of code
- Shows the code snippet in a styled tomb block if one was provided
- Shows the eulogy if one was written
- Allows visitors to pay respects via an R.I.P. button, which increments a per-grave counter

### Statistics Bar
- Total souls buried
- Total lines of code at rest (counted from snippets)
- Year of the oldest relic in the cemetery
- Total R.I.P. respects paid across all graves

### Filtering
- Filter headstones by programming language
- Chip buttons generated dynamically based on languages present in the cemetery

---

## Cause of Death Options

| Cause | Icon |
|---|---|
| Deprecated by framework update | -- |
| Replaced by 3rd-party library | -- |
| Business requirements changed | -- |
| Rewrote entire app from scratch | -- |
| Performance issues | -- |
| Security vulnerability | -- |
| It never actually worked | -- |
| Too clever to maintain | -- |
| Abandoned side project | -- |
| Merge conflict casualty | -- |
| The client said "no" | -- |
| Spaghetti beyond repair | -- |
| AI wrote it better | -- |
| Unknown / Natural causes | -- |

---

## Supported Languages

JavaScript, TypeScript, Python, CSS, PHP, Java, C++, Ruby, SQL, Bash, Rust, Go, and an "unknown" option for relics of indeterminate origin.

---

## Usage

### Getting Started

Download or clone the repository and open `index.html` in any modern browser. No installation required.

```
git clone https://github.com/yourname/dead-code-cemetery
cd dead-code-cemetery
open index.html
```

### Burying Code

1. Fill in the function or variable name in the burial form at the top of the page
2. Select the language and cause of death
3. Optionally paste a snippet and write a eulogy
4. Click the epitaph area to generate a randomized inscription
5. Click **Lay to Rest** — the grave appears in the cemetery below

### Paying Respects

Click any headstone to open the memorial modal. Click the **Pay Respects** button to increment the R.I.P. counter for that grave. The count persists across sessions.

### Filtering

Use the language filter chips above the cemetery grid to narrow the view to a specific technology.

---

## Data Storage

All data is stored in `localStorage` under two keys:

| Key | Contents |
|---|---|
| `deadCodeGraves` | JSON array of all grave objects |
| `deadCodeRips` | Integer total of all R.I.P. respects paid |

### Grave Object Schema

```json
{
  "id": 1713000000000,
  "name": "calculateTax_v3_FINAL",
  "lang": "JavaScript",
  "year": "2019",
  "cause": "Rewrote entire app from scratch",
  "snippet": "function calculateTax_v3_FINAL(amount) { ... }",
  "story": "Four years of edge cases and regional tax rules...",
  "epitaph": "It worked on my machine.",
  "rips": 3,
  "buriedAt": "April 17, 2026",
  "lines": 12
}
```

`id` is a Unix timestamp in milliseconds. `lines` is calculated from newline count in the snippet field.

---

## Seeded Demo Data

On first load, if `localStorage` is empty, four example graves are created automatically:

- `getUserData_v2_FINAL_USE_THIS` — JavaScript, 2018, SQL injection and all
- `$.ajax_everywhere.js` — JavaScript, 2014, a jQuery eulogy
- `calculate_shipping_v3_NEW` — Python, 2020, business requirements claimed it
- `hack_fix_modal_css.css` — CSS, 2022, `margin-top: -47px !important` with a DO NOT REMOVE comment

These can be cleared by running `localStorage.clear()` in the browser console and refreshing.

---

## Clearing the Cemetery

To remove all graves and start fresh:

```javascript
localStorage.removeItem('deadCodeGraves');
localStorage.removeItem('deadCodeRips');
location.reload();
```

---

## Technical Notes

### Architecture

The entire application is a single HTML file with no external dependencies at runtime. Fonts are loaded from Google Fonts via a `<link>` tag and require an internet connection on first load; subsequent visits use the browser cache.

### Fonts Used

- `UnifrakturMaguntia` — title and modal headings
- `Special Elite` — body text, epitaphs, buttons
- `IBM Plex Mono` — labels, metadata, code snippets, stats

### Browser Compatibility

Requires a modern browser with support for CSS custom properties, CSS Grid, `localStorage`, and ES6. Tested in Chrome, Firefox, and Safari.

### Cursor

The application sets a custom coffin cursor via a base64-encoded inline SVG data URI. This falls back to the default cursor in environments that do not support custom cursors.

---

## Customization

### Adding Epitaphs

The `EPITAPHS` array near the top of the script block contains all possible generated inscriptions. Add or remove strings freely. The generator also produces a name-specific epitaph if the function name contains `FINAL`, `v2`, or `v3`.

### Adding Languages

Add `<option>` elements to the `#codeLang` select in the form. No other changes required.

### Adding Causes of Death

Add `<option>` elements to the `#codeCause` select, then add a corresponding entry in the `CAUSE_ICONS` object mapping the cause string to a display icon.

### Theming

CSS custom properties are defined in `:root` at the top of the stylesheet:

```css
--dirt: #2a1f14;
--soil: #3d2b1a;
--moss: #4a5e3a;
--stone: #8a8a7e;
--stone-light: #b0afa3;
--parchment: #d4c9a8;
--moonlight: #c8d8b8;
```

Adjusting these values will propagate through the entire UI.

---

## File Structure

```
dead-code-cemetery/
  index.html     -- the entire application
  README.md      -- this file
```

---

## License

MIT. Bury freely. Fork respectfully. All deprecated code deserves dignity.

---

*Every function served. Every loop ran. Every variable held its value.*
