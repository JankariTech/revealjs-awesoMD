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

> [!NOTE]
> Slide names are sanitized to ASCII-characters (a-z, A-Z, 0-9, -, _), Special characters including umlauts (äöüß), accents (éñç), and non-Latin scripts will be transliterated or removed. For best results, use simple Latin filenames.

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
