# Widgets Analysis Report

## Widget Types Found

| Widget | Location | Purpose |
| --- | --- | --- |
| `points-alert` | `public/widget-loader.js`, `/widget/embed` | Compact inline promo badge that can dismiss itself and does not open a modal |
| `points-card` | `public/widget-loader.js`, `/widget/modal`, `promos/points-card-addon.blade.php` | Richer product-page card that opens a parent-page modal |
| `installments` | `public/widget-loader.js`, `promos/installments.blade.php` | Larger promo widget suitable for checkout / decision-stage messaging |

## JS CDN / Loader

- Primary loader found at: `public/widget-loader.js`
- Script usage in code comments:
  - `https://papp.sa/widget-loader.js`
- Runtime default base URL inside loader:
  - `https://business.papp.sa`

## Public Routes

- `GET /widget/embed`
- `GET /widget/modal`
- `GET /widget-test`
- `GET /tool/assets/fonts/{file}`
- `GET /tool/assets/images/{file}`

## Required Parameters

### Common init shape

```javascript
PointsWidget.init({
  type: 'points-card', // or points-alert / installments
  lang: 'ar',          // ar or en
  points: 250,         // used by promo widgets
  container: '#widget-container',
  widgetUrl: 'https://business.papp.sa', // optional, auto-detected when possible
  callbackUrl: 'https://example.com/callback' // used by installments
});
```

### Auto-init shape

```html
<script
  src="https://business.papp.sa/widget-loader.js"
  data-type="points-alert"
  data-lang="ar"
  data-points="300"
  data-container="#widget-4">
</script>
```

## Authentication

- Widgets use publicly embeddable frontend configuration only
- No Private Key usage found in widget loader implementation
- Embed requests are driven by URL query params to `/widget/embed`

## Backend Endpoints Used

- `/widget/embed?type=...&lang=...&points=...&parentOrigin=...`
- `/widget/modal?type=...&lang=...`

## Widget Behavior

### `points-alert`

- Inline badge / alert
- Clicking it should hide / dismiss it
- Does **not** open a modal

### `points-card`

- Inline card with points message
- Clicking it opens modal content in the parent page
- Modal content fetched from `/widget/modal`

### `installments`

- Taller widget with explanatory content
- Supports `callbackUrl`
- Suitable for checkout or purchase-decision surfaces

## Loader Capabilities Confirmed

- iframe-based isolation
- skeleton loading state
- postMessage resize handling
- parent modal rendering
- auto-init from script data attributes
- `destroy()` method for cleanup

## Customization Options Available

- `type`
- `lang`
- `points`
- `container`
- `widgetUrl`
- `parentOrigin`
- `callbackUrl`

## Known Constraints

- No evidence of separate `ProductWidget` / `CheckoutWidget` JS classes
- No theme / size public API found in current loader
- No widget-specific OpenAPI documentation found in `openapi/points-api-v1.yaml`

