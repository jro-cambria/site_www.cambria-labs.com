---
title: "How to build & deploy a site using MkDocs and Render"
tags: [meta, tools]
---
# How this site is built

## Overview
Edit and publish a website using your laptop or mobile device, using plaintext files. 

## Benefits
- Use your laptop, phone & tablet to edit website content
- Website source files are plain text files and are saved to a hosted repository
- Use a Markdown text editor to edit you website content
- Automatically publish updates to your website site when changes are saved to the repository

## Technology Stack
- Operating systems:
	- Laptop: MacOS
	- Phone: iPhoneOS
	- Tablet: iPadOS
- File Sync (between laptop & mobile device): iCloud
- Domain name provider (DNS): [NameCheap](https://namecheap.com/)
- Static site generator: [MkDocs](https://www.mkdocs.org/)
	- Site theme: [MkDocs-Material](https://squidfunk.github.io/mkdocs-material/)
- Content Repository: [GitHub](https://github.com/)
- Deployment platform: [Render](http://render.com/)
- Website Content editor: [Obsidian](https://obsidian.md/)

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
```
brew install git
git --version # verify
```


#### Install `python3`
```
brew install python3
python3 --version # verify
```


#### Install `pip3` Python package manager
```
brew install pip3
pip3 --version # verify
```


#### Install `mkdocs` and `mkdocs-material`
```
pip3 install mkdocs
mkdocs --version # verify

pip3 install mkdocs-material # Install theme
```


## Configure Dependencies
- Create a file `requirements.txt` in the root directory, containing:
```
mkdocs
mkdocs-material
```
Render uses this file when building the site to install `mkdocs` and dependenies.

## Setup Content Repository
- [Create a GitHub organization](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)
	- Example: `cambria-labs`
- [Create a new repository in GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository) where website content is stored
	- Example: `site_www.cambria-labs.com`

## Configure MkDocs
[MkDocs Documentation > Getting Started](https://squidfunk.github.io/mkdocs-material/getting-started/)
	- [MkDocs Documentation > Setup](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)
- Create a new `mkdocs` site at Local Content directory:

```
cd {Local Content Directory}
mkdocs new .
```

- Verify you can see your website:
	- Run `mkdocs serve` to run the local server
	- Visit the site in your browser: http://127.0.0.1:8000/

## Setup Git
- Initialize `git` repository in this folder: `git init`
- Add files to git, do an initial commit, push to repository:
```
{TODO: Add git commands here}
# Add new files to the repository
# Initial commit
# Add Remote Origin
# Test push using git cli
```

- Check GitHub to Verify content updates were saved to the repository
	- Example: https://github.com/cambria-labs/site_www.cambria-labs.com



## Configure Render to deploy site
### Connect Render with GitHub
- [Grant Render access to GitHub repositories](https://render.com/docs/github)

### Add new Site in Render using GitHub repository
- Render > New Static Site
- Choose your repository from GitHub
- Configure Render build command:
`pip install -r requirements.txt && mkdocs build`
- Set publish directory: `site` (this is the site `mkdocs build` creates)
- Save changes, and start a build
- Verify that the site builds on Render:
	- Check Render > Dashboard > {Site} > Events to see the build progress
- Once the Render build completes, verify you can view your site on Render's domain name
	- Example: https://cambria-labs-com.onrender.com/

### Connect domain name to Render
- Follow these instructions to add your domain name to Render
	- [Render Documentation > Configure DNS](https://render.com/docs/configure-namecheap-dns)
- Verify you can visit your site using domain name
	- Example: https://cambria-labs.com/

## Configure laptop to edit & publish content
### Setup & Configure Obsidian
- [Download & Install Obsidian app](https://obsidian.md/download)
- Add the Local Content directory  as a Vault in Obsidian
	- Browse to your Cloud drive, find the Obsidian folder, and choose your site's directory as a Vault
#### Setup & Configure GitHub Deskop (optional)
- [Download & Install GitHub Deskop](https://desktop.github.com/)
- In GitHub Deskop app, Add Local Repository, and choose the Local Content Directory
#### Perform a test edit & push
- In Obsidian, edit a text file (example, open `index.md` and add "Hello World")
- Open GitHub Deskop and verify that the changed file was detected
- Commit the change ("Added `Hello World`")
- Push the commit to the remote origin
#### Verify changes are published
- Check Render's dashboard, and verify that the site build began
- When the site build completes on Render, open your browser to your site's URL and verify that you see "Hello world" on the site

## Setup mobile device (iPhone/iPad) to edit and publish changes to the content repository on GitHub
- [Download & Install Working Copy.app](https://workingcopy.app/)
- In Working Copy, click the "+" button to add a repository
- Click "Link External Directory"
- Browse to your iCloud/Obsidian/{Site}
- To Verify, edit text in Obsidian.app ("Hello Universe"), switch to Working Copy, and you ought to see a change detected.
- Commit the change
- Push the change
	- Potential issues: 
		- SSH key not configured in GitHub
- Verify changes to the repository were detected by Render and were published to the public site

# Documentation TO-DO's
- How to Configure Remote origin in GitHub Desktop
- How Create SSH key on MacOS & add to GitHub user
- How to Create SSH key on iPhone Working Copy, add to GitHub repo Deploy keys, so Working Copy can push changes to the repository