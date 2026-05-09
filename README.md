# monaco-themes-exports-map

A demonstration repo for [exporting Monaco Theme'ss theme files via exports maps](https://github.com/brijeshb42/monaco-themes/issues/65).  This would support being able to import theme JSON files directly using ESM.

```js
import theme from 'monaco-themes/themes/Night Owl.json' with { type: 'json'};
```

## Setup

1. Clone the repo
1. Have NodeJS LTS installed (or run `nvm use`)
1. Run `npm ci`

## Demo

After running `npm ci`, patch-package should run, which applies a patch to monaco-theme's _package.json_ which adds an exports map entry for all the theme files

```json5
"exports": {
  ".": {
    "types": "./dist/index.d.ts",
    "import": "./dist/index.js",
    "require": "./dist/index.cjs"
  },
  "./themes/*": "./themes/*", # added this line
  "./dist/monaco-themes.js": "./dist/monaco-themes.js"
},
```

Run `npm run demo` to see the output of _index.js_:

```sh
➜  monaco-themes-exports-map git:(master) npm run demo                 

> monaco-themes-exports-map@1.0.0 demo
> node .

{
  theme: {
    base: 'vs-dark',
    inherit: true,
    rules: [
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object], [Object], [Object],
      [Object], [Object], [Object], [Object],
      ... 62 more items
    ],
    colors: {
      'editor.foreground': '#d6deeb',
      'editor.background': '#011627',
      'editor.selectionBackground': '#5f7e9779',
      'editor.lineHighlightBackground': '#010E17',
      'editorCursor.foreground': '#80a4c2',
      'editorWhitespace.foreground': '#2e2040',
      'editorIndentGuide.background': '#5e81ce52',
      'editor.selectionHighlightBorder': '#122d42'
    }
  }
}
```