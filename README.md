# trains india

A terminal-style Indian train tracker. One HTML file, no build step, no server.

Search any train, open it, and see live running status as a vertical station line with a blinking dot at the train's current position, plus a text-character map of the states it passes through.

## Features

- **Local search:** about 14,000 trains (including Vande Bharat) are built into the file. Search by train number, name, station name or station code. Searching never uses an API call.
- **Live status:** one API call when you open a train, from [RailRadar](https://railradar.in). Results are cached for 5 minutes and there is no auto-refresh, so you spend calls only when you choose to.
- **Backup source:** if RailRadar fails, the page can fall back to [RailCore](https://railcore.tech). The RailCore key box only appears when RailRadar has failed.
- **Station line:** every station on the route, with times, shown in ASCII. The page scrolls down to the train's current position when you open it.
- **State map:** a pixelated text map showing only the states the train covers, with the route as a `*` line, `o` for stations, station code labels and a blinking `●` for the current position. It is approximate and not meant for navigation.
- **Terminal look:** pure black background, Cascadia Mono at 12px (falls back to Consolas, Menlo or the system monospace font), and a matrix-rain intro. Press any key or click to skip the intro.
- **Phone friendly:** the back button returns from a train to the search screen.

## Using it

1. Host the file (see below) or open it in a normal browser tab. It will not work inside a sandboxed preview, because the browser blocks calls to the live-status API there.
2. Get a free API key from [RailRadar](https://railradar.in), paste it into the key box and press **save key**. The key is stored in your own browser and nowhere else.
3. Type a train number, name or station and press Enter, or tap a result.

Search, the train list and the map work without any key. Only live status needs one.

### Keys and limits

- Each visitor uses their own key. Nothing is stored in this repository.
- RailRadar's free plan has a small monthly limit, so the page shows how many calls you have made this month from this browser. That counter only counts calls from the browser you are using.
- RailCore's docs ask for requests to come from a server. If its key box shows a "blocked or offline" error, it cannot be called straight from a web page.

### Shortcuts

| Key | Action |
| --- | --- |
| Up / Down | Move through search results |
| Enter | Open the highlighted train |
| Esc | Back to search |
| r | Refresh the live status (uses one call) |

## Hosting on GitHub Pages

1. Rename the HTML file to `index.html` and upload it to a public repository.
2. Go to **Settings**, then **Pages**, set the branch to `main` and the folder to `/ (root)`, and save.
3. After a minute or two the site is live at `https://<your-username>.github.io/<repo-name>/`.

Netlify Drop, Cloudflare Pages and Vercel also work, since it is a single static file.

## Notes and limits

- This is an unofficial hobby project. It is not affiliated with Indian Railways, RailRadar or RailCore.
- The built-in train list is a snapshot (November 2026). New or renumbered trains may be missing from search, but any 5-digit train number can still be opened directly for live status. Some trains in the list have no origin or destination shown.
- Live data depends on the provider. Delays, positions and "not live" states are only as good as what they report.
- Station coordinates and state outlines are coarse. Small states such as Goa and Delhi are only a few characters wide, Ladakh is merged into J&K, and the Andaman and Lakshadweep islands are not included.
- Always confirm anything important on [NTES](https://enquiry.indianrail.gov.in) or IRCTC.

## Data sources

- Train and station lists: [datameet/railways](https://github.com/datameet/railways), refreshed from RailRadar's train list.
- State boundaries: [datameet/maps](https://github.com/datameet/maps).
- India outline used in an earlier version: [johan/world.geo.json](https://github.com/johan/world.geo.json).

Check each source's own licence before reusing its data.

## Files

- `index.html`: the whole app, with the data embedded. There is nothing else to build or install.
