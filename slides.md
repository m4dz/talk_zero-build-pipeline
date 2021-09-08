---
title: Zero Build Pipeline
theme: ../divRIOTS_slidev-theme
permalink: https://talks.m4dz.net/zero-build/
author: m4dz
twitter: m4d_z
info: >
  For many years, we have migrated all our DevTools to Node.js for the sake of
  simplicity: a common language (JS/TS), a huge ecosystem (NPM), and a powerful
  engine. In the meantime, we moved a lot of computation tasks to the
  client side thanks to PWA and JavaScript Hegemony.


  So we made Webapps for years, developing with awesome reactive frameworks and
  bundling a lot of dependencies. We progressively moved from our simple to
  complex app toolchains. We've become the new Java-like ecosystem. It sucks.


  It's 2021, we have a lot of new technologies to sustain our users'
  experience. It's time to have a break and rethink our tools rather than going
  faster and faster in the same direction. It's time to redesign the developer
  experience. It's time for a bundle-free developers’ environment. It's time to embrace
  a new front end building philosophy, still with our lovely JavaScript.


  Introducing Snowpack, Vite, and other Bare Modules tools concepts!
---

The Eternal Sunshine of the

---

# TL;DR

<v-clicks>

1. We're the only industry to ensure 30 years of backwards compatibility
2. You should upgrade your DevTools, now
3. It's no more than replacing a single file

</v-clicks>

---
layout: media
---

<Figure src="img/meme.jpg" caption="Modern Web Development"/>

---
layout: media
---

<Gif id="3orieJI3IdkKWIsAGA" caption="Web is 30 years old" class="h-4/5" />

---

# The Modern <mark>Front end</mark> Development Stack

- Templates Engines
- CSS Pre-processors
- PostCSS
- Reactive UI Framework
- Packer/Bundler
- Web Dev Server/Hot-Reload/HMR

---
layout: punch
---

Did you see
<mark>HTML/CSS/JS</mark> <br>
in the previous list?

---
layout: media
---

<Gif id="3og0ID5AW1SmPuG3u0" caption="npm run dev" class="h-4/5" />

---
layout: leaf
background: img/danist-8Gg2Ne_uTcM-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@danist07?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">贝莉儿 DANIST</a> on <a href="https://unsplash.com/s/photos/build?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a> -->


# Why Do We Compile Websites?

---
layout: punch
---

Developer eXperience is bloated, <br>
thanks to our <mark>DevTools</mark>

---

Back to the Future

# Coding in the Browser, the Antique Way

```html
<!DOCTYPE html>
<html lang="en">
  <p id="text"></p>
  <script src="main.js"></script>
</html>
```

```js
window.addEventListener('DOMContentLoaded', (e) => {
  document.getElementById('text').textContent = `Hello World!`
});
```

---

# Modules Everywhere

- Inherited from the IIFE pattern
  ```js
  (function(w, d) {
    let bud = 'World';

    w.addEventListener('DOMContentLoaded', (e) => {
      d.getElementById('text').textContent = `Hello ${bud}!`
    });
  })(window, document);
  ```
- CommonJS format vs. ES Modules
- Bundling for the Web (Browserify, etc.)

