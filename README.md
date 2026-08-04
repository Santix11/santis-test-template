# Custom React Native Template — Setup Guide

This guide walks through creating your own reusable React Native template/boilerplate, similar to `santis-world-template`.

## 1. Create the template package

```bash
mkdir your-template-name
cd your-template-name
npm init -y
```

Open the generated `package.json` and:
- Remove/modify fields as needed (description, author, license, etc.)
- Add the following so only the template files are published/used:

```json
"files": [
  "template",
  "template.config.js"
]
```

## 2. Create the template config

Create a file named `template.config.js` in the root:

```js
module.exports = {
  placeholderName: 'SantisWorld',
  templateDir: './template',
};
```

## 3. Match the placeholder name

`placeholderName` should match the name of the project you scaffold in the next step (it doesn't have to match your final project name later — this is just the name used internally when generating the template).

## 4. Scaffold the React Native app into the template directory

From the project root:

```bash
npx @react-native-community/cli init SantisWorld --directory template
```

This creates a fresh bare React Native app inside `./template`.

## 5. Fix a known CLI/npm issue with `.gitignore`

The RN CLI generates a `.gitignore` inside `template/` that can get excluded when packaging, since npm ignores `.gitignore` files by default when publishing. Rename it so it's preserved:

```bash
mv template/.gitignore template/_gitignore
```

To verify it's there:

```bash
ls -la template
```

> Reference: [restackio/examples-typescript#16](https://github.com/restackio/examples-typescript/pull/16)

Note: when your template generator copies these files into a new project, it should rename `_gitignore` back to `.gitignore` at generation time.

## 6. Build your boilerplate code

Add your actual folder structure, design system, navigation setup, state management, and any other opinionated defaults inside `template/` — this is the code every new project scaffolded from this template will start with.