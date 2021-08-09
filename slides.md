---
title: Zero Build Pipeline
theme: ../divRIOTS_slidev-theme
permalink: https://talks.m4dz.net/zero-build/
author: m4dz
twitter: m4d_z
info: >
  For many years, we have migrated all our DevTools to Node.js for the sake of
  simplicity: a common language (JS/TS), a large ecosystem (NPM), and a powerful
  engine. In the meantime, we moved a lot of computation tasks to the
  client-side thanks to PWA and JavaScript Hegemony.


  So we made Webapps for years, developing with awesome reactive frameworks and
  bundling a lot of dependencies. We progressively moved from our simple to
  complex apps toolchains. We've become the new Java-like ecosystem. It sucks.


  It's 2021, we've got a lot of new technologies to sustain our Users'
  eXperience. It's time to have a break and rethink our tools rather than going
  faster and faster in the same direction. It's time to redesign the Developer
  eXperience. It's time for a bundle-free dev environment. It's time to embrace
  a new frontend building philosophy, still with our lovely JavaScript


  Introducing Snowpack, Vite, and other Bare Modules tools concepts!
---

The Eternal Sunshine of the

<!--

-->

---

<Figure src="img/meme.jpg" caption="Modern Web Development" class="h-4/5"/>

---

# The Modern <mark>Front-end</mark> Development Stack

- Templating Engines
- CSS Pre-processors
- PostCSS
- Reactive UI Framework
- Packer/Bundler
- Web Dev Server/Hot-Reload/HMR

---
layout: punch
---

Did you see <br>
<mark>HTML/CSS/JS</mark> <br>
in that list?

---

<Gif id="3og0ID5AW1SmPuG3u0" caption="npm run dev" class="h-4/5" />

---
layout: punch
---

Developer eXperience <br>
is bloated, thanks to <br>
our <mark>DevTools</mark>

---
layout: leaf
background: img/danist-8Gg2Ne_uTcM-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@danist07?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">贝莉儿 DANIST</a> on <a href="https://unsplash.com/s/photos/build?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
   -->

# Why Do We Compile Websites?

---

Back to the Future

# Using JS in the Browser, the Antique Way

```html
<html>
  <script src="main.js"></script>
  <p id="text"></p>
</html>
```

```js
window.addEventListener('DOMContentLoaded', (e) => {
  document.getElementById('text').textContent = `Hello World!`
});
```

---

From JS IIFE to JS Modules

```js
(function(w, d) {
  let bud = 'World';

  w.addEventListener('DOMContentLoaded', (e) => {
    d.getElementById('text').textContent = `Hello ${bud}!`
  });
})(window, document);
```

::linkroll::
- [MDN Glossary - IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)

---

Back to the Future

# AMD <small>vs</small> CommonJS

```js
define(['jquery'] , function ($) {
    return function () {};
});
```

```js
var $ = require('jquery');
exports.myExample = function () {};
```

