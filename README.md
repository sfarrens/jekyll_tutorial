# Jekyll Tutorial

> Author: <font color='#f78c40'>[Samuel Farrens](http://www.cosmostat.org/people/sfarrens)</font>    
> Year: 2020  
> Email: [samuel.farrens@cea.fr](mailto:samuel.farrens@cea.fr)  

The objective of this tutorial is to introduce [Jekyll](https://jekyllrb.com/) and show you how to build a website that you can host on GitHub for free.

[<img src="https://jekyllrb.com/img/logo-2x.png" width="200">](https://jekyllrb.com/)

## Contents

1. [Requirements](#Requirements)
1. [Installation](#Installation)
1. [An example website in under 10 min](#An-example-website-in-under-10-min)
1. [Deployment](#Deployment)
1. [Customising your website](#Customising-your-website)
1. [How Jekyll works](#How-Jekyll-works)
1. [Tips and tricks](#Tips-and-tricks)

## Requirements

To follow all of the steps in this tutorial you will need a [GitHub](https://github.com/) account. It is possible to run everything locally and deploy your website on a different server, but everything will presented under the assumption that you already have a GitHub account.

You will also need to install Jekyll (see the [next section](#installation)) for local development and testing. It is also possible to build your website entirely on GitHub, but you will save yourself a lot of time if you are able to test things locally before deployment.

## Installation

Before starting you will have to install Jekyll. Jekyll is written in [Ruby](https://www.ruby-lang.org/en/downloads/) and therefore your system must have Ruby installed in order to build Jekyll. With Ruby installed the installation of Jekyll should simply be:

```bash
gem install jekyll bundler
```

Please see the [installation instructions](https://jekyllrb.com/docs/installation/) on the Jekyll website for more details.

## An example website in under 10 min

Now that you have Jekyll installed let's make a quick website to see how easy it is. We we will go through everything in more detail afterwards.

### Step 1 - Create a new repository

On your GitHub account either [fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) this repository or create a new one.

> If you choose to create a new repository be sure to click the `Add .gitignore` button at the bottom and scroll down to `Jekyll`.

Now clone your repository. *e.g.*

```bash
git clone https://github.com/<USERNAME>/jekyll_tutorial.git
```

and `cd` to the repository name. *e.g.*

```bash
cd jekyll_tutorial
```

### Step 2 - Create a gh-pages branch

If you forked this repository then you can simply checkout the `gh-pages` branch.

```bash
git checkout gh-pages
```

Otherwise, create and checkout a new branch called `gh-pages`.

```bash
git checkout -b gh-pages
```

> `gh-pages` is a special branch name used to idetify [GitHub Pages](https://pages.github.com/) content. It is also possible to host GitHub pages on the `master` branch.

### Step 3 - Jekyll quickstart

Next we will run through the [Jekyll quickstart](https://jekyllrb.com/docs/) instructions with some minor changes.

You will need run these commands in your local repository directory.

> Otherwise, you can run the standard quickstart commands and copy the outputs to this directory. Be careful to copy all the hidden files!

First, we will create a new Jekyll site in the current directory.

```bash
jekyll new . --force
```

Then, we will launch the Jekyll local server.

```bash
bundle exec jekyll serve
```

You can view the website at the address specified by `Server address`.

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

Let's add some example content to start making this look like a website .

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

Stage the files generated by Jekyll.

```bash
git add .
```

> Note that the contents of `_site` and `.jekyll-cache` should be ignored by git.

Commit the changes.

```bash
git commit -m "upload jekyll content"
```

Finally, push the commits to your remote GitHub repository.

```bash
git push origin gh-pages
```

If you forked this repository, otherwise:

```bash
git push --set-upstream origin gh-pages
```

Now you should be able to view your example site at `https://<USERNAME>.github.io/<REPOSITORY>/`.

> If you forked this repository it will be `https://<USERNAME>.github.io/jekyll_tutorial/`. Note it may take a few minutes before the website is available.

## Deployment

In the first example we looked at how to deploy a basic Jekyll site on the `gh-pages` branch of any given repository. There is, however, another way in which you can create your own personal website or one for a GitHub organisation.

### Personal website

To create your own personal website (*i.e.* one linked to your GitHub username) you need to create a new repository on your GitHub account called `<USERNAME>.github.io`.

The master branch of this repository will behave in the same way as the `gh-pages` branch in the example. So you can prepare your Jekyll site in pretty much the same way. Since the site is not linked to a normal repository, you won't have to specify the `baseurl` in `_config.yml`.

Once your site is deployed it will be visible at `https://<USERNAME>.github.io/`.

*e.g.* You can find my website here: [https://sfarrens.github.io/](https://sfarrens.github.io/)

### Organisation website

You can create a website for your GitHub organisation in exactly the same way. Simply create a repository called `<ORGANISATION_NAME>.github.io` and follow the same steps.

Once your site is deployed it will be visible at `https://<ORGANISATION_NAME>.github.io/`.


## Customising your website

Now that you know how to make and deploy a basic website you will probably want to personalise it to fit your needs and taste.

The easiest way to get started is by using a theme.

### Jekyll themes

The default theme in Jekyll is [Minima](https://github.com/jekyll/minima) (which was used for the first example), but there are huge number of [Jekyll themes](http://jekyllthemes.org/) available online.

#### Changing theme locally

If you want to try out a different theme locally you need to update the value of `theme` in `_config.yml`. You also need to update your `Gemfile` to download the theme by adding `gem <THEME_NAME>`.

*e.g.* To use the [Cayman theme](https://pages-themes.github.io/cayman/) you would add `theme: jekyll-theme-cayman` to `_config.yml` and `gem "jekyll-theme-cayman"` to `Gemfile`.

Then update your *bundle* before launching the Jekyll server.

```bash
bundle update
bundle exec jekyll serve
```

> Be sure to read the warnings and errors as not all themes use the same *layouts*. So pages will need to updated to fit the theme requirements.

#### Changing theme on GitHub

Changing a theme on GitHub is even simpler. In your repository, click on "Settings" and scroll down to "GitHub Pages". There is a button labelled "Change Theme" that will take you to a selection of themes you can use.

This will simply update the value of `theme` in `_config.yml`.

#### Making your own theme

If you have decided that none of the Jekyll themes really offer what you are looking for you, you can make your own or simply modify an existing theme.

It is possible to create your own Jekyll theme that you can share as a template for others to use.

There plenty of [blog posts](https://www.siteleaf.com/blog/making-your-first-jekyll-theme-part-1/) that explain how to do this in more detail.

### Plugins

There is also an extensive library of [Jekyll plugins](https://jekyllrb.com/docs/plugins/) you can install to add extra functionality to your website.

You can specify the plugins you want to use in your `_config.yml` under the attribute `plugins`. *e.g.*

```yaml
plugins:
  - jekyll-latex
```

Then, you add them to your `Gemfile` so that they are downloaded and installed.

```ruby
gem 'jekyll-latex'
```


## How Jekyll works

If you made it through the first parts of this tutorial you should be able to make a very basic website with some personal touches, but you probably don't know how everything works.

In this section we will go through everything in a bit more detail.

### What does Jekyll do?

Jekyll is a static site generator, which means it does not use a database (like *e.g.* WordPress).

>"Instead of using databases, Jekyll takes the content, renders Markdown or Textile and Liquid templates, and produces a complete, static website ready to be served by Apache HTTP Server, Nginx or another web server. Jekyll is the engine behind GitHub Pages, a GitHub feature that allows users to host websites based on their GitHub repositories for no additional cost."
>
> Taken from https://en.wikipedia.org/wiki/Jekyll_(software)

In simple terms, Jekyll automatically converts [Markdown](https://daringfireball.net/projects/markdown/) files to HTML. This allows you to more easily write content for your website.

### Jekyll structure

Jekyll sites generally have the following structure:

```bash
├── _config.yml
├── _data
│   └── navigation.yml
├── _includes
│   ├── footer.html
│   └── header.html
├── _layouts
│   ├── default.html
│   └── post.html
├── _posts
│   └── 2020-03-07-my-first-post.md
├── _sass
│   ├── _base.scss
│   └── _layout.scss
├── _site
├── assets
│   ├── css
│   └── images
├── Gemfile
└── index.html
```

Here is a very brief rundown of what each of these components do.

- `_config.yml:` The configuration file for your site. Here you define some variables, list plugins and set the corresponding parameter values.
- `_data:` In this directory you can create YAML files to define additional variables.
- `_includes:` This is simply a place for defining HTML snippets that can be used in your layouts. *e.g.* Define behaviour for the header/footer of your site.
- `_layouts:` This is where you define *layouts* for your site pages. In other words, these are HTML files that define how a given page is laid out.
- `_posts:` This one is pretty clear, it's a directory where you store your *posts*. The best part being that they can be markdown files!
- `_sass:` This is the most important section if you want to customise the look of your website. In this directory you define all your style sheets using Sass.
- `_site:` This is where the final static HTML files generated by Jekyll are stored. In general you won't need to touch anything here, but it can be useful to see what's going on as you are building your website.
- `assets:` In this directory you can store *e.g.* images, CSS files and JavaScript.
- `Gemfile:` The [Gemfile](https://jekyllrb.com/docs/step-by-step/10-deployment/#gemfile) is used to fix package versions and dependencies for your website.
- `index.html:` This is where you set the content for your home page. It can be defined in either HTML or markdown. Other static pages are similarly defined in the root directory.

> To get a more in depth understanding of each of these components I recommend following the Jekyll [Step by Step tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/).

You will probably notice that in the earlier example site many of these files and directories were missing. This is because much of this content is often hidden in the Jekyll theme you are using.

### Liquid templating

Jekyll uses the [Liquid template language](https://shopify.github.io/liquid/), which allows you to include some dynamic content in your markdown/HTML files.

For example, rather than manually typing the page title inside every file, you could instead create a layout that includes the following liquid object.

```html
{{ page.title }}
```

This will automatically generate the page name from the [front matter](#Front-matter-and-data). Liquid also includes operators that allow more complex behaviour. For example, you can loop through all of the posts on your site and create a list.

```html
<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ site.baseurl }}/{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
```  

> [More on this topic](https://jekyllrb.com/docs/step-by-step/02-liquid/)

### Front matter and data

So, where does Liquid get the variables from? Well, some of them are [predefined by Jekyll](https://jekyllrb.com/docs/front-matter/), the rest are defined by you.

- `site` variables (*e.g.* `site.baseurl`) are defined in your `_config.yml`.
- `site.data` variables are defined in additional YAML files you place in the `_data` directory.
- `page` variables are taken from the front matter of pages.
- `post` variables are taken from the front matter of posts.

So what is "Front Matter"? This is what we referred to as a header in the first example. It includes everything enclosed within the `---` at the top of the file. You may notice that the content is also in YAML format. While `_config.yml` and `_data` are global YAML content for your site, the front matter can be thought of as local YAML content for a given page or post.

> Note Jekyll will not convert markdown files without front matter. Even empty front matter will suffice.

> [More on this topic](https://jekyllrb.com/docs/step-by-step/03-front-matter/)

### Layouts

The most important attribute in the front matter of any page or post is the `layout`. Layouts are HTML files placed in `_layouts` that specify how a given page or post should look.

Most themes will include a `default.html` file that specifies the default layout for a given page. Other layouts can inherit this layout as a base to build upon. This is done via front matter. Imagine, for example, that you want to create a layout for posts. You could create a file called `posts.html` stored in `_layouts` with the following front matter:

```html
---
layout: default
---
```

Below the front matter you would specify the HTML specific to the layout of your posts.

Here is an example from my personal website:

```html
---
layout: default
---

<br>
<div class="in-post-image-container">
  <img src="{{ site.image_path }}/{{ page.image }}" class="in-post-image">
</div>
<br>
<br>

{{ content }}
```

Then, in the front matter of your posts, you would put:

```html
---
layout: post
---
```

While writing your layouts you may find that there are many pieces of reusable HTML, or that it may be easier to manage smaller files. You can break apart your HTML and store the files in `_includes`.

For example, if your site has a header, you could create a file called `header.html` stored in `_includes`. Then, in your `default.html` you can simply include this fragment with Liquid.

```html
{%- include header.html -%}
```

> [More on this topic](https://jekyllrb.com/docs/step-by-step/04-layouts/)

### Assets

You will need a place to store your site's images, scripts and style sheets. This is what the `assets` directory is for. The directory contents are copied to the Jekyll build (*i.e.* the `_site` directory).

> [More on this topic](https://jekyllrb.com/docs/step-by-step/07-assets/)

### Sass

Most of the work of getting your site to look the way you want it to is in defining the style sheets. This means learning how to write Cascading Style Sheets (CSS). Jekyll uses [Syntactically Awesome Style Sheets (Sass)](https://sass-lang.com/).

[<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/1920px-Sass_Logo_Color.svg.png" width="200">](https://sass-lang.com/)

> To get started with SASS check out their [guide](https://sass-lang.com/guide).

Your Sass files can be stored in the `_sass` directory. Similarly to the layouts, your style sheets can also be broken apart into fragments and imported. For example, if you created a style sheet just for your navigation menu called `navigation.scss`, you could import this into a general style sheet as follows.

```sass
@import "navigation";
```

Sass has several very cool features including nesting and *mixins*. Mixins allow you to define reusable pieces of CSS that you can include in your Sass files (`.scss`).

Here is a quick example of how to add a shadow to a container (something I used extensively on my own site).

```sass
@mixin shadow {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.post-container {
  @include shadow;
}
```

Once you get comfortable with Sass, the rest is just patience.

## Tips and tricks

Once you have understood how all of the pieces of Jekyll work, you are pretty much good to go. Before finishing this tutorial, however, I will leave you with a few tips and tricks that you may find helpful when working on your website.

### Use containers

If you are new to HTML or like me never really learned to do things the right way, the best piece of advice I can offer is to use [spans](https://www.w3schools.com/tags/tag_span.asp) and [containers](https://www.w3schools.com/w3css/w3css_containers.asp).

You can dramatically simplify the HTML files in your site by using containers like `<header>`, `<footer>` and `<div>`. Then use Sass to do the rest.

Take, for example, the `default.html` layout for my personal website.

```html
<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">

  {%- include head.html -%}

  <body>

    {%- include header.html -%}
    {%- include navigation.html -%}

    <main id="content" class="main-content" role="main">

      {% if page.title %}
      <h1>{{ page.title }}</h1>
      {% endif %}

      {%- include anchor_headings.html html=content -%}

    </main>

    {%- include footer.html -%}
    {%- include scripts.html -%}

  </body>

</html>
```

As you can see, it is very short and simple. All of the properties that make the website look the way it does are included in the Sass class `main-content`.

### Use Jekyll plugins

Don't waste your time reinventing the wheel. Before spending a lot of time writing something, look to see if there is a Jekyll plugin already available that will provide the functionality you need.

For example, I really hate when external links open in the same tab. I could have wasted a lot of time specifying `target="_blank"` for every external link, or writing some fancy script to do it automatically. It turns out there was already a nice plugin (`jekyll-target-blank`) that did just what I wanted.

### Treat your website like code

There is no reason to treat your website any differently than any other code base hosted on GitHub. Keeping things clean and organised will make it a lot easier to maintain and improve. Like any code language, principles like encapsulation and abstraction are really helpful. Don't copy and paste HTML or Sass all over the place. Instead, find fragments you can reuse, define them once and import them where needed.

You can also run [CI tests on your website](https://jekyllrb.com/docs/continuous-integration/travis-ci/)! Services like [Travis-CI](https://travis-ci.org/) can be used to make sure you don't break your own website every time you change something.

> Note: If you have any trouble getting `htmlproofer` to work with arguments try the following.

```yaml
install:
  - bundle install

script:
  - bundle exec jekyll build
  - bundle exec htmlproofer --disable-external --empty_alt_ignore ./_site
```
