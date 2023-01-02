---
title: "How to build & deploy a site using MkDocs and Render"
tags: [meta, tools]
---

## Benefits
- Website source files are plain text files (Markdown)
- Use Markdown text editor (Obsidian) to edit website content
- Website source files are stored in a hosted repository (GitHub)
- Website automatically publishes when changes are made to content

## Limitations / Issues
- Obsidian mobile app can't open files in Google Drive (only iCloud folders, or Obsidian sync)

## Technology Stack
- Workstation operating system: MacOS
- Fileshare: Google Drive
- Domain name provider: [NameCheap](https://namecheap.com/)
- Static site generator: [MkDocs](https://www.mkdocs.org/)
- Site theme: [MkDocs-Material](https://squidfunk.github.io/mkdocs-material/)
- Repository: [GitHub](https://github.com/)
- Deployment platform: [Render](http://render.com/)
- Code editor: [VSCode](https://code.visualstudio.com/)
- Content editor: [Obsidian](https://obsidian.md/)



## Configure Local workstation
### Install tools
#### Install Homebrew package manager
- [Homebrew docs](https://brew.sh/)
- Verify `brew` is installed: `brew --version`

#### Install `git`
- `brew install git`

#### Install `python3`
- `brew install python3`

#### Install `pip3` Python package manager
- `brew install pip3`

#### Install `mkdocs` and `mkdocs-material`
- `pip3 install mkdocs`
- `pip3 install mkdocs-material`

## Configure Dependencies
Add `requirements.txt` to root directory. Render uses this to build the site.
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

# Editing Site Content
## On MacOS
- Open 