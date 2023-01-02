---
title: "How to build & deploy a site using MkDocs and Render"
tags: [meta, tools]
---

## Overview
Edit and publish a website using your laptop or mobile device, using plaintext files. 

## Benefits
- Use laptop (MacOS), phone (iPhone), & tablet (iPad) to edit website content
- Website source files are plain text files (Markdown)
- Website source files are stored in a hosted repository (GitHub)
- Use Markdown text editor (Obsidian) to edit website content
- Website automatically publishes when changes are made to content (GitHub + Render)

## Technology Stack
- Operating systems:
	- Laptop: MacOS
	- Phone: iPhoneOS
	- Tablet: iPadOS
- File Sync: iCloud
- Domain name provider (DNS): [NameCheap](https://namecheap.com/)
- Static site generator: [MkDocs](https://www.mkdocs.org/)
- Site theme: [MkDocs-Material](https://squidfunk.github.io/mkdocs-material/)
- Content Repository: [GitHub](https://github.com/)
- Deployment platform: [Render](http://render.com/)
- Code editor: [VSCode](https://code.visualstudio.com/)
- Content editor: [Obsidian](https://obsidian.md/)

## Assumptions
- Ensure you have accounts setup for:
	- NameCheap
	- GitHub
	- Render
- File locations
	- Repository URL: https://github.com/{organization}/{Site}
	- Local Content Directory: `iCloud/Obsidian/{Site}`
		- Example: `/Users/jro/Library/Mobile Documents/iCloud~md~obsidian/Documents/Cambria_Public`
	- Obsidian Vault: `iCloud/Obsidian/{Site}`


## Configure laptop (MacOS)
### Install tools
#### Install Homebrew package manager
- [Homebrew docs](https://brew.sh/)
	- Verify: `brew --version`

#### Install `git`
- `brew install git`
	- Verify: `git --version`

#### Install `python3`
- `brew install python3`
	- Verify: `python3 --version`

#### Install `pip3` Python package manager
- `brew install pip3`
	- Verify: `pip3 --version`

#### Install `mkdocs` and `mkdocs-material`
- `pip3 install mkdocs`
	- Verify: `mkdocs --version`
- `pip3 install mkdocs-material`

## Configure Dependencies
Add `requirements.txt` to root directory. Render uses this file when building the site to install `mkdocs` and dependenies.
```
mkdocs
mkdocs-material
```

## Setup Content Repository
- Create a GitHub organization
	- https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch
- Create a new repository in GitHub where website content is stored
	- https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository

## Configure MkDocs
Create a new `mkdocs` site at Local Content directory
- [MkDocs Documentation > Getting Started](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [MkDocs Documentation > Setup](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)

```
cd {Local Content Directory}
mkdocs new .
```

Verify you can see your website:
- Run `mkdocs serve` to run the local server
- Visit the site in your browser: http://127.0.0.1:8000/

Initialize `git` repository in this folder:
`git init`

Add files to git, do an initial commit, push to repository
`{TODO: Add git commands here}`

Verify content made it to GitHub repository.
- Example: https://github.com/cambria-labs/site_www.cambria-labs.com

## Configure Render
### Integrate Render with GitHub
- [Grant Render access to GitHub repositories](https://render.com/docs/github)

### Automatically Deploy site upon changes
#### Configure Site on Render
- Render > New Static Site
- Choose your repository from GitHub
- Render build command:
`pip install -r requirements.txt && mkdocs build`
- Publish directory: `site`
- Verify that the site builds on Render:
	- Render > Dashboard > {Site} > Events
- Verify you can view your site on Render's domain name
	- Example: https://cambria-labs-com.onrender.com/

### Connect domain name to Render
- [Render Documentation > Configure DNS](https://render.com/docs/configure-namecheap-dns)
- Verify you can visit your site using domain name
	- Example: https://cambria-labs.com/

## Setup laptop to edit & publish content
### Setup & Configure Obsidian
- [Download & Install Obsidian app](https://obsidian.md/download)
- Add the Local Content directory (in iCloud) as a Vault in Obsidian
#### Setup & Configure GitHub Deskop (optional)
- [Download & Install GitHub Deskop](https://desktop.github.com/)
- In GitHub Deskop app, Add Local Repository, and choose the Local Content Directory
#### Perform a test edit & push
- In Obsidian, edit a text file (example, add "Hello World" to `index.md`)
- Open GitHub Deskop and verify that the changed file was detected