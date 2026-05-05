# RevealJs AwesoMD
A plugin for [reveal.js](https://revealjs.com/) that support markdown with metadata.

# Setup
To use the plugin configure reveal.js plugin as:
```javascript
Reveal.initialize({
    hash: true,
    // ...

    plugins: [ RevealAwesoMD ]
    // ...
});
```

And add the following script tag in `index.html` file:
```html
<script src="plugin/awesoMD/awesoMD.js"></script>
```

# Adding Templates

Create your template file as `<template-name>-template.html`. Make sure that all the slide templates are inside same directory.

**Option 1: Using Slide Templates**
```markdown
---
slide: title-content
---
```
This will load as `title-content-template.html`

**Option 2: Using Blob URL**
You can also pass a blob URL.

Blob URL format
```markdown
blob:<origin>/<uuid>?template=<template_name>
```

```markdown
---
slide: blob%3Ahttps%3A%2F%2Fexample.org%2F40a5fb5a-d56d-4a33-b4e2-0acf6a8e5f64%3Ftemplate%3Dmytemplate
---
```

Or using inline metadata:

```markdown
# My Slide ::slide:blob%3Ahttps%3A%2F%2Fexample.org%2F40a5fb5a-d56d-4a33-b4e2-0acf6a8e5f64%3Ftemplate%3Dmytemplate
```

**Important Notes:**
- The entire blob URL must be URL-encoded. Use `encodeURIComponent` to encode the full URL.
- Add a query parameter `?template=<template-name>` at the end when you want to explicitly control the slide's CSS class name.
- If the `template` parameter is present, only its value will be used as the slide's CSS class name.
- If the `template` parameter is omitted, the decoded blob URL is used as the source for the slide's CSS class name.
- The blob URL is always used for fetching the template HTML.

> [!NOTE]
> Slide names and fallback class names are sanitized to ASCII characters. In addition to letters and digits, sanitized names may include `-`, `_`, `.`, and `%`; for blob URL fallback class names, `:` and `/` may also be preserved. Special characters including umlauts (äöüß), accents (éñç), and non-Latin scripts will be transliterated or removed. For best results, use simple Latin filenames.

```text
<project-root-directory>
└── <templates-folder>
    ├── <template-name-1>-template.html
    ├── <template-name-2>-template.html
    └ ...
```

The path to the templates folder can be set as below:
```javascript
const awesoMd = RevealAwesoMD()
awesoMd.setBaseUrl(<path-to-templates-folder>)
Reveal.initialize({
    plugins: [ awesoMd ]
})
```
