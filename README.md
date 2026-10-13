# New1Direction.github.io

Personal portfolio for ares: repo.ing, Ohiyo, and wmcp.sh, with Korg as the engineering deep dive.
Live at https://new1direction.github.io

Single-file static site (`index.html`). Edit and push to update.

## Outbound analytics

Clicks on links to repo.ing, Ohiyo, wmcp.sh, and Korg (product sites, source repos, packages) are measured by a small provider-neutral hook at the bottom of `index.html`. It sets no cookies, uses no storage, and sends no identifiers; visitors with Global Privacy Control or Do Not Track enabled are skipped. Links always navigate natively.

Each click dispatches `outbound:click` on `document` with `{ product, placement, destination, page }`, for example `{ "product": "ohiyo", "placement": "contact", "destination": "app.ohiyo.gg/", "page": "/" }`.

- **Collector:** set `analytics.endpoint` to a URL that accepts a `text/plain` JSON POST. It's empty by default, so no requests are sent.
- **Provider script:** listen for the event instead, e.g. `document.addEventListener('outbound:click', (e) => plausible('Outbound', { props: e.detail }))`.
- **Products:** edit `analytics.products` (host or whole-segment path prefixes). Override a link's placement with `data-placement`.
- **Debug:** open the site with `?analytics-debug` to log events to the console.
