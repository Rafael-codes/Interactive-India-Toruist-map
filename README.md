# Nexus-India (summa.html)

Interactive India tourist planner that lets you explore Indian states/UTs via an SVG map.

## Features
- Click a highlighted region on the map to open a “Sector” panel.
- Displays curated **places** per region with a classification label.
- Filters:
  - **Zone type** (Coastal / Elevated / Mystic / Legacy)
  - **Budget** (Eco / Standard / Premium)
- Search by state/UT name.
- Hover tooltip shows the selected state name.

## How it works
- `statesData` maps SVG region ids (e.g. `IN-KA`) to:
  - `name`
  - `budget` (`low | medium | high`)
  - `type` (array like `['beach']`, `['hill']`, `['spiritual']`, `['historical']`)
  - `places[]` (name + type)
  - `img` (one of the `img*.avif` assets)
- Every `<path>` inside the embedded `<svg>` is treated as a clickable region.
- UI logic:
  - `showPlaces(code)` renders place cards inside `#placesList`
  - `applyFilters()` hides/shows regions and applies a highlight style
  - `searchStates()` filters regions by name as you type

## Folder / assets
- `summa.html` (single-file app)
- `img1.avif` … `img8.avif` (used by `statesData` entries)

## Usage
1. Open `summa.html` in a browser.
2. Optionally use:
   - **All Zones / Coastal / Elevated / Mystic / Legacy**
   - **Budget / Eco / Standard / Premium**
   - **Search** to locate a state
3. Click any visible region.
4. In the side panel, click **INITIATE SCAN** to open a Google Maps search for the selected place.

## Notes / limitations
- The SVG map is embedded directly in the HTML.
- `statesData` contains entries for many states/UTs; only ids present in `statesData` will respond to interactions.
- Filtering uses `data.type.includes(type)` and `data.budget === budget`.

## Tech stack
- HTML + inline CSS
- Vanilla JavaScript
- SVG for the map
- Google Fonts (Rajdhani)

