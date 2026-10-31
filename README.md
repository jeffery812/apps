# apps

**English** | [简体中文](README.zh-CN.md)

Landing pages and privacy policies for all my apps, published with GitHub Pages. Each app has its own directory.

- Repository: <https://github.com/jeffery812/apps>
- Website: <https://jeffery812.github.io/apps/>

## Apps

| App | Landing page | Privacy policy | App Store |
| --- | --- | --- | --- |
| STHLM Rail | [sthlm-rail/](https://jeffery812.github.io/apps/sthlm-rail/) | [privacy.html](https://jeffery812.github.io/apps/sthlm-rail/privacy.html) | [id1084180460](https://apps.apple.com/se/app/stockholm-rail/id1084180460?l=en-GB) |

## Structure

```
apps/
├── README.md
├── index.html            # List of all apps
├── 404.html              # Site-wide 404 page; GitHub Pages only uses the one in the root
└── sthlm-rail/
    ├── index.html        # Landing page
    ├── privacy.html      # Privacy policy
    └── images/           # Screenshots and icons
```

## Conventions

- **Directory names** use the product name in lowercase, with words joined by `-` and no platform suffix (`sthlm-rail`, not `sthlm-rail-ios`). The directory name is part of the URL, so don't rename it after publishing, or the privacy policy URL in App Store Connect will break.
- **Every app has at least two pages**: `index.html` (landing page) and `privacy.html` (privacy policy).
- **Use relative paths only** for images and pages (`images/icon-180.png`, `privacy.html`), so a directory still works if it's moved.
- **Pages are plain static HTML** with no build step. Fonts and icons load from Google Fonts and unpkg; everything else lives in the page.
- **All pages are in English.**
- **The README exists in English (`README.md`) and Chinese (`README.zh-CN.md`).** Keep both in sync when you change either one.
- **The privacy policy must match what the app actually does**, including the SDKs it uses, the events it reports and how long data is kept. When the app's data handling changes, update `privacy.html` and its "Last updated" date before releasing, and check the privacy labels in App Store Connect.

## Adding a new app

1. Create a directory `<app-name>/` containing `index.html`, `privacy.html` and `images/`.
2. Add an entry to the app list in this README (both the English and Chinese versions), in the root `index.html` and in `404.html`.
3. Preview locally and check for broken links (see below).
4. Commit and push. GitHub Pages usually updates within a minute or two.
5. In App Store Connect, set the app's privacy policy URL to `https://jeffery812.github.io/apps/<app-name>/privacy.html`. If needed, set the support URL or marketing URL to the landing page.

## Local preview

```bash
cd /Users/zhihuitang/repo/Documents/apps
python3 -m http.server 8000
```

Then open <http://localhost:8000/sthlm-rail/>. Opening the HTML files directly also works, but a local server is closer to how the live site behaves.

## Publishing setup

One-time setup on GitHub: in the repository's **Settings → Pages → Build and deployment**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.

To use a custom domain later, add a `CNAME` file to the root and configure DNS with your domain provider. App paths stay the same.
