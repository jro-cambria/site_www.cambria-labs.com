---
title: "How to build & deploy a site using MkDocs and Render"
tags: [meta]
---

## Technology Stack
- Domain name provider: [NameCheap](https://namecheap.com/)
- Static site generator: [MkDocs](https://www.mkdocs.org/)
- Site theme: [MkDocs-Material](https://squidfunk.github.io/mkdocs-material/)
- Repository: [GitHub](https://github.com/)
- Deployment platform: [Render](http://render.com/)
- Code editor: [VSCode](https://code.visualstudio.com/)
- Content editor: [Obsidian](https://obsidian.md/)

## Configure Local workstation
### Install tools
- Install `brew`
- Install `git`
- Install `python3`
- Install `pip3`
- Install `mkdocs` & `mkdocs-material`

## Configure Dependencies
Add `requirements.txt` to root directory:
```
mkdocs
mkdocs-material
```

## Setup Repositories
- Create a new repository in GutHub

## Configure MkDocs
- [MkDocs Documentation > Getting Started](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [MkDocs Documentation > Setup](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)

## Configure Render
### Integrate Render with GitHub
- [Grant Render access to GitHub repositories](https://render.com/docs/github)

### Automatically Deploy site upon changes
- Render build command:
`pip install -r requirements.txt && mkdocs build`
- Publish directory: `site`

### Setup Domain name
- [Render Documentation > Configure DNS](https://render.com/docs/configure-namecheap-dns)