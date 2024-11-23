# About

Slide Deck on Git Basics.

## Tool

We use the (node-based)
[Markdown presentation ecosystem (Marp)](https://github.com/marp-team/marp)
based on
[this template repository](https://github.com/yhatt/marp-cli-example?tab=readme-ov-file).

## Build the Presentation

Install VS-Code extension `marp` to have a real time build during development.

Install required node libraries with

```bash
npm i
```

Build the slides

```bash
npm run build
```

or alternatively, run the slides in local browser

```bash
npm run start
```

or [create a static pdf-file](https://pcotret.github.io/marp-to-pdf/) with

```bash
npx @marp-team/marp-cli main.md -o public/output.pdf --allow-local-files
```
