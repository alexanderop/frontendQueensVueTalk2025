---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: All you need is (Love) Vue
layout: cover
info: |
  ## Vue For Beginners

  By Alexander Opalic — 2025

  Learn Vue from first principles. Build intuition, not memorization.

  Learn more at [alexop.dev](https://alexop.dev)
---

# All you need is (Love) Vue


---

# Agenda

<VClicks class="space-y-2 text-xl mt-6">

1. Why Vue exists  
2. What reactivity really means  
3. From plain HTML to automatic updates  
4. Building the core idea in 6 lines  
5. Components and local state  

</VClicks>

---
layout: two-cols
heading: About me
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
  <img class="w-75 rounded-full" src="https://avatars.githubusercontent.com/u/33398393?v=4" />
  <h2 class="mt-4">Alexander Opalic</h2>
</div>
</template>

<template v-slot:right>
<VClicks class="space-y-2 mt-10 text-xl h-full">

* Developer at Otto Payments  
* 7 years with Vue  
* Based near Munich, Germany  
* Blogger at alexop.dev  
* Talks on Vue, testing, GraphQL, AI

</VClicks>
</template>

---
layout: center
---

#  Why Vue Exists

---

# Evan You & The Birth of Vue

<VClicks class="space-y-2 text-xl">

- **Background**: Art history major, MFA in Design & Technology from Parsons
- **2012**: Joined Google Creative Labs prototyping browser experiments
- **The Problem**: Angular had great data binding but too much complexity
- **The Idea**: "What if I extract just the parts I like and make it lightweight?"
- **2013**: Started Vue as a personal experiment in his free time
- **Feb 2014**: Released Vue.js publicly — a framework by a designer, for developers

</VClicks>

---

# 11 Years of Growth: The Vue Ecosystem

<VClicks class="space-y-2 text-xl">

- **Vue Router**: Official routing solution, evolved alongside the core
- **State Management**: Vuex (2016) → Pinia (2022, now official)
- **Nuxt**: Meta-framework for SSR, SSG, and full-stack apps (2016+)
- **Vite**: Next-gen build tool created by Evan You (2020)
- **Official DevTools**: Browser extensions for debugging Vue apps

</VClicks>

---

<div class="flex justify-center items-center h-full">
  <iframe
    src="https://platform.twitter.com/embed/Tweet.html?id=590281695581982720&theme=dark"
    width="550"
    height="200"
    frameborder="0"
    scrolling="no"
    class="rounded-lg"
  ></iframe>
</div>

---

````md magic-move
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Counter Button</title>
  </head>
  <body>
    <button id="btn">Count: 0</button>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Counter Button</title>
  </head>
  <body>
    <button id="btn">Count: 0</button>

    <script>
      let count = 0;
      const btn = document.getElementById('btn');
    </script>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Counter Button</title>
  </head>
  <body>
    <button id="btn">Count: 0</button>

    <script>
      let count = 0;
      const btn = document.getElementById('btn');
      btn.addEventListener('click', () => {
        count++;
        btn.textContent = `Count: ${count}`;
      });
    </script>
  </body>
</html>
```
````


---

# The mental picture

When data changes, the UI should *react* automatically.  
No manual updates. No `document.querySelector()` acrobatics.  


---

# Vue to the rescue

````md magic-move
```vue
<template>
  <button>Count: 0</button>
</template>
```

```vue
<script setup>
</script>

<template>
  <button>Count: 0</button>
</template>
```

```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
  <button>Count: {{ count }}</button>
</template>
```

```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
  <button @click="count++">Count: {{ count }}</button>
</template>
```
````

<VClicks class="space-y-2 mt-4">

- Data lives inside `ref()`
- Template shows data directly
- Vue updates automatically when it changes

</VClicks>


---
layout: two-cols
heading: Single File Components
---

<template v-slot:default>

````md magic-move
```vue
<template>
  <div>Hello World</div>
</template>
```

```vue
<script setup>
import { ref } from 'vue'
const message = ref('Hello World')
</script>

<template>
  <div>{{ message }}</div>
</template>
```

```vue
<script setup>
import { ref } from 'vue'
const message = ref('Hello World')
</script>

<template>
  <div>{{ message }}</div>
</template>

<style scoped>
div {
  color: #ff6bed;
}
</style>
```
````

</template>

<template v-slot:right>
<div class="grid gap-6 mt-4">

<div v-click="0">
  <div class="text-2xl font-bold mb-2"><code>&lt;template&gt;</code></div>
  <div class="text-lg">Your HTML structure</div>
</div>

<div v-click="1">
  <div class="text-2xl font-bold mb-2"><code>&lt;script setup&gt;</code></div>
  <div class="text-lg">Your JavaScript logic</div>
</div>

<div v-click="2">
  <div class="text-2xl font-bold mb-2"><code>&lt;style&gt;</code></div>
  <div class="text-lg">Your CSS (optional)</div>
</div>

<div v-click="3" class="mt-4 text-xl opacity-80">
  Each <code>.vue</code> file = one component
</div>

</div>
</template>

---


<VuePlayground
height="460px"
url="https://play.vuejs.org/#eNp9kU1PAjEQhv/KpBc0EDDRE1mMSjjoQY167AXLgIVu27RTJNnsf3faldUD4daZ9yNPM4249368TyimoooqaE8QkZK/lVbX3gWCBgKuoYV1cDUM2DqQVjkbCZRLlmCW9YurS2mrSdfAWR4Ia2+WhDwBVJ+JyFm4U0ar3UyKkh0OpSgywDzPU2ia39a2LbFJl2NTNekLxUhQZIS13oy30Vlmb7I7t9ZeGwwvnjQjSsGNXb8US2Pc91PZUUg4Ou7VF6rdif02HvJOiteAEcMepeg1WoYNUicv3p/xwO9erN0qGXafEd8wOpMyY2d7SHbF2P98hfaxXEDbzUdcHAhtPH4qg2ZnW/xS8FXmZ77+h3s9vik5aVvR/gBvjaiO"
/>

---
layout: center
---


# Lets build our own Ref 

---
layout: two-cols
heading: Building our own Ref
---

<template v-slot:default>

````md magic-move
```js
const effects = new Set()
```

```js
const effects = new Set()

function effect(fn) {
  effects.add(fn)
  fn()
}
```

```js
const effects = new Set()

function effect(fn) {
  effects.add(fn)
  fn()
}

function ref(value) {
  return {
    get value() { return value },
    set value(v) {
      value = v
      effects.forEach(fn => fn())
    }
  }
}
```

```js
// usage
const count = ref(0)
effect(() => {
  console.log('render', count.value)
})
count.value++
```
````

</template>

<template v-slot:right>
<div class="grid gap-6 mt-8 text-lg">

<div v-click="0">
  <div class="text-2xl font-bold mb-2">Store effects</div>
  <div>Create a Set to track all functions that need to re-run when data changes</div>
</div>

<div v-click="1">
  <div class="text-2xl font-bold mb-2">Register effects</div>
  <div>The <code>effect</code> function adds a callback to the Set and runs it immediately</div>
</div>

<div v-click="2">
  <div class="text-2xl font-bold mb-2">Create reactive refs</div>
  <div>The <code>ref</code> function wraps a value with getter/setter. When the value changes, all effects re-run</div>
</div>

<div v-click="3">
  <div class="text-2xl font-bold mb-2">Use it!</div>
  <div>Create a reactive counter, register an effect, and watch it automatically update when count changes</div>
</div>

</div>
</template>

---
layout: center
---

# The Real Deal: Vue's Reactivity

---

<div class="text-center mb-8">
  <div class="text-3xl font-bold mb-4">Core Mental Model</div>
  <div class="text-2xl text-pink-400">"Reads <span class="text-white">track</span>, Writes <span class="text-white">trigger</span>"</div>
</div>

<div class="grid gap-8 mt-12 text-xl">

<div v-click="0">
  <div class="text-2xl font-bold mb-3">📖 When you READ</div>
  <div class="pl-4">
    Vue registers the current effect as a dependency for that value
  </div>
  <div class="pl-4 mt-2 opacity-70">
    <code>count.value</code> → "Effect A depends on count"
  </div>
</div>

<div v-click="1">
  <div class="text-2xl font-bold mb-3">✍️ When you WRITE</div>
  <div class="pl-4">
    Vue schedules all dependent effects to re-run
  </div>
  <div class="pl-4 mt-2 opacity-70">
    <code>count.value++</code> → Re-run Effect A (not B, C, D...)
  </div>
</div>

<div v-click="2" class="mt-6 border-t border-gray-700 pt-6">
  <div class="text-2xl font-bold mb-3">🔧 How Vue does it</div>
  <div class="grid grid-cols-2 gap-4 pl-4">
    <div><code>ref()</code> → <span class="opacity-70">.value getter/setter</span></div>
    <div><code>reactive()</code> → <span class="opacity-70">Proxy traps</span></div>
    <div class="col-span-2">Scheduler → <span class="opacity-70">Batches updates, prevents redundant re-runs</span></div>
  </div>
</div>

</div>

---

# watchEffect

```ts
import { ref, watchEffect } from 'vue'

const count = ref<number>(0)

watchEffect(() => {
  console.log(`Count changed: ${count.value}`)
})
```

---

<VuePlayground
height="460px"
url="https://play.vuejs.org/#eNp9Ustu2zAQ/JUFUSAOYksJ2l5c2Wib+pAe2qLtkYco1EpiQpEEH44NQf/eFWW7PgQ+CCB3Zpazo+3ZF2uzbUS2ZIUXTtoAHkO0oErdrDgLnrM117KzxgXowWE9h9cyiHZT1ygCDFA708EV9bjimmthtA8gTNQBViO90LF7Qree3V6P+Jl2NruG1Rp6roEE2huFmTLN7PE+qUVLFrBawrs+tcu2pYo4PFKbgb4in/ySO7oE7KwqA9INoKjkNh3o2N6tz+2m1uhgsytJgEVO+IFp1wlcQt8f/A9Dkdsj/BRDMBo+CyXFCyWTKDc3FM+DFg471KHIJ9JFyWJBkm/4lqTIJ+NFfjYOXX3YKwQvjMWKKkSaQqsNtavLTqr9Evzek2oR5Rx8qf3Co5P1p5Fmy6qSulnCHb1JlYHrg7PUpStdI/XCyaal4W+zjycWRTy+TE+yOW0C/aNaNtmzN5rWJWnHmTorFbqfNkj6h5xRftP4nJVKmdfvqRZcxPmxLloUL2/Un/1urHH2yyHZ3yJnJyyQSwwTvPnzA3d0PoGdqaIi9gXwN9J+xdHjRPsadUW2z3jJ7UNadErrr9/sAmp/HGo0OjKHxOeM9v3+wuj/7b7PPiQdJcqGf6vkKf4="
/>

---

layout: section

---

 # Components

---

# Local brains

<VClicks class="space-y-2 text-xl">

- Its a function with its own scope 
- Each component has its own state (`ref`s)  
- Each controls its own part of the DOM  
- Composition gives clarity  

</VClicks>

---

<VuePlayground
height="460px"
url="https://play.vuejs.org/#eNp9UcFOAjEU/JXaCxrYXRM9kYWohIMe1KjHXrA8sNBtm/YVSTb777bdBYmSvXXezDTz3tT03ph854GOaXmRZaSDJMumTJWOW2GQOEBvAhaV0RbJTHuFYMnK6ooM8qLD0TcIpqJ1BX0ACJWRC4SACCkPzuI/LIujlI4oOq7VSqzzjdMqZKujnlGuKyMk2BeDQivH6JgkJnILKfX3U5qh9TA6zPkX8O2Z+cbt44zRVwsO7A4YPXK4sGvAlp6/P8M+vI9kpZdeBnUP+QZOSx8ztrIHr5Yh9okupX1M9xRq/eHmewTlDkvFoFHZJD2j4bKzntV/497kt8nHVBOueFJM7Pd8mzWxsCJN12bbYTi+Q8KjnUwif3l91d/sp0fUitxxKfh2EpsK3uGQ0WkKEcLW3X9NUxat+k/rzQ+u4trn"
/>

---

<VuePlayground
height="460px"
url="https://play.vuejs.org/#eNqdU01v2zAM/SuELnGQIG62nQwn6Fbk0B22YutRF9ehE7W2ZOgjC2D4v4+SbC9th27oTeLjox6px459btvVySHLWG5KLVoLBq1roS7kYcOZNZxtuRRNq7SFDjRW0EOlVQMzos0m6EY5aVEP0Cod7r42JXFZKmksWGWLGja+TLK+mnugcrK0Qkk4FnJf460sNTYobXIqaocZSNc8oJ5DxyVE/iogsNhAOHDZc5mnUT1ppYvFpq0Li3QDyI8ftvfh3dJrgiRILOrhjtrMM+i6QVvf5ykRfBmijl1lxhba0jyuOINrMWqkwAvVBKfx1VfU9X9y8/RCPlvSF9DsKnFYPRol6Z/CIDgrVdOKGvX31k+Pvoma8IjHqDn162uIWe1wOcbLI5ZPf4k/mrOPcXan0aA+IWcTRuoPSNo8vPv5Dc90nsBG7V1N2W+AP9Co2nmNMe2L803ri7yg9jbYSMjDvdmdLUozNuWF+sw+5HNGhrp5o/U/cj+uPgUe+YOmeOHH93t9tHEH4VMJ3cAeKyHxTqvW5EFFgEbf0uPbJPg8MrERdiLt6DKQEnL6bPLGbBmtPbk/g5MS+5fFop/jNoVXny/UVC4Ztifkx+1ZLHzAq0mePbumEv9YpwdnLVW/LmtRPtHYJnqYnv+FMOuwU1FhTxWJmEbmK4v3vwHp241e"
/>

---

## layout: section
---

# The Essentials You’ll Use Daily

---

# Template syntax

<VClicks class="space-y-2 text-xl">

- `{{ value }}` — text binding  
- `@click="fn"` — event  
- `:class="isOn ? 'on' : 'off'"` — dynamic binding  
- `v-for="todo in todos" :key="todo.id"` — loops  
- `v-if` / `v-show` — conditions  
- `v-model="form.name"` — two-way binding  

</VClicks>

---

# Computed and watch

````md magic-move
```ts
import { ref } from 'vue'

const price = ref(10)
const qty = ref(3)
```

```ts
import { ref, computed } from 'vue'

const price = ref(10)
const qty = ref(3)

const total = computed(() => price.value * qty.value)
```

```ts
import { ref, computed, watch } from 'vue'

const price = ref(10)
const qty = ref(3)

const total = computed(() => price.value * qty.value)

watch(total, (t) => {
  console.log('total changed:', t)
})
```
````

<VClicks class="space-y-2 mt-4">

- `computed` caches automatically
- `watch` reacts to a single source

</VClicks>

---

# Simple form

```vue
<script setup>
import { ref } from 'vue'
const name = ref('')
const agree = ref(false)
</script>

<template>
  <input v-model="name" placeholder="Your name">
  <label><input type="checkbox" v-model="agree"> I agree</label>
  <p>Hello {{ name }} (agreed: {{ agree }})</p>
</template>
```

---

## layout: section

# 6) Minimal Setup

---

# Create a project

<VClicks class="space-y-2 text-xl">

- Use **Create Vue** (official tool)  
- Powered by **Vite**  
- TypeScript optional  

</VClicks>

```bash
npm create vue@latest
npm install
npm run dev
```

---

# Or just one file

````md magic-move
```html
<!doctype html>
<html>
  <head>
    <script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script>
  </head>
  <body>
    <div id="app"></div>
  </body>
</html>
```

```html
<!doctype html>
<html>
  <head>
    <script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script>
  </head>
  <body>
    <div id="app">
      <button @click="count++">Count: {{ count }}</button>
    </div>
  </body>
</html>
```

```html
<!doctype html>
<html>
  <head>
    <script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script>
  </head>
  <body>
    <div id="app">
      <button @click="count++">Count: {{ count }}</button>
    </div>

    <script>
      const { createApp, ref } = Vue
      createApp({
        setup() {
          const count = ref(0)
          return { count }
        }
      }).mount('#app')
    </script>
  </body>
</html>
```
````

---

## layout: section

# 7) Recap & Challenge

---

# What we learned

<VClicks class="space-y-2 text-xl">

- Data lives in refs  
- Templates react to data changes  
- Effects re-run automatically  
- Components isolate logic and state  

</VClicks>

---

# Quick challenge

Build a small tip calculator.

<VClicks class="space-y-2 mt-4">

- Inputs: amount and percent  
- Output: tip and total  
- Use `ref` and `computed`  

</VClicks>

<Callout type="info" class="mt-4">
Goal: make it update automatically — no manual DOM changes.
</Callout>

---

# Playground (tip calculator)

<VuePlayground
height="480px"
url="https://play.vuejs.org/#eNqNkM1qwzAQx79K5xlqCk2wQdQG1IH6QFFSSu4hvXbNJqW0vdRD8S9PXWJj7uTsvf+0ltgT98KNtxHFQFSg9sIRBKToZtKo1llP0IHFFfSw8raFgquFNNLU1gSCNjQwTfyyfEJ9bXmrXy4viypoqnI5j4/igbB1Y0HIH0C1vpl0XF/v+qvlKKbKuEmwrW71C9FQK5lNAyLkqh/ZESEHh0q9UM98EaNm9SvpS1bZ1S6N+cqVYT4oIZJLZgu1+XnJGOuNp39ZrrH5P/JulCpkU7x4D+i1KcGC18A7TgeeZr7nj5gNk+6m4fAZ+YLArJ8ag9wDNk7SPetn3OV9+ZZqvMdwQm7C+VRNNzT/2peB+8nj36v+7t+K7vSdML/oyJj9Oag=="
/>

---


<div class="flex justify-center items-center h-full">
  <Excalidraw
    drawFilePath="./example.excalidraw.json"
    class="w-[600px]"
    :darkMode="true"
    :background="false"
  />
</div>


---

## layout: section

# Q & A

---

# Thank You

<div class="text-center mt-8">
<Callout type="info">
Slides and links: [alexop.dev](https://alexop.dev)
</Callout>
</div>
```


