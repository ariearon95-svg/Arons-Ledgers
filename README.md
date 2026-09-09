# Aron Book — PWA files (for an online APK builder)

This folder is a ready-to-host Progressive Web App:

- `index.html` — your app
- `manifest.json` — app name, icons, colors (generated from the logo already
  embedded in your app)
- `sw.js` — basic offline-caching service worker
- `icons/icon-192.png`, `icons/icon-512.png` — generated from your app's logo

## Fastest path: PWABuilder.com

1. Host these files somewhere public (e.g. GitHub Pages, Netlify, Vercel,
   or your own web host) so they're all served from one URL, with
   `index.html` at the root of that URL.
2. Go to https://www.pwabuilder.com, paste that URL in, and click **Start**.
3. PWABuilder will detect the manifest and service worker automatically.
4. Click **Package for stores → Android**, choose the options (package
   name, signing key — it can generate one for you), and download the
   generated APK/AAB.

## Notes specific to this app

Your app itself detects when it's running inside a packaged WebView (the
`isPackagedWebViewApp()` check near the end of `index.html`) and shows extra
hints if:
- the file upload buttons ("Upload logo", CSV import) don't respond — the
  wrapper needs "File Upload" / "File Chooser" support turned on, and
- PDF downloads/sharing don't work — the wrapper needs Blob/download
  support turned on.

Most APK-builder tools (including PWABuilder's generated Trusted Web
Activity) handle this correctly by default since they use Chrome itself
rather than a bare WebView, but if you use a different builder, look for
those two settings specifically.

## Alternative: full Android Studio project

If you'd rather have full control (or the online builder doesn't support a
setting your app needs), a complete, ready-to-open Android Studio project
that wraps this same app with proper file-chooser and PDF-download support
built in is provided alongside this folder.
