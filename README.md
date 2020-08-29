# Singular Public Documentation

This repository contains Singular framework's public documentation generated using [Fluorite](https://fluorite.js.org).

# Setup

  1. Install Fluorite globally: `npm install @chisel/fluorite -g`
  2. Inside root directory of this repo run `fl build` and `fl serve` to serve the docs on `localhost:6001`

# Deploy

  1. Clone this repository twice into two different directories sibling of each other called: `docs-src` and `docs-dist`
  2. Inside `docs-dist`, switch to branch `gh-pages`: `git checkout -b gh-pages`
  3. Inside `docs-src`, run: `fl build`
  4. Commit and push the changes inside `docs-dist`

# Domain Setup

  1. Create a file in `docs-dist` named `CNAME` which contains your domain name.
  2. Create a CNAME record with your DNS provider that points the domain added in the file to `<user>.github.io` (where user is your username).
  3. Make sure to add `"exclusions": ["CNAME"]` to `flconfig.json` so the file doesn't get deleted the next time the documentation is generated.
