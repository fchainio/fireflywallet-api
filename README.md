# firefly wallet api

## Folders content

- `./src` folder contains the source code in TypeScript.

- `./lib` folder contains transpiled in es5 code. So, if you do not know how to use TypeScript - you can modify these files to change the result bundle later.

- `./dist` folder contains bundled JavaScript files which can be inlined into a page 

## Build & bundle

Before building or bundling your code you need to run `npm install` to install dependencies.

`package.json` contains some handy scripts to build or generate the bundle:
- `npm run compile` to compile TypeScript source code into JavaScript files (output will be in `./lib` folder)
- `npm run bundle-js` to bundle multiple JavaScript files into one bundle (it also bundle polyfills)
- `npm run build` to compile and bundle (it is a combination of all above commands)

NOTE: if you want to minify the bundle code, you need to set `ENV` environment variable to a value different from `development`.

For example:
```bash
export ENV=prod
npm run bundle-js # or npm run build
```

or

```bash
ENV=prod npm run bundle-js
```

or

```bash
ENV=prod npm run build
```
