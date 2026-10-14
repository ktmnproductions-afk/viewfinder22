# Viewfinder22 — Photo Scout

Photo Scout is a browser-based field guide for photographers. It combines an interactive map, source-linked places and reference photographs, parking candidates, historical notes, and illustrative composition studies for a Canon EOS R50 with an RF-S 18–150 mm lens.

## Open and develop locally

The main app is a static web app in `index.html`. Its map and geographic/photo research use external services, so run it from a local HTTP server rather than opening the HTML file directly.

1. Clone this repository and open the folder in VS Code.
2. Choose the feature branch for changes under review, or use `main` for the currently published version.
3. Start a simple local server from the repository root:

   ```bash
   python -m http.server 8000
   ```

4. Open `http://localhost:8000` in your browser.

VS Code's Live Server extension is another option. The browser console is useful for diagnosing external network and CORS errors.

## Development workflow

- Make focused changes on a branch.
- Review the diff before committing.
- Test the map, location search, pin selection, nearby-place results, reference-photo source links, saved stops, and responsive layout after changing relevant code.
- Browser checks run in GitHub Actions for pull requests targeting `main`.
- The workflow checks the primary vector map when available, the raster-map fallback, a real map click, the selected-location sketch, and the in-app image-generation authorization gate.
- AI provider credits are not spent by the automated browser tests; the test does not authorize an account or invoke image generation.

## Map and data sources

The default basemap uses MapLibre GL JS with OpenFreeMap vector styles. If the vector style or tiles fail to load, the app attempts a simpler OpenStreetMap raster layer. Attribution is shown in the map controls/footer. Geographic search results come from external open-data services and may be incomplete; a mapped feature does not guarantee public access, a legal place to park, or a clear photographic sightline.

Reference photographs are matched by subject/title where possible and link to their original source and licence. Illustrative SVG composition sketches are framing ideas, not documentary photographs or verified views.

## Optional AI image generation

The in-app generator uses Pollinations' image API via its OAuth authorization-code flow with PKCE.

1. Create a Pollinations App Key in the [Pollinations key dashboard](https://enter.pollinations.ai/keys).
2. Register the exact callback URI displayed in Photo Scout's **Connect image generation** panel. The public GitHub Pages URI for this project is `https://ktmnproductions-afk.github.io/viewfinder22/`; local testing requires a registered local callback too.
3. Paste only the publishable `pk_...` App Key into Photo Scout, save it, and click **Connect account**.
4. Review the provider's consent screen and its model, expiry and Pollen budget limits before approving.
5. Generate an image from a selected map pin. It is displayed inside the app and can be saved locally.

**Do not paste a personal secret `sk_...` key into the static app, commit it to GitHub, or place it in browser source.** The `pk_...` value is a public OAuth client identifier, not a generation token. The temporary user-authorized token is kept in the browser session; it is not written into the repository. Image generation requires an authorized Pollinations account with available Pollen and is not guaranteed to be free.

Generated images are creative concepts. They should never be presented as proof of the exact real-world view or camera position.

## Deployment

GitHub Actions publishes the contents of the repository to GitHub Pages when changes reach `main`. Review and test a pull request before merging; do not expose provider secret keys in static files.
