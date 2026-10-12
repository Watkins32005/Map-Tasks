# Cobotiq guide builder (GitHub version)

One page (`index.html`) that builds a Map and Task Guide PDF from files stored in a public GitHub repo.

## How a guide is put together

1. Title page: generated from the site details, styled by the build-out (header color, robot picture, cover art, QR badge).
2. Map and Task pages: generated from the site details, same style.
3. Operation pages: your premade PDF, PNG or JPG files, added exactly as they are.
4. Maintenance pages: same.
5. Last page: a premade QR page chosen per guide (PDF, PNG or JPG).

A build-out links items 1 to 4 and a default for item 5. QR pages are stored separately and reused across build-outs.

## Repo layout (suggested)

    index.html            this tool
    builds.json           the index (build-outs and QR pages)
    pages/<build-id>/     operation and maintenance files
    qr/                   QR pages
    img/                  robot pictures, cover art, title QR badges

## One-time setup

1. Create a public repo and add `index.html` and `builds.json`.
2. Repo Settings, Pages, deploy from branch `main`, folder `/ (root)`.
3. Open `https://OWNER.github.io/REPO/`. The tool loads `builds.json` next to it automatically.
   Links in `builds.json` can be relative to that file (for example `pages/phantas-v1-3/operation.pdf`).

You can also open `index.html` from your computer. Paste the raw link to `builds.json` into "Library index", for example
`https://raw.githubusercontent.com/OWNER/REPO/main/builds.json`, and press Load. Links must then be full links.

## Adding a new build-out

1. Upload the page files to the repo (Add file, Upload files).
2. Open the tool, "Add to the library", "New or edit build-out". Paste each file link. GitHub "blob" links are converted to raw links for you.
3. Press Check links, then Preview title and map pages, then Add to working copy.
4. Test it in "Build a guide". It works there before it is published.
5. In "Index and publish", Copy or Download builds.json and commit it to the repo.
6. Wait about five minutes (GitHub caches raw files), then reload.

QR pages work the same way under "New or edit QR page".

## Good to know

- The tool never writes to GitHub. You commit `builds.json` yourself.
- Unpublished changes are kept in your browser until you commit them or press Discard.
- Nothing is deleted. Archive hides an item from the Build tab; you can restore it.
- Premade pages keep their own size. Use letter size for a consistent guide.
- Password-protected PDFs may not merge. Export an unprotected copy.
- The page loads three libraries from cdnjs.cloudflare.com (jsPDF, pdf-lib, pdf.js), so it needs internet access.
