# datawhorehouse

A super–minimal static site delivered via GitHub Pages. Single React-powered page loading from a CDN; no build step required.

## Preview
Open `index.html` directly in a browser or visit the GitHub Pages URL once enabled:
```
https://<your-github-username>.github.io/datawhorehouse/
```

## Enable GitHub Pages
1. Commit & push `index.html` (already present).
2. In the repository on GitHub go to: Settings → Pages.
3. Under "Build and deployment" choose:
   - Source: `Deploy from a branch`
   - Branch: `main` / root (`/`)
4. Save. Wait 1–2 minutes for the site to publish.
5. Your site will appear at: `https://<username>.github.io/datawhorehouse/`.

(Optional) Add a custom domain under the same Pages settings; GitHub will guide DNS changes.

## Add Your Images
The placeholder dashed box sits inside a `<div class="image-shell">` container. Replace it with one or more `<img>` tags.

Example:
```html
<div class="image-shell">
  <img src="images/hero.jpg" alt="Hero description" style="width:100%;height:100%;object-fit:cover;" />
</div>
```

### Steps
1. Create an `images/` folder at the repo root.
2. Add your image files (e.g. `hero.jpg`).
3. Update the markup inside `index.html`.
4. Commit & push; refresh the live site.

## Multiple Images / Simple Gallery
You can swap the placeholder with a lightweight gallery—still no build tools required. Example script snippet:
```html
<script>
  const pics = [
    'images/pic1.jpg',
    'images/pic2.jpg',
    'images/pic3.jpg'
  ];
  const shell = document.querySelector('.image-shell');
  let i = 0;
  function show() {
    shell.innerHTML = `<img src="${pics[i]}" alt="Gallery image ${i+1}" style="width:100%;height:100%;object-fit:cover;" />`;
    i = (i + 1) % pics.length;
  }
  show();
  setInterval(show, 4000);
</script>
```
Place this after the existing React script, or convert the React component to manage images—either works.

## Accessibility Tips
- Always provide meaningful `alt` text.
- Maintain sufficient contrast if you change colors.
- Keep decorative images empty `alt=""`.

## Customization Ideas
| Goal | Quick Change |
|------|--------------|
| Title | Edit `<title>` tag in `index.html` |
| Favicon | Replace the inline SVG data URL with `favicon.ico` |
| Fonts | Add `<link rel="preconnect" href="https://fonts.googleapis.com">` + desired font CSS |
| Analytics | Paste script before closing `</body>` |
| Dark only | Remove the `@media (prefers-color-scheme: light)` block |

## No Build Philosophy
Everything runs from a single HTML file + CDN React. If you later want a build (Vite/Next/etc.), you can add a toolchain without losing history.

## Cache Busting
When replacing images, browsers may cache them. Append a query string: `hero.jpg?v=2` if you don’t see updates.

## License
Add a license of your choice if this will be public. (MIT is common.)

---
Enjoy your minimal site. Push and it ships.
