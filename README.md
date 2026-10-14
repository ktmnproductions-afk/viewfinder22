# Viewfinder22 — Photo Scout

Photo Scout is a browser-based field guide for photographers. It combines an interactive map, source-linked places and reference photographs, parking candidates, historical notes, nearby scenic subjects, and illustrative composition studies for a Canon EOS R50 with an RF-S 18–150 mm lens.

## Open and develop locally

The main app is a static web app in `index.html`. Its map and geographic/photo research use external services, so run it from a local HTTP server rather than opening the HTML file directly.

1. Clone this repository and open the folder in VS Code.
2. Choose the branch you are working on. Review the Git changes before committing or merging.
3. Start a simple local server from the repository root:

   ```bash
   python -m http.server 8000
   ```

4. Open `http://localhost:8000` in your browser.

VS Code's Live Server extension is another option. Use the browser console to diagnose external network, tile and CORS failures.

## Development workflow

- Make focused changes on a branch and review the diff before committing.
- Test the interactive map, location search, pin selection, nearby-place results, reference-photo source links, saved stops, and responsive layout after relevant changes.
- Browser checks run in GitHub Actions for pull requests targeting `main`.
- The browser workflow checks the primary vector basemap, the raster-map fallback, a real map click, the selected-location sketch and the in-app image-generation authorization gate.
- Automated browser tests do not authorize a provider account and do not spend image-generation credits.

## Map and geographic data

The default map uses MapLibre GL JS and OpenFreeMap vector styles. If vector styles or tiles fail to load, the app attempts a simpler OpenStreetMap raster map. Keep the displayed map attribution intact. Geographic search results are external open-data results and may be incomplete. A mapped feature does not guarantee public access, legal parking, current availability or a clear photographic sightline.

Reference photographs are matched by subject/title where possible and link back to the original source and licence. Illustrative SVG composition sketches are framing ideas, not documentary photographs or verified views.

## Optional AI image generation

The in-app generator uses Pollinations via OAuth authorization-code flow with PKCE.

1. Create a Pollinations App Key at [enter.pollinations.ai/keys](https://enter.pollinations.ai/keys).
2. Register the exact redirect URI displayed by Photo Scout's **Connect image generation** panel. For the public GitHub Pages app, it is `https://ktmnproductions-afk.github.io/viewfinder22/`. Local testing requires a registered local callback too.
3. Paste only the publishable `pk_...` App Key into Photo Scout, save it, and click **Connect account**.
4. Review the provider's consent screen, allowed model, expiry and Pollen budget limit before approving.
5. Select a map pin and generate a concept image. The result appears inside Photo Scout and can be saved locally.

**Never paste a personal secret `sk_...` API key into this static site or commit it to GitHub.** A `pk_...` App Key identifies the OAuth client; it is not the generation token. The temporary user-authorized token is kept in session storage and is not written into the repository. Generation requires an authorized Pollinations account with available Pollen, so it is not guaranteed to be free.

Generated images are creative concepts and must not be presented as proof of the exact real-world view or camera position.

## Deployment

GitHub Actions publishes the repository to GitHub Pages when changes reach `main`. Review and test pull requests before merging. Do not expose provider secret keys in static files.
