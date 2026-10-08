# Big Hands

One-page dark-luxury streetwear site, rebranded from the previous
"P$ Noir / Prime Atelier" project to **Big Hands**, using the new BH logo.
Same visual language (black background, chrome/white type, red + blue
accents) — hero, a horizontally-scrolling "Coming Soon" section, brand
story, two-person leadership section, contact, and a working shopping
cart. Pure HTML/CSS/JS — no build step, no dependencies.

## Files

```
index.html         All page markup and section content
style.css           All styling (colors/fonts as CSS variables at the top)
script.js           Cart, checkout stub, newsletter stub, scroller, smooth scroll
assets/logo.jpeg    The Big Hands logo, used in the navbar and footer
```

Open `index.html` in a browser to preview.

## Latest update

- Logo swapped for the new monogram-only version (`assets/logo.jpeg`) —
  cropped tight around the "BH" mark and centered on its own square, with
  the "BIG HANDS" wordmark beneath it removed since the site already
  spells the name out in text next to the mark.
- Coming Soon is now two separate sliders, **Men** and **Women**, each
  scrolling independently (see below).

## What changed from the P$ Noir version

- Brand name/logo swapped throughout (nav, footer, page title, favicon).
- The old product grid (`#collections`) is now `#coming-soon` — a
  horizontally-scrollable teaser row instead of a shop. See below.
- The old single CEO section (`#ceo`) is now `#leadership` — two profile
  cards, Founder and Co-Founder. See below.
- Cart and checkout logic is untouched and still fully wired up; there
  just aren't any purchasable items yet since the shop is "coming soon."

## Placeholders to replace

Search the project for `[Placeholder: ...]` — every instance marks
something to swap out before launch: the nav tagline, Coming Soon preview
images/captions, the Atelier brand-story copy, both leaders' names/
titles/quotes/bios/portraits, contact info, and footer legal links.

## Coming Soon section (horizontally scrollable, adaptable)

`#coming-soon` holds two independent sliders stacked vertically — **Men**
and **Women** — each its own `.coming-soon-group` with a heading, a flex
row (`.coming-soon-track`) that scrolls sideways with CSS scroll-snap,
and its own pair of arrow buttons. The two sliders scroll independently
of each other.

To add more previews to either slider, copy one `.coming-soon-item`
block inside that group's `.coming-soon-track` in `index.html`:

```html
<figure class="coming-soon-item">
  <span class="badge red-badge">Coming Soon</span>
  <img src="your-image.jpg" alt="Describe the image">
  <figcaption>Optional caption</figcaption>
</figure>
```

There's no grid to rebalance — add as many as you like and the row just
keeps scrolling. Each item is sized with `clamp()` so they stay a
reasonable width on any screen.

To add a third slider (e.g. "Kids" or "Accessories"), copy one whole
`.coming-soon-group` block — the JS in `script.js` automatically wires up
arrows for any `.coming-soon-scroller` it finds, no changes needed there.

## Leadership section (Founder + Co-Founder)

`#leadership` holds a `.leadership-grid` containing two `.leader-card`
blocks, one per founder. To add a third person later, copy one
`.leader-card` block and paste it into the grid — it wraps automatically
and stacks on narrow screens.

## Cart & checkout (payment-ready, not yet connected)

Unchanged from before: the cart persists to `localStorage`, and
`PAYMENT_CONFIG` near the top of `script.js` is where you plug in a real
backend endpoint once one exists. See the comments there for the exact
steps. Since the shop is "Coming Soon," there are currently no
`.product-card` elements feeding the cart — once real products are ready,
add cards with `data-id` / `data-name` / `data-price` attributes and an
`.add-to-cart-btn`, the same pattern the old collections section used.

## Newsletter signup

The form in `#contact` still just logs the submitted email to the
console. Connect it to a real provider (Mailchimp, Klaviyo, your own
backend) inside the newsletter handler in `script.js`, marked with a
`TODO`.

## Known gaps to close before launch

- No real checkout backend yet.
- No real email provider connected yet.
- No actual products yet (by design — section is "Coming Soon").
- Legal pages (Shipping & Returns, Privacy Policy) are placeholder links
  with no destination.
