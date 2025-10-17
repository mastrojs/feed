# @mastrojs/feed

Generate feeds with [Mastro](https://mastrojs.github.io/).

Currently only Atom, but we might add RSS in the future if there's demand.

## Install

### Deno

    deno add jsr:@mastrojs/feed

### Node.js

    pnpm add jsr:@mastrojs/feed


## Usage

```ts
import { atomResponse } from "@mastrojs/feed";
import { html } from "@mastrojs/mastro";

const baseUrl = "https://mywebsite.org/";

export const GET = () => {
  // read feed entries here from db or markdown files
  const entries = [{
    title: "Test",
    id: new URL("blog/test/", baseUrl),
    updated: new Date("2025-01-01"),
    content: html`Less: <em> &lt; </em>`,
  }];

  return atomResponse({
    title: "My Blog",
    id: new URL(baseUrl),
    linkSelf: new URL("feed.xml", baseUrl),
    updated: new Date("2025-01-01"),
    author: { name: "me" },
    entries,
  };
}
```

To see all functions `@mastrojs/feed` exports, see its [API docs](https://jsr.io/@mastrojs/feed/doc).
