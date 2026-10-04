# Edge Add-ons — Privacy & Permissions (Partner Center → Privacy step, copy-paste)

## Single purpose description (required)

```text
Detect downloadable media (videos, streams and files) on web pages and hand them to the Swift Download Manager desktop application running on the user's own computer.
```

## Remote code question

```text
No, I am not using remote code.
```

All code (content script, background worker, popup, options) ships inside the package. Nothing is fetched from a CDN or evaluated at runtime.

---

## Permission justifications (one per permission shown in the package)

### `webRequest`
```text
Observes network requests made by web pages in order to detect downloadable media files (video streams, HLS/DASH manifests, direct file links) so the floating download button and quality menu can be offered.
```

### `storage`
```text
Saves the user's own settings (local app address, feature switches, menu preferences) in browser storage so they persist between sessions.
```

### `downloads`
```text
Lets the browser download a file directly when the user explicitly chooses the browser-download fallback instead of the desktop app.
```

### `alarms`
```text
Periodically checks whether the Swift Download Manager desktop app is running on the user's computer (localhost) so the toolbar popup and button state stay accurate.
```

### `cookies`
```text
Reads the current site's session cookies so the local desktop app can open authenticated video pages exactly as the browser sees them. Cookies are only ever sent to 127.0.0.1 on the user's own machine and are never sent to the developer or any remote server.
```

### Host permissions `<all_urls>`
```text
The content script must run on every web page to show the floating download button, and media requests must be observed on all sites so downloadable files can be detected anywhere the user browses.
```

---

## Data usage questions (Partner Center → Privacy → Data usage)

**What actually happens in this extension (answer truthfully based on the exact checkbox labels you see):**

- All processing is local. The extension sends data **only to 127.0.0.1** (the SwiftDM desktop app on the user's own PC).
- **Nothing** is transmitted to the developer, to analytics, or to any third-party server.
- Data that flows to the local app: the media URL/format information of the current page and, on login-walled sites, the current site's session cookies (so the app can fetch the same media the browser sees).
- Settings live in `chrome.storage` on the user's device.

**How to answer:** if the checklist wording is about data *collected by the developer or sent to external servers*, select **"None of the above"** — that statement is accurate for this extension. If there is an option covering *"authentication information"* or *"website content"* being *transmitted*, tick it and note in any free-text box: *"transmitted only to 127.0.0.1 on the user's own machine (companion desktop app); never leaves the device."* Do not tick options for things you don't do (location, financial info, web history, etc.).

---

## Privacy policy (required — must be a public URL)

Save the text below as `PRIVACY.md` in a **public GitHub repository** and link the rendered page,
e.g. `https://github.com/YOURNAME/swiftdm/blob/main/PRIVACY.md`
(or any page you host). GitHub README/PRIVACY pages are acceptable as privacy policy URLs.

```markdown
# Privacy Policy — SwiftDM Companion

Last updated: October 2026

SwiftDM Companion (the "extension") is a companion to the Swift Download Manager
desktop application. This policy describes exactly what the extension accesses
and where it goes.

## What the extension accesses

- **Media information from web pages you visit** (video/file URLs, formats, page titles)
  in order to show download buttons and quality menus.
- **Session cookies of the current site**, only when inspecting a page that requires
  login, so the local desktop app can see the same content your browser sees.
- **Your settings** (server address on your computer, feature switches), stored in
  your browser's local storage.

## Where the data goes

All of the above is sent **only to the Swift Download Manager application running on
your own computer (127.0.0.1)**. It is used to create and manage your downloads.

## What the extension does NOT do

- It does not send any data to the developer or to any other server.
- It does not use analytics, trackers, or advertising.
- It does not collect personal information, location, history, or financial data.
- It does not share data with third parties.

## Data retention

The extension stores only your settings in your browser. You can remove them at any
time by removing the extension or clearing the browser's extension storage.

## Contact

[YOUR SUPPORT EMAIL]
```

---

## Certifications (checkboxes shown in the Privacy step)

Answer honestly; for this extension the correct answers are:

- Single purpose: as written above ✓
- I am not using remote code ✓
- The extension does not modify any website it visits (it only adds its own overlay button on video elements) ✓
- If asked whether it injects code into pages: it injects its own local content script only, no remote code
