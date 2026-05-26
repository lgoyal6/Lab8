# Lab 8 — Network & Service Workers

**Name:** Laksh Goyal

**GitHub Pages URL:** https://lgoyal6.github.io/Lab8/

## Graceful Degradation & Service Workers

Graceful degradation means building an app so that its core experience still
works even when some capability is missing — a flaky network, an old browser,
or disabled JavaScript — instead of breaking entirely. In this lab, service
workers are the tool that makes that resilience possible. A service worker is a
script the browser runs in the background, separate from the page, that can
intercept network requests and serve responses from a local cache. On install,
this app pre-caches all of the recipe URLs, and on every subsequent fetch it
uses a cache-first strategy: if a resource is already cached it is returned
immediately, otherwise it is fetched from the network, added to the cache, and
then returned. The result is that once the page has loaded a single time, the
recipes remain available even with no connection at all, and repeat visits are
faster because resources are not re-downloaded. Combined with `localStorage`
caching of the parsed recipes and a web app manifest that lets the site be
installed like a native app, the page degrades gracefully — falling back to
cached data when the network is unavailable rather than showing a broken,
empty screen.
