# UI Design & Layout Guide

This document describes the visual system, layout, and component structure of this Astro Blog Starter.

## 1) Design tokens (CSS custom properties)
These are defined in global CSS and control color and elevation.

```css
/* tokens in global.css */
:root {
  --accent: #2337ff;
  --accent-dark: #000d8a;
  --black: 15, 18, 25;
  --gray: 96, 115, 159;
  --gray-light: 229, 233, 240;
  --gray-dark: 34, 41, 57;
  --gray-gradient: rgba(var(--gray-light), 50%), #fff;
  --box-shadow: 0 2px 6px rgba(var(--gray), 25%), 0 8px 24px rgba(var(--gray), 33%), 0 16px 32px rgba(var(--gray), 33%);
}
```
- Accent: interactive/link color
- Black/Gray: text palette (rgb triplets to be used with rgb(var(...)))
- Box-shadow: elevation for cards/hero images

## 2) Typography
- Font family: “Atkinson” (regular 400, bold 700), preloaded in BaseHead and declared in CSS
- Base sizing: 20px on desktop, 18px under 720px
- Headings scale: h1 3.052em, h2 2.441em, h3 1.953em, h4 1.563em, h5 1.25em
- Body line-height: 1.7; headings 1.2

## 3) Global layout and spacing
- Page container main: 720px fixed width with responsive max-width and center alignment; 3em vertical padding (1em under 720px)
- Images: max-width: 100%; 8px radius; hero images get box-shadow
- Code blocks: padded and rounded; inline code has gray bg

## 4) Blog post layout
- BlogPost layout overrides main to be edge-to-edge and centers the inner .prose at 720px
- Title block centered with date and optional last-updated
- Optional hero image above content, full width container, centered, 12px radius + box shadow

## 5) Navigation header
- Structure: Site title at left, internal nav links, social links at right
- Active link: underline + heavier weight
- Responsive: hide social links below 720px
- Elevation: white bg with subtle box-shadow

## 6) Footer
- Centered content; gradient background; gray text
- Social links displayed in a centered row with gap

## 7) Responsive behavior
- Single breakpoint at 720px used in global and header
- Adjustments: font-size from 20px to 18px; main padding reduced; social links hidden in header

## 8) Accessibility
- sr-only utility class for accessible labels on icon-only links
- Images are responsive; ensure meaningful alt on content images (hero image uses empty alt; consider adding descriptive alt if needed)

## 9) Theming & customization guidance
- To change brand color, update --accent and optionally --accent-dark; verify contrast (WCAG AA)
- To widen content, change main width (global) and .prose width (BlogPost)
- To introduce another breakpoint, extend @media queries consistently (global and components)

## 10) Component inventory
- BaseHead: global metadata, font preloads, and global.css import
- Header / HeaderLink: site navigation, active link logic, social icons
- Footer: copyright and social links
- FormattedDate: date formatting for posts

Include code references below for traceability (see appendix sections A–E for exact source snippets).

### Appendix A — Tokens & Typography (global.css)

```7:18:src/styles/global.css
:root {
  --accent: #2337ff;
  --accent-dark: #000d8a;
  --black: 15, 18, 25;
  --gray: 96, 115, 159;
  --gray-light: 229, 233, 240;
  --gray-dark: 34, 41, 57;
  --gray-gradient: rgba(var(--gray-light), 50%), #fff;
  --box-shadow:
    0 2px 6px rgba(var(--gray), 25%), 0 8px 24px rgba(var(--gray), 33%),
    0 16px 32px rgba(var(--gray), 33%);
}
```

```19:45:src/styles/global.css
@font-face {
  font-family: "Atkinson";
  src: url("/fonts/atkinson-regular.woff") format("woff");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Atkinson";
  src: url("/fonts/atkinson-bold.woff") format("woff");
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}
body {
  font-family: "Atkinson", sans-serif;
  margin: 0;
  padding: 0;
  text-align: left;
  background: linear-gradient(var(--gray-gradient)) no-repeat;
  background-size: 100% 600px;
  word-wrap: break-word;
  overflow-wrap: break-word;
  color: rgb(var(--gray-dark));
  font-size: 20px;
  line-height: 1.7;
}
```

```62:76:src/styles/global.css
h1 { font-size: 3.052em; }
h2 { font-size: 2.441em; }
h3 { font-size: 1.953em; }
h4 { font-size: 1.563em; }
h5 { font-size: 1.25em; }
```

