# ClipSave

A simple, fast, mobile-friendly web page for saving a public TikTok video to your device from its link. No account, no tracking, no app to install.

> **Disclaimer:** ClipSave is an independent project. It is **not affiliated with, endorsed by, sponsored by, or connected to TikTok or ByteDance** in any way. TikTok is a trademark of its respective owner. See [Legal](#legal) before using or deploying this project.

---

## Features

- Paste a public video link and get the video, an HD version when available, or the audio track as MP3
- Works on phones, tablets, and desktops
- Automatic light and dark theme
- One static HTML file, with no build step, no framework, and no dependencies
- No cookies, analytics, or local storage
- Keyboard accessible, with reduced-motion support
- Built-in Terms & privacy dialog

## How it works

ClipSave is a static front end. It does not host, store, or process any videos itself.

1. You paste a TikTok video link.
2. The page sends that link to a third-party media service (configured in `CONFIG.API_URL`).
3. The service returns the video details and file URLs.
4. Your browser downloads the file directly from the service's servers.

Because it relies on a third-party service, ClipSave works only as long as that service does.

## Deploy with GitHub Pages

1. Fork this repository, or create a new one and add `index.html`.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, then select your main branch and the `/ (root)` folder.
4. Save. Your site will be live at `https://<your-username>.github.io/<repository-name>/` within a few minutes.

## Configuration

Settings are at the top of the `<script>` block in `index.html`:

```js
const CONFIG = {
  API_URL: 'https://www.tikwm.com/api/',
  API_ORIGIN: 'https://www.tikwm.com'
};
```

| Option       | Description                                                                                  |
| ------------ | -------------------------------------------------------------------------------------------- |
| `API_URL`    | Endpoint that resolves a TikTok link to file URLs.                                           |
| `API_ORIGIN` | Origin used to complete relative file URLs returned by the service.                          |

If the service stops working, point `API_URL` at another compatible service or at your own proxy that returns the same JSON shape.

## Known limitations

- **Depends on a third-party service.** If it goes offline, changes its API, adds rate limits, or blocks browser requests from other sites, ClipSave will stop working until the configuration is updated.
- **Public videos only.** Private, removed, or region-restricted videos cannot be saved.
- **Browser behavior varies.** Some browsers block direct cross-origin saves. In that case ClipSave opens the file in a new tab so you can save it from there.
- **No guarantee of availability.** This is a hobby project, not a commercial service.

## Legal

### Not affiliated

ClipSave is not affiliated with, authorized by, maintained by, sponsored by, or endorsed by TikTok, ByteDance, or any of their subsidiaries or affiliates. All product names, logos, and brands are the property of their respective owners and are used here only to describe what the tool does.

### Responsible use

Videos are the property of their creators and are protected by copyright and other laws. Use ClipSave only to save content that you created, that you have permission to download, or that you may lawfully save for personal use under the laws of your country. Do not re-upload, redistribute, or monetize other people's content without permission. Using this tool may also be restricted by TikTok's own terms of service. You alone are responsible for how you use it.

### No warranty

This software is provided **"as is"**, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or contributors be liable for any claim, damages, or other liability arising from, out of, or in connection with the software or its use.

### Privacy

ClipSave itself uses no accounts, cookies, analytics, or browser storage. The link you paste is sent to a third-party service to fetch the video, and that service has its own privacy practices and terms. Review them before use. If you deploy this project, you are responsible for any logging or analytics you add.
