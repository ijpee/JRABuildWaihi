# JRA BUILD Website (Astro)

Static marketing site for JRA BUILD LIMITED (Waihi Beach, NZ) built with Astro.

## Tech Stack
* Astro 5
* Bootstrap 5 (custom styles in `public/css/style.css`)
* Font Awesome / Bootstrap Icons
* Owl Carousel, WOW.js, Waypoints, Easing (loaded globally)

## Project Structure
```
public/          # Static assets (images currently placeholder stock)
src/
	components/    # Reusable UI (Navbar, Footer)
	layouts/       # Base layout injecting meta, OG, JSON-LD
	pages/         # Route pages (index, about, service, project, contact, 404)
```

## Development
| Command | Description |
| ------- | ----------- |
| `npm install` | Install dependencies |
| `npm run dev` | Start dev server (default http://localhost:4321) |
| `npm run build` | Production build to `dist/` |
| `npm run preview` | Preview built site |

## SEO Enhancements Implemented
* Canonical URL & Open Graph tags (no Twitter) in `BaseLayout.astro`.
* JSON-LD `LocalBusiness` schema.
* Single H1 per page; section headings demoted to H2/H3.
* Descriptive `alt` text and `loading="lazy"` on non-critical images.
* `robots.txt` & static `sitemap.xml` (placeholders: update with real domain).
* Accessible nav (`aria-label`).

## Replace Placeholders
1. Set real production domain:
	 * `astro.config.mjs` -> `site: 'https://your-domain.example'`
	 * `public/robots.txt` -> `Sitemap: https://your-domain.example/sitemap.xml`
	 * `public/sitemap.xml` -> update each `<loc>`.
2. Provide real project/service copy if needed (current images & some text are placeholders).
3. Supply a social share image and pass `ogImage` prop to key pages. Recommended size 1200x630.
4. Replace `#!` social links (Footer & About) with actual profile URLs or remove buttons.

## Adding a New Page
Create `src/pages/your-page.astro`:
```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
import Navbar from '../components/Navbar.astro';
import Footer from '../components/Footer.astro';
---
<BaseLayout title="Title | JRA BUILD" description="Page description." ogImage="https://your-domain.example/img/share.jpg">
	<Navbar />
	<!-- Page content here -->
	<Footer />
</BaseLayout>
```

## Image Optimization (To Do)
Current JPEG/PNG images are placeholders. Before launch:
1. Export originals to appropriately sized WebP (and optionally AVIF) versions.
2. Use a `<picture>` pattern for hero & large gallery images:
```astro
<picture>
	<source srcset="/img/hero-slider-1.webp" type="image/webp" />
	<img src="/img/hero-slider-1.jpg" alt="Custom coastal home build exterior" width="1600" height="900" loading="lazy" />
</picture>
```
3. Add explicit width/height to reduce layout shift.

## Generating a Dynamic Sitemap (Optional)
Astro Integration (manual example pending). For small static sites, the committed file is fine—just update when adding pages.

## Accessibility Checklist
* Single H1 per page: ✅
* Alt text present: ✅ (update with real project descriptions when available).
* Color contrast: Verify against final brand palette.

## Future Enhancements
* Image optimization (WebP/AVIF + responsive sizes)
* Remove unused JS libraries if certain animations/carousels are dropped
* Add form spam protection (honeypot or captcha) for `contact` form
* Add 301 redirects if legacy URLs exist

---
Questions or changes needed? Update the layout or open an issue.
