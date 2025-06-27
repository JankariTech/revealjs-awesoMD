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

Create a folder name `templates` in your project root directory where you can add your templates file.
Name your template file as `<template-name>-template.html`. 

```text
<project-root-directory>
└── templates
    ├── <template-name-1>-template.html
    ├── <template-name-2>-template.html
    └ ...
```

If the `templates` folder is not in the root directory, then the path to the templates folder can be set as below:
```javascript
const awesoMd = RevealAwesoMD()
awesoMd.setBaseUrl(<path-to-templates-folder>)
Reveal.initialize({
    plugins: [ awesoMd ]
})
```
