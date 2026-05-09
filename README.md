# monaco-themes-exports-map

A demonstration repo for Monaco Themes with themes in the exports map.  This would support being able to import theme JSON files directly using ESM.

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
  "./themes/*": "./themes/*", # add this line
  "./dist/monaco-themes.js": "./dist/monaco-themes.js"
},
```

Run `npm run demo` to see it in action.