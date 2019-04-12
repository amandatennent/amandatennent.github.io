---
layout: post
title: 'Who am I?'
date: 2019-04-12 12:48:55 +1000
categories: learning introduction
---

I have decided to keep this blog as a means to keep track of what I'm learning. The past 6 or so months I've been working a lot harder to learn more, after having completed my degree 3 years ago. I allowed myself to get lazy, and my programming skills suffered because of it.

A few months ago I went for a job interview where I was told that I should

> Try to come to a deeper understanding of the performance characteristics of the systems that you are already familiar with

I'd already been working through online tutorials and the like, but I hadn't really been learning about what goes on 'under the hood', so I set to work finding some books on JavaScript - my language of choice. I decided on ['You Don't Know JS' series of books by Kyle Simpson][ydkjs] after reading some posts & comments on Reddit, and so far they've been great.

Another thing I've wanted to do is document my learning as I find that it uses a different part of your brain and helps you remember it. What better way than a blog? I wanted something quick and easy, so I went with Github pages - it's already tied to my code so it's perfect. But in typical me fashion, even though I wanted something quick and easy, I made it complicated and had to make it mine. It took a few goes to get it working locally on my own computer, but I got it working the way I like (for the most part - I have the source code so I can always tweak it as I need to), it took me a few goes before I got my head around it though, so I thought I'd document what I did.

The problem that I had was because it's written in ruby and I really don't have a lot of experience with it. Also, I didn't read the documentation very well and just tinkered.

1. First, set up your repo following [these][github-pages] instructions
2. Then follow [these][github-jekyll-local] instructions to install Jekyll, generate the Jekyll files and build the site
3. I decided to use the 'Slate' theme from Github pages, and to get that to work locally I needed to uncomment `gem "github-pages", group: :jekyll_plugins` from the `Gemfile` and then run `bundle update`. Depending on the theme you choose, you might need to create a `_layouts` folder and add some files to that. The original installation only includes a `default.html` file but some of the markdown files in different themes include a different layout file. You can also just change each of the markdown files to use the default layout.
4. I had issues getting the index.html page to render when visting the base url on github pages (it worked locally), until I removed the `baseurl` and `url` fields from the `_config.yml` file

More information on setting up and customising Jekyll can be found [here][github-pages-jekyll]

[ydkjs]: https://github.com/getify/You-Dont-Know-JS
[github-pages]: https://pages.github.com/
[github-pages-jekyll]: https://help.github.com/en/articles/using-jekyll-as-a-static-site-generator-with-github-pages
[github-jekyll-local]: https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll#step-2-install-jekyll-using-bundler
