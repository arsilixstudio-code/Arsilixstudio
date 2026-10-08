# Arsilixstudio

Landing page for **Arsilix Studio**, a digital agency working across AI, design, development and automation.

The whole site is a single self-contained file, [`arsilix-studio_1.html`](arsilix-studio_1.html): HTML, CSS and JavaScript in one place, with no build step or dependencies (fonts load from Google Fonts).

## Viewing the site

Open `arsilix-studio_1.html` in any modern browser. That's it.

## Page sections

Hero · Services · Why Arsilix · Portfolio (filterable) · Process · Tech stack · Testimonials · Pricing · FAQ · Contact · Footer

## Editing content

Most section content is generated from plain JavaScript arrays near the bottom of the file, so text changes don't require touching the markup:

| Section | Array |
| --- | --- |
| Services | `services` |
| Why Arsilix | `why` |
| Portfolio | `portfolio` |
| Process | `process` |
| Tech stack | `tech` |
| Testimonials | `testimonials` |
| Pricing | `pricing` |
| FAQ | `faqs` |

Colors and fonts are defined as CSS variables in the `:root` block at the top of the file.
