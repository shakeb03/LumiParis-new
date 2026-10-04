# LumiParis-new

Shopify theme code for Lumi Paris (thelumiparis.com). Planning, brand rules and decisions live in the `lumiParis-notes` repo; read its `CLAUDE.md` and `06 Operations/Store Build Brief.md` before changing anything here.

## What this is

Horizon 4.2.0 (Shopify's free theme) with a Lumi Paris brand layer on top. It mirrors the unpublished store theme **"Lumi Paris — build"** (`gid://shopify/OnlineStoreTheme/188769927395`). The live theme (Horizon) is never edited from here.

## Brand layer (everything Lumi is prefixed `lumi-`)

| File | What it does |
|---|---|
| `snippets/lumi-head.liquid` | Loads Cormorant Garamond 500 and Outfit 400/500, and `assets/lumi.css`. Rendered in both layouts |
| `assets/lumi.css` | Design tokens, fonts, buttons, focus ring, labels, cards, sign-up form; hides sale styling |
| `sections/lumi-announcement.liquid` | One-line bar; Canadian visitors see the Canada price line |
| `sections/lumi-hero.liquid` | "Wear the light." hero; Ivory Soft block until AI imagery is approved |
| `sections/lumi-category-tiles.liquid` | Four category tiles |
| `sections/lumi-edit.liquid` + `snippets/lumi-product-card.liquid` | The edit: 4 to 6 products, swipe row on mobile |
| `sections/lumi-facts.liquid` | Three material and care facts; `[FACT FROM BRANVAS DATA]` placeholders only show in the theme editor |
| `sections/lumi-brand-line.liquid` | The approved name line |
| `sections/lumi-reviews.liquid` | Reviews app slot, off until real reviews exist |
| `sections/lumi-early-access.liquid` | Inline sign-up, no discount, tags customers `early-access` |
| `sections/lumi-footer.liquid` | Footer: help and brand menus, email, socials, policies. No address |
| `sections/lumi-password.liquid` | "Lumi Paris is opening soon. Wear the light." with sign-up |
| `blocks/lumi-canada-price.liquid` | "Canada price" label on the product page, Canada only |
| `blocks/lumi-reassurance.liquid` | Reassurance row under Add to bag |
| `blocks/lumi-product-accordions.liquid` | Details, Materials and care, Size guide, Shipping and returns |

Edited Horizon files: `layout/theme.liquid` and `layout/password.liquid` (one line each, rendering `lumi-head`), `config/settings_data.json`, `sections/header-group.json`, `sections/footer-group.json`, `templates/index.json`, `templates/product.json`, `templates/collection.json`, `templates/password.json`.

## Store data the theme expects

- Menus: `lumi-build-main`, `lumi-build-help`, `lumi-build-brand`
- Pages: `about`, `questions`, `care`, `shipping-and-delivery`, `returns`, `contact`
- Collections: `earrings`, `necklaces`, `rings`, `bracelets` (smart, by product type), `gifts` (tag `gift`), `archive` (tag `archive`)
- Product metafields (create definitions before importing the catalog): `custom.material` (single line text, exact supplier wording), `custom.details` (rich text), `custom.size_guide` (rich text)
- Logo file: `shopify://shop_images/lumi-logo-header.png`

## Syncing to the store

Work only in the unpublished "Lumi Paris — build" theme. Push changed files with the Admin API `themeFilesUpsert` (or `shopify theme push --theme 188769927395 --only <files>` with the Shopify CLI). Never use `--live` or publish without the founder's approval. Lint with `@shopify/theme-check-node` before pushing.
