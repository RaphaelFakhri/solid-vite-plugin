---
'@solidjs/vite-plugin': patch
---

With `serverFunctions: { components: true }`, the dev server now also pre-bundles `@solidjs/web/server-functions/client`. `@solidjs/web/frames` imports the runtime by that subpath. When the app listed `@solidjs/web` in `optimizeDeps.exclude`, the frames bundle loaded a second copy of the client from node_modules, and server components that mounted after boot resolved to `undefined` (#428).