```130:137:src/styles/global.css
@media (max-width: 720px) {
  body {
    font-size: 18px;
  }
  main {
    padding: 1em;
  }
}
```

### Appendix B — Global layout (global.css)

```46:51:src/styles/global.css
main {
  width: 720px;
  max-width: calc(100% - 2em);
  margin: auto;
  padding: 3em 1em;
}
```

```103:129:src/styles/global.css
img { max-width: 100%; height: auto; border-radius: 8px; }
code { padding: 2px 5px; background-color: rgb(var(--gray-light)); border-radius: 2px; }
pre { padding: 1.5em; border-radius: 8px; }
pre > code { all: unset; }
blockquote { border-left: 4px solid var(--accent); padding: 0 0 0 20px; margin: 0px; font-size: 1.333em; }
hr { border: none; border-top: 1px solid rgb(var(--gray-light)); }
```

```139:155:src/styles/global.css
.sr-only {
  border: 0;
  padding: 0;
  margin: 0;
  position: absolute !important;
  height: 1px;
  width: 1px;
  overflow: hidden;
  /* IE6, IE7 - a 0 height clip, off to the bottom right of the visible 1px box */
  clip: rect(1px 1px 1px 1px);
  /* maybe deprecated but we need to support legacy browsers */
  clip: rect(1px, 1px, 1px, 1px);
  /* modern browsers, clip-path works inwards from each corner */
  clip-path: inset(50%);
  /* added line to stop words getting smushed together (as they go onto separate lines and some screen readers do not understand line feeds as a space */
  white-space: nowrap;
}
```

### Appendix C — Blog post layout

```16:44:src/layouts/BlogPost.astro
<style>
  main {
    width: calc(100% - 2em);
    max-width: 100%;
    margin: 0;
  }
  .hero-image {
    width: 100%;
  }
  .hero-image img {
    display: block;
    margin: 0 auto;
    border-radius: 12px;
    box-shadow: var(--box-shadow);
  }
  .prose {
    width: 720px;
    max-width: calc(100% - 2em);
    margin: auto;
    padding: 1em;
    color: rgb(var(--gray-dark));
  }
  .title {
    margin-bottom: 1em;
    padding: 1em 0;
    text-align: center;
    line-height: 1;
  }
  .title h1 { margin: 0 0 0.5em 0; }
  .date { margin-bottom: 0.5em; color: rgb(var(--gray)); }
  .last-updated-on { font-style: italic; }
</style>
```

```57:83:src/layouts/BlogPost.astro
<main>
  <article>
    <div class="hero-image">
      {heroImage && <img width={1020} height={510} src={heroImage} alt="" />}
    </div>
    <div class="prose">
      <div class="title">
        <div class="date">
          <FormattedDate date={pubDate} />
          { updatedDate && (
            <div class="last-updated-on">
              Last updated on <FormattedDate date={updatedDate} />
            </div>
          )}
        </div>
        <h1>{title}</h1>
        <hr />
      </div>
      <slot />
    </div>
  </article>
</main>
```

### Appendix D — Header

```6:14:src/components/Header.astro
<header>
  <nav>
    <h2><a href="/">{SITE_TITLE}</a></h2>
    <div class="internal-links"> ... </div>
    <div class="social-links"> ... </div>
  </nav>
</header>
```

```45:85:src/components/Header.astro
<style>
  header {
    margin: 0;
    padding: 0 1em;
    background: white;
    box-shadow: 0 2px 8px rgba(var(--black), 5%);
  }
  h2 { margin: 0; font-size: 1em; }
  h2 a,
  h2 a.active { text-decoration: none; }
  nav { display: flex; align-items: center; justify-content: space-between; }
  nav a { padding: 1em 0.5em; color: var(--black); border-bottom: 4px solid transparent; text-decoration: none; }
  nav a.active { text-decoration: none; border-bottom-color: var(--accent); }
  .social-links,
  .social-links a { display: flex; }
  @media (max-width: 720px) { .social-links { display: none; } }
</style>
```

### Appendix E — Footer

```5:15:src/components/Footer.astro
<footer> ... social links ... </footer>
```

```42:62:src/components/Footer.astro
<style>
  footer { padding: 2em 1em 6em 1em; background: linear-gradient(var(--gray-gradient)) no-repeat; color: rgb(var(--gray)); text-align: center; }
  .social-links { display: flex; justify-content: center; gap: 1em; margin-top: 1em; }
  .social-links a { text-decoration: none; color: rgb(var(--gray)); }
  .social-links a:hover { color: rgb(var(--gray-dark)); }
</style>
```