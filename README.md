# Montage 360

360° virtual tours of the Montage Event Complex halls. You can build tours from Insta360 photos, link the photos with hotspots, and browse them by hall, event and tag.

The whole app is one static file, `index.html`. There is no build step and no server. It loads three.js from cdnjs and the Jost font from Google Fonts.

## Run locally

Open `index.html` in a recent Chrome, Edge, Firefox or Safari, or serve the folder:

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy (GitHub Pages)

1. Merge this code into `main`.
2. In the repo, go to **Settings → Pages → Build and deployment → Source** and choose **GitHub Actions**.
3. Every push to `main` runs `.github/workflows/pages.yml` and publishes the site to
   `https://zaib21485.github.io/montage360/`. You can also start the workflow by hand from the **Actions** tab.

GitHub Pages on a **private** repository needs a paid plan (GitHub Pro, Team or Enterprise). On the free plan, make the repository public first.

## Where data is stored

Tours, photos, users and settings are saved in each visitor's own browser (IndexedDB). The hosted site does not share them:

- Tours built on one computer do not appear on another computer or for other visitors.
- Clearing browser data deletes the tours.
- Users, roles and PINs only control the interface on that one browser. They are not real security.

To share tours with other people, you need a backend: storage for the photo tiles (for example S3, Cloudflare R2 or Firebase Storage), a database for tours and hotspots, and real authentication.
