# slidev-theme-happy

[![NPM version](https://img.shields.io/npm/v/slidev-theme-happy?color=3AB9D4&label=)](https://www.npmjs.com/package/slidev-theme-happy)

A Happy theme for [Slidev](https://github.com/slidevjs/slidev).

## Install

Add the following frontmatter to your `slides.md`. Start Slidev then it will prompt you to install the theme automatically.

<pre><code>---
theme: <b>happy</b>
---</code></pre>

Learn more about [how to use a theme](https://sli.dev/themes/use).

## Theme Config

- support logo config, logo size using `QueryString` syntax setting

```
themeConfig:
  logo: /node_modules/@slidev/client/assets/logo-title-horizontal.png?w-111px,h-40px
```

## Layouts

This theme provides the following layouts:

### Full `full`

Use all space to display content without any cropping

![full](https://i.imgur.com/zSdwPl6.png)

### Customized end page

End page to add `['🌈', '⚡️', '💥', '🥳', '🎉', '✨']` effect

![end](https://i.imgur.com/sGaXsVk.png)

## Components

This theme provides the following components:

### KeepScale

keeping the scaling

```html
<KeepScale class="h-400px w-868px">
  <img class="w-full h-full rounded-8px overflow-hidden" src="https://source.unsplash.com/collection/94734566/1920x1080" />
</KeepScale>
```

![keep scale](https://i.imgur.com/SdT9dPL.png)

### Speech

text to speech

```html
<Speech text="hello slidev" lang="en-US">
  <p>Hello Slidev</p>
</Speech>
```

![speech](https://i.imgur.com/BThbCL4.png)

## License

[MIT](LICENSE).
