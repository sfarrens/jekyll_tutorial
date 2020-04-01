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

## A website in 5 min

Now that you have Jekyll installed let's make a quick website to see how easy it is.

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

Next we will run throught the [Jekyll quickstart](https://jekyllrb.com/docs/) instructions. You can run these commands locally in any directory you like.

First, we create a new Jekyll site called `mysite` (or whatever you like).

```bash
jekyll new mysite
cd mysite
```

Then, we will run the Jekyll local server to see what the website looks like before uploading it.

```bash
bundle exec jekyll serve
```