::linkroll::
- [MDN Glossary - IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)
- [Require.js - CommonJS / AMD](https://requirejs.org/docs/whyamd.html#commonjs)
- [Browserify - require in the browser](https://browserify.org/)
- [NPM & left-pad: Have We Forgotten How To Program?](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/)

---

# The Transpilers

- Inherited from ActiveScript and CoffeeScript
- Better doesn't mean simpler
- Syntactic sugar on JS
- Still only one JavaScript

<Gif id="3JNGvAym5kKzQrD4xt" class="h-2/5"/>

---

# The Browser-as-a-VM Era

Cross-platform binary with WebAssembly

```rust
mod utils;

use wasm_bindgen::prelude::*;

#[cfg(feature = "wee_alloc")]
#[global_allocator]
static ALLOC: wee_alloc::WeeAlloc = wee_alloc::WeeAlloc::INIT;

#[wasm_bindgen]
extern {
    fn alert(s: &str);
}

#[wasm_bindgen]
pub fn greet() {
    alert("Hello, wasm-game-of-life!");
}
```

---

# This is why we're now <br> *compiling* our Websites

<v-clicks>

- Modules
- Transpillers
- New formats to support (WASM...)
- <mark>Performance</mark> improvements

</v-clicks>

---
layout: punch
---

Web Evolved

<v-clicks>

We still rely on its foundations <small>(HTML/CSS/JS)</small>

But we need <mark>high-level</mark> tools daily

</v-clicks>

---
layout: leaf
background: img/sigmund-4CNNH2KEjhc-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Sigmund</a> on <a href="https://unsplash.com/s/photos/pipes?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a> -->

# The '21 Web Building Pipeline

---
layout: punch
---

Easier developers life <br>
means overly complex <br>
DevTools Stack

---

# The Usual Suspects

<v-clicks>

- Webpack: Pack every part of your app (JS, assets...)
- Rollup/Parcel: Bundle the logic
- Jest: Testing suite
- TypeScript: Improve the language
- Prettier: Reformat
- ESLint: Check the syntax
- NPM/Yarn: Manage dependencies
- any tools specific to your frameworks

</v-clicks>

---

**As a...**
- Front-end Developer

**I want...**
- a shitload of tools that mimic my browser features

**So I...**
- can wait eternally rather than coding my stuff

---
layout: punch
---

_Compiling_ for production <br>
should not be mandatory <br>
during <mark>development</mark>

---

# Web Developer Superpowers

- JavaScript Modules (ESM)
- Advanced Cache Policy
- HTTP/2

---

# Improving the ~~User~~ Developer eXperience

- Standardized ESM
- Superset of languages (TS, JSX...)
- Free from loading the whole NPM Registry locally
- Instant Startup!
- Built-in HMR support
- Extensible
- Focusing on codebase

---
layout: leaf
background: img/emre-karatas-Ib2e4-Qy9mQ-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@emrekaratas?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Emre Karataş</a> on <a href="https://unsplash.com/s/photos/speed?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a> -->

# Solving the bottleneck

---

# How does it work?

<v-clicks>

- Use native ESM support in the browser
- Tranform non-JS modules to ESM
- Cache Modules in the Browser
- Use HMR for on-the-fly updates
- Use HTTP[/2] features

</v-clicks>

---

# Dependencies

- Loaded from `node_modules` directly
- _Not_ bundled
- Can be dynamically loaded from a CDN
- Use ESM versions

<v-click>

```js
import confetti from 'canvas-confetti';

confetti.create(document.getElementById('canvas'), {
  resize: true,
  useWorker: true,
})({ particleCount: 200, spread: 200 });
```

</v-click>

---

# On-Request Build Oriented

<Figure src="./img/esm.3070012d.png" caption="The Developement Pipeline" class="h-4/5"/>

::linkroll::
- [Why Vite?](https://vitejs.dev/guide/why.html)
- [How Snowpack Works](https://www.snowpack.dev/concepts/how-snowpack-works)

---

# Why a Single File approach?

- Fast builds
- Deterministic
- Easy to Debug
- Dev speed unrelated to project size
- Better cache

---
layout: media
---

<Figure src="./img/snowpack-unbundled-example-3.png" caption="Bundled vs. Unbundled approach in Snowpack" class="h-5/5" />

---
layout: media
---

<Gif id="dGtf1UhMLrcLm" caption="Our Challengers" class="h-3/5" />

---
layout: 3-cols
class: sm
---

# The Challengers

::left::

## Snowpack

- The First of Its Kind
- Lightweight and fast
- Agnostic
- Webpack/Parcel support for builds
- Plugins API
- Highly configurable

::middle::

## Vite

- The Leader
- Compatible Vue/[P]React/Svelte/Lit
- `esbuild` for dev | Rollup for builds
- multi-Page support
- Library Mode
- CSS Code-Splitting
- Standard API

::right::

## WMR

- The Tiny Mouse
- Native import from NPM
- JSX Debug in Browser
- Native CSS Modules
- HMR for Static Assets
- Rollup for builds
- HTTP/2 for dev

---

# Vite, as-a-backend service

<video playsinline autoplay loop class="max-h-full min-w-full m-auto h-4/5">
  <source src="/backlight-simba-demo.webm" >
  <source src="/backlight-simba-demo.mp4" >
  <img src="/backlight-simba-demo.png" alt="" >
</video>

::linkroll::
- [Backlight.dev Design System IDE](https://backlight.dev/)

---
layout: 2-cols
---

::left::
## Pros

- Blazingly Fast
- Native HMR
- Quick preview even on large codebases
- MD Vue for embedding components

::right::
## Cons

- Error-prone on code analysis for deps
- No MDX native support
- MD Vue isn't standard
- Dedicated Worker for Vite previews
  ```
  preview
    -> service-worker
    -> vite worker
    -> service-worker
  -> preview
  ```

---
layout: leaf
background: img/caroline-selfors-r2jpr8MDw0I-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@cselfors?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Caroline Selfors</a> on <a href="https://unsplash.com/s/photos/packing?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a> -->

# Still Building in Prod.

---
layout: punch
---

You're <small>(probably)</small> not your <mark>end-user</mark>

---

# Behind the Hood

- Rollup/Parcel/esbuild
- Plugins Support
- Optimize for production
- Browserlist support for legacy browsers
- Code-splitting/Lazy-loading
- Treeshaking for ESM

::linkroll::
- [Rollup](https://rollupjs.org/guide/en/)
- [esbuild](https://esbuild.github.io/)

---

# The Treeshaking Mystery

<Gif id="3sZv" provider="gifer" class="h-4/5" />

::linkroll::
- [Benefits of dead code elimination during bundling](https://exploringjs.com/es6/ch_modules.html#_benefit-dead-code-elimination-during-bundling)

---

# Extending the Build

- Plugins Interface
- Snowpack: Custom API
- Vite/WMR: Rollup Plugins
- Support external asset types
- Allow types mix (MD Vue...)

---
layout: punch
---

It's a new generation of Devtools <br>
led by great **communities** <br>
(Skypack, Vue, Preact...)

---

# <emojione-waving-hand class="inline" /> ESM-Oriented Registries

- [Skypack](https://www.skypack.dev/)
- [ESM.sh](https://esm.sh/)
- [JSPM](https://jspm.org/)
- [UNPkG](https://unpkg.com/)

---

# <emojione-waving-hand class="inline" /> New Advanced <emojione-high-voltage class="inline" /> Tools

- [Vitepress](vitepress.vuejs.org/)
- [Slidev](https://sli.dev/)
- [Viteshot](https://viteshot.com/)

::linkroll::
- [Awesome Vite](https://github.com/vitejs/awesome-vite)

---

# Easily Plug it into your existing project

<v-clicks>

1. Imports will still work
2. Few adjustments on edges (`resolve.alias`...)
3. Update `npm scripts`
4. Add `vite.config.js`, and remove Webpack <emojione-party-popper class="inline" />
   ```js
   import { defineConfig } from 'vite';

   import plainText from 'vite-plugin-plain-text';
   import sprites from 'rollup-plugin-sprite';
   import reactRefresh from 'vite-plugin-react-refresh'

   export default defineConfig({
     /* ... */
   });
   ```

</v-clicks>

::linkroll::
- [kresus - Use Vite for bundling](https://framagit.org/kresusapp/kresus/-/merge_requests/1440)

---

> Who Controls the Past <br>
> Controls the Future

George Orwell *in* 1984