::linkroll::
- [Require.js - CommonJS / AMD](https://requirejs.org/docs/whyamd.html#commonjs)

---

Bandwith Matters

# How to Keep Performances on Tracks <br> When loading a bunch of modules?

---

Back to the Future

# Browserify

```js
const uniq = require('uniq');
let data = [1, 2, 2, 3, 4, 5, 5, 5, 6];

console.log(uniq(data));
```

```sh
$ npm install uniq
$ browserify main.js -o bundle.js
```

::linkroll::
- [Browserify - require in the browser](https://browserify.org/)

---
layout: punch
class: sm
---

The _modules_ pattern led to <br>
**Registries** like NPM, distributing <br>
more and more small chunks of code

::linkroll::
- [NPM & left-pad: Have We Forgotten How To Program?](https://www.davidhaney.io/npm-left-pad-have-we-forgotten-how-to-program/)

---

Moving to WebApps

# The Assets Challenge

- Different types (images, fonts, styles...)
- Templates
- Styles Processors (Sass, PostCSS...)
- Statics (`.well-known`...)

---

# We didn't speak about...

<Gif id="3JNGvAym5kKzQrD4xt" caption="Transpilers" class="h-4/5"/>

---

<Figure src="img/Super-Size-Me-COVER.jpg" caption="The (still valid) WebPerf Challenge" class="w-3/5"/>

---
layout: punch
---

**This** is why we're now <br>
_compiling_ our Websites

---
layout: punch
class: sm
---

Web Evolved, <br>
we still rely on tough foundations (HTML/CSS/JS) <br>
but we need <mark>high-level</mark> tools daily

---
layout: leaf
background: img/sigmund-4CNNH2KEjhc-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Sigmund</a> on <a href="https://unsplash.com/s/photos/pipes?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
   -->

# The '21 Web Building Pipeline

---

# Step 1: Creating your app

```sh
$ npx preact-cli create default my-preact-app
```

```sh
$ npx @vue/cli create my-vue-app
```

```sh
$ npx degit sveltejs/template my-svelte-app
```

---

# Step 2: Scaffold components

<v-clicks>

1. Add JS basics
2. Write the template
3. Style it
4. Code JS logics

</v-clicks>

---

# Then...

- Require a bunch of modules for some components
- Add Routing/Store/... parts
- Go to scaffolding new components and repeat
- Be mad at internal tools configuration
- _Finally_ get something working
- Make the project more complex
- Dedicate a team to _operations_ <br>
  thanks to those damned dependencies

---

# Finally...

Still wait 10-20 seconds each time you save a file

---

# The Usual Suspects

<v-clicks>

- Webpack: Pack every part of your apps (JS, assets...)
- Rollup / Parcel: Bundle the logics
- Jest: Testing suite
- TypeScript: Improve the language
- Prettier: Reformat
- ESLint: Check the syntax
- NPM/Yarn: Manage dependencies
- any tools specific to your frameworks

</v-clicks>

---
layout: punch
---

Easier developers life <br>
means overly complex <br>
DevTools Stack

---
layout: punch
---

_Compiling_ for production <br>
should not be mandatory <br>
during <mark>development</mark>

---

# ~~User~~ Developer eXperience

Browsers capabilities:

- JavaScript Modules (ESM)
- WebAssembly
- Advanced Cache Policy
- HTTP/2

---

**As a...**
- Front-end Developer

**I want...**
- a shitload of tools that mimic my browser features

**So I...**
- can wait eternally rather than coding my stuff

---

# Developer Needs

- Standard: ESM
- Superset of languages (TS, JSX, etc)
- *Not* loading half of NPM locally
- Instant Startup!
- Built-in HMR
- Extensible stack
- Focusing on Dev | Bundling on Prod

---
layout: leaf
background: img/emre-karatas-Ib2e4-Qy9mQ-unsplash.jpg
---
<!-- Photo by <a href="https://unsplash.com/@emrekaratas?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Emre Karataş</a> on <a href="https://unsplash.com/s/photos/speed?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
   -->

# Solving the Bottleneck

---
layout: punch
---

The Bare-Modules Dev Trend

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

# Build on Request

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
- Multi-Page support
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

# Vite, IRL

<Figure src="img/backlight.png" caption="Backlight.dev Design Systems IDE" class="h-4/5" />

::linkroll::
- [Backlight.dev Design System IDE](https://backlight.dev/)

---

# Where is Vite?

<Gif id="xUPGcJU55vuGH8Hfeo" class="h-2/5" />

- Live Pages Rendering
- Documentation
- Slides

::linkroll::
- [Vitepress](vitepress.vuejs.org/)
- [Sli.dev](https://sli.dev/)
- [Astro](https://astro.build/)

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
- Dedicated worker for Vite previews
  ```
  preview
    -> service-worker
    -> vite-worker
    -> service-worker
  -> preview
  ```

---

# Why still Building?

<Figure src="img/snowpack-build-example.png" caption="Snowpack build example" class="w-3/5"/>

::linkroll::
- [Vite Building for Production](https://vitejs.dev/guide/build.html)

---

# Behind the Hood

- Rollup/Parcel/esbuild
- Plugins Support
- Optimize for production
- Browserlist support for legacy browsers
- Code-splitting/Chunks Lazy-loading
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
- Allow mixin types (MD Vue...)

---
layout: punch
---

Who Controls the Past <br>
Now Controls the Future

::linkroll::
- [1984, Georges Orwell](http://www.george-orwell.org/1984/index.html)

---
layout: punch
class: sm
---

It's a new generation of Devtools, <br>
lead by great **communities** <br>
(Skypack, Vue, Preact...)

---
layout: punch
---

Say <twemoji-waving-hand class="inline" /> to ESM Registries

::linkroll::
- [Skypack](https://www.skypack.dev/)
- [ESM.sh](https://esm.sh/)
- [JSPM](https://jspm.org/)
- [UNPkG](https://unpkg.com/)

---

# Easily Plug it into your existing project

<v-clicks>

1. Forget Webpack
2. Imports will still work
3. Few adjustments on edges (`resolve.alias`...)
4. Update `npm scripts`

</v-clicks>
