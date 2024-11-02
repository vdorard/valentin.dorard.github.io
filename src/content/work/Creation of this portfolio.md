---
title: Creation of this portfolio
publishDate: 2019-10-02 00:00:00
img: /assets/logo_astro.jpeg
img_alt: logo astro
description: |
  Short paragraph about the creation of this portfolio 
tags:
  - Design
  - Dev
---

> ### Motivations 

In the last year of engineering student, I decided to develop a portfolio online to provide informations about the project I realised during my years as a student. I think it's a great way to stand out from others and to be able to desplay my work in a simple way.  

In this first ever blog post, I will go over the creation process of this website that can be followed as a tutorial.

> ### Technologies

For the creation of this portfolio, we will use GitHub and <strong><a href="https://astro.build/" target="_blank">Astro</a></strong> in order to publish and code our site. 

Astro is a website where you can found framework that suit your ambitions. You can also create page for many purpose (Portfolio, blog, marketing website).

GitHub will allow us to host our project for free. The page will be linked to your personnal or company account. If you already have a DNS address to your name (which you can buy online to DNS providers), you can set it as a custom URL.

--- 

> ## Starting our project : 

#### GitHub Initialisation  
To publish your creation, you should create a repository on GitHub. <strong>IMPORTANT</strong> : Your repository name must finish by ".github.io" in order to be detected as a website.
Then, clone it into your computer : 
```bash 
> cd /your_local_project_folder
> git clone https://www.github.com/<USERNAME>/<USERNAME>.github.io.git
```
#### Astro Initialisation

Go to the <strong><a href="https://astro.build/themes/" target="_blank">Astro's website</a></strong> website and select a Theme. If you want help to setup astro on your computer, follow this <strong><a href="https://docs.astro.build/en/getting-started/" target="_blank">tutorial</a></strong>.

Make sure to load your project into the file you just cloned. 

#### Setting your Astro Template as a GitHub page : 
We can deploy our Astro website using GitHub Actions.

* Copy/Paste and modify this block of code to your astro.config.mjs file.
```bash 
import { defineConfig } from 'astro/config'

export default defineConfig({
  site: 'https://astronaut.github.io',
})
```
This file should be located at the root of your project (in the original folder).

Customize it to fit your website’s URL.

* Create a new file in your project at .github/workflows/deploy.yml and paste in the YAML below.

Create the folders and the file. Then paste this code:

```bash
name: Deploy to GitHub Pages

on:
  # Trigger the workflow every time you push to the `main` branch
  # Using a different branch name? Replace `main` with your branch’s name
  push:
    branches: [ main ]
  # Allows you to run this workflow manually from the Actions tab on GitHub.
  workflow_dispatch:

# Allow this job to clone the repo and create a page deployment
permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout your repository using git
        uses: actions/checkout@v3
      - name: Install, build, and upload your site
        uses: withastro/action@v0
        # with:
            # path: . # The root location of your Astro project inside the repository. (optional)
            # node-version: 16 # The specific version of Node that should be used to build your site. Defaults to 16. (optional)
            # package-manager: yarn # The Node package manager that should be used to install dependencies and build your site. Automatically detected based on your lockfile. (optional)

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```

* On your Github Page, go to your repository's settings and find "Pages".

* Choose GitHub Action as the source of your site 

* Commit the workflow file ".yaml" and push it to your GitHub. 

* Check the website, it should be online ! 


### Customize as you pleased 

Now that you have setup your website, customize it ! you can add pages, pictures, and whatever you want !

You may understand basic of HTML5 and CSS in order to customize your website.