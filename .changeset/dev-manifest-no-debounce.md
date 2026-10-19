---
'@solidjs/vite-plugin': patch
---

The server function manifest no longer waits a fixed second on each load in dev (#427). When another plugin owns the SSR environment (for example `@cloudflare/vite-plugin`), the generated handler imports the manifest in dev. It reloads each time a new server function module is transformed, so startup, restarts and the first call to a new function each waited 1,000 ms. The debounce is only needed for builds, so dev now returns the current list. Each new module still invalidates the manifest before anything can call it.
