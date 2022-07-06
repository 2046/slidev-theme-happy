---
theme: ./
layout: full
themeConfig:
  logo: /node_modules/@slidev/client/assets/logo-title-horizontal.png?w-111px,h-40px
---

# A Happy Slidev Theme

<div class="pt-12 text-center">
  <span @click="next" class="px-2 p-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<style>
  .slidev-page-1 {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .slidev-page-1 h1 {
    text-align: center;
    font-size: 3.75rem;
  }
</style>
---

# What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)


---

# Navigation

Hover on the bottom-left corner to see the navigation's controls panel

### Keyboard Shortcuts

|     |     |
| --- | --- |
| <kbd>space</kbd> / <kbd>tab</kbd> / <kbd>right</kbd> | next animation or slide |
| <kbd>left</kbd>  / <kbd>shift</kbd><kbd>space</kbd> | previous animation or slide |
| <kbd>up</kbd> | previous slide |
| <kbd>down</kbd> | next slide |

---
layout: image-right
image: 'https://source.unsplash.com/collection/94734566/1920x1080'
---

# Code

Use code snippets and get the highlighting directly!

```ts
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: Partial<User>) {
  const user = getUser(id)
  const newUser = { ...user, ...update }
  saveUser(id, newUser)
}
```

---

# KeepScale

Keeping the Scaling

<KeepScale class="h-400px w-868px">
  <img class="w-full h-full rounded-8px overflow-hidden" src="https://source.unsplash.com/collection/94734566/1920x1080" />
</KeepScale>

---

# Speech

Text to Speech

<div class="text h-80">
  <Speech text="hello slidev" lang="en-US">
    <p>Hello Slidev</p>
  </Speech>
</div>

<style>
  .text {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .text p {
    font-size: 5.75rem;
    font-family: Avenir Next;
  }
</style>
