# vite-electron-quick

👻 A fast Simple Vite2 Vue3 and Electron 11.x template.

⚡️ If you want to **fast** create a `Vite 2 + Vue 3 + Electron 11.x` project:

🚀 Why not use this?

## quick install

```

npx create-vite-electron <project_name>

yarn create vite-electron <project_name>

```

## run

- yarn

- yarn dev

- yarn build

## change log

#### 210331

- Update `rollup-plugin-esbuild` version.

#### 210219

- resolve #6
- change vite config file (alias => resolve.alias)
- current version:
  - vite 2.0.1
  - electron 11.2.3

#### 210113

- fix Vite2 config bugs
- vue-router next use `hash mode` instead of `history mode`

#### 210108

- use Vite2
- use Electron 11.x

#### 201029

- fix build bug
- if build slowly, you can use electron mirror

#### 201026

- vite update, update `vite.config.ts` file
- add third lib `element-plus` import globally
- please note when using **NODE MODULE**, may need to change `vite.config.ts -> optimizeDeps.allowNodeBuiltins`
