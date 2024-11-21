# About

Slide Deck on Git Basics.

## Tool Stack

- [slides](https://github.com/maaslalani/slides)
  - Go-Lang
  - ❌
    - too basic
- [present](https://github.com/vinayak-mehta/present)
  - Python
  - ❌
    - Font scaling in terminal is bad
    - Not pdf support
- [mdx-deck](https://github.com/jxnblk/mdx-deck)
  - node
  - ❌
    - Could not resolve error
      ```/home/julian/git/git_basics_slides/mdx_deck/node_modules/gatsby-recipes/dist/graphql-server/server.js:52
      var remarkMdx = require('remark-mdx');
      ^
      Error [ERR_REQUIRE_ESM]: require() of ES Module /home/julian/git/git_basics_slides/mdx_deck/node_modules/gatsby-recipes/node_modules/remark-mdx/index.js from
      /home/julian/git/git_basics_slides/mdx_deck/node_modules/gatsby-recipes/dist/graphql-server/server.js not supported.
      Instead change the require of index.js in /home/julian/git/git_basics_slides/mdx_deck/node_modules/gatsby-recipes/dist/graphql-server/server.js to a dynamic
      import() which is available in all CommonJS modules.
      at Object.<anonymous> (/home/julian/git/git_basics_slides/mdx_deck/node_modules/gatsby-recipes/dist/graphql-server/server.js:52:17) {
      code: 'ERR_REQUIRE_ESM'
      }
      ```
- [pandoc](https://pandoc.org/chunkedhtml-demo/10-slide-shows.html)
  - pandoc installed with conda or `apt-get`
- [marp](https://github.com/yhatt/marp-cli-example?tab=readme-ov-file)
  - node
  - Install VS-Code extension `marp`
  - Create repository based on this [template-link](https://github.com/yhatt/marp-cli-example/generate)
  - Enable Github pages if required (Note: Not pretty)
  - Start / build using npm
    ```bash
    npm i
    npm run start
    npm run build
    ```
