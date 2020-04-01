# Jekyll Tutorial

The objective of this tutorial is to introduce [Jekyll](https://jekyllrb.com/) and show you how to build a website that you can host on GitHub for free.

[<img src="https://jekyllrb.com/img/logo-2x.png" width="200">](https://jekyllrb.com/)

## Requirements

To follow all of the steps in this tutorial you will need a [GitHub](https://github.com/) account. It is possible to run everything locally and deploy your website on a different server, but everything will presented under the assumption that you already have a GitHub account.

## Installation

Before starting you will have to install Jekyll. Jekyll is written in [Ruby](https://www.ruby-lang.org/en/downloads/) and therefore your system must have Ruby installed in order to build Jekyll. With Ruby installed the installation of Jekyll should simply be:

```bash
gem install jekyll bundler
```

Please see the [installation instructions](https://jekyllrb.com/docs/installation/) on the Jekyll website for more details.

## An example website in 5 min

Now that you have Jekyll installed let's make a quick website to see how easy it is. We we will go everything in more detail afterwards.

### Step 1 - Create a new repository

On your GitHub account either [fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) this repository or create a new one.

> If you choose to create a new repository be sure to click the `Add .gitignore` button at the bottom and scroll down to `Jekyll`.

Now clone your repository. *e.g.*

```bash
git clone https://github.com/<USERNAME>/jekyll_tutorial.git
```

### Step 2 - Create a gh-pages branch

Create and checkout a new branch called `gh-pages`.

```bash
git checkout -b gh-pages
```

> `gh-pages` is a special branch name used to idetify [GitHub Pages](https://pages.github.com/) content. It is, however, possible to allow any branch to host GitHub pages if you want.

### Step 3 - Jekyll quickstart

Next we will run through the [Jekyll quickstart](https://jekyllrb.com/docs/) instructions with some minor changes.

You will need run these commands in your local repository directory.

> Otherwise, you can run the standard quickstart commands and copy the outputs to this directory. Be careful to copy all hidden files!

First, we create a new Jekyll site in the current directory.

```bash
jekyll new . --force
```

Then, we will launch the Jekyll local server.

```bash
bundle exec jekyll serve
```

You can view the website at the address specified by `Server address:`.

Play around a bit then close the server by typing `ctrl+c`.

### Step 4 - Basic configuration

We need to add some basic information about our website, in particular where it will be deployed.

Open the `_config.yml` file and update update the entries `url` and `baseurl` (repository name) to those of your GitHub repository. *e.g.* If you forked this repository they will be:

```yaml
baseurl: /jekyll_tutorial
url: https://<USERNAME>.github.io/
```

> You can update the other entries if you want, just leave `theme` alone for now.

Here is the content I will use for this demonstration.

```yaml
title: Yoda's House
email: yoda@force.com
description: >-
  Very good my site is!
baseurl: /jekyll_tutorial
url: https://sfarrens.github.io/
twitter_username: yoda
github_username:  yoda

# Build settings
theme: minima
plugins:
  - jekyll-feed
```

Now relaunch the Jekyll server and you can keep it running for the next step.

```bash
bundle exec jekyll serve
```

You can see where some of the information is displayed.

### Step 5 - Basic content

To start making this look like a website lets add some example content.

Open `index.markdown` and add some content below the header.

Open `about.markdown` and replace the default content below the header.

Create new markdown file called `cv.md` and add the following header.

```html
---
layout: page
title: CV
permalink: /cv/
---
```

Add any content you like below the header.

Finally, in the directory `_posts` create a new post with the following file name format: `year-month-day-post-title.md`.

Add the following header to the post.

```html
---
layout: post
title:  <Post Title>
date:   <year-month-day>
categories: news
---
```

Add any content you like below the header.

Play around a bit then close the server by typing `ctrl+c`.

### Step 6 - Deploy the example site

Now that we have something that looks like a website we can deploy it on GitHub.
