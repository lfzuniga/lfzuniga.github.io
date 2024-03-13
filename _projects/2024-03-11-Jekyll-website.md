---
layout: project
title: Jekyll Website Built v1
description: Coding of Jekyll Website.
date: 2024-03-11
status: Completed
---

#### Goal
- Build a personal website to share writings and projects.
- Learn how to work with Github repositories and use the pages feature to host a static website
#### Process
The first thing to know about websites is that there are a lot of different ways of building and hosting them. There are also different "types" of websites generally based on how the website is generated and presented to the user. This website is a **static website**, which means each visitor will see the same and the content of the website will change only if I change the source code. **Dynamic websites** on the other hand, change their content in real-time based on user interaction or other factors [^1].

Since static websites use less resources to run compared to dynamic ones, they are great for making a personal website. You can create and host one for free with [Github pages](https://pages.github.com). And you can use either of these three frameworks to make a static website:
- [Jekyll](https://jekyllrb.com)
- [Hugo](https://gohugo.io)
- [Gatsby](https://www.gatsbyjs.com)

I decided to use Jekyll because it is natively supported by Github pages and pretty straightforward to maintain. For instance, if I want to publish a new post or project writeup, I just have to make a markdown file and then put it in the respective folder of the repository. 

I used ChatGPT to guide me through the initial process of setting up the website. This consisted of installing `ruby` (programming language), `jekyll` (the actual tool to turn markdown and other files into a static website), and `bundler` (command line tool to manage ruby gems), and creating the Github repository. I had to do some troubleshooting since MacOS already comes with its own (somewhat old) version of `ruby` installed but at the core it's just two simple commands to get started.

command to install `ruby` via `homebrew`:
```
brew install ruby
```

command to install `jekyll` and `bundler`
```
gem install jekyll bundler
```

After that I created the infrastructure for the website with 
```
jekyll new <name-of-new-site>
```

Lastly, in terms of important commands, I used the following to actually build and iterate different versions of the website as I made changes to the initial layout:

command to install gems. Only needed when you mess around with `gem` files.
```
bundle install 
```

command to build website. Needed every time you mess up with `config` file
```
bundle exec jekyll build 
```

command to serve and see your website locally
```
bundle exec jekyll serve
```

The default website built with the `jekyll new <name-of-new-site>` command comes with the minima theme. I wanted to do some tweaks to it so I removed all connections with the theme in `_config.yml` and `Gemfile` and manually copied all the files from the [minima theme Github repository](https://github.com/jekyll/minima). The `README.md` file is very well written and explains in detail how all the different files that make minima work. I made significant changes to the minima theme specific files (in addition to changes to `_config.yml`)
- `home.html`
- `footer.html` 
- `_layout.scss`
The important thing to note about the theme is that if you want to edit how something *looks* in the website, you have to make changes to **both** the `.html` files and the `_layout.scss` file [^2]. The `_layout.scss` file contains the "functions" and the `.html` the actual "implementation" in the website. In summary, the main changes I made consisted on simplifying and improving the layout of the footer and simplifying the home page to have writings and projects. Because I wanted projects to be a "separate entity" from writings (or `posts`, and jekyll formally calls them), I created a new [collection](https://jekyllrb.com/docs/collections/) in `_config.yml` with the following specifications:
```ruby
collections:
	projects:
		output: true
		permalink: /:collection/:path/
```

I of course made more small changes, all of which are in the [Github repository](https://github.com/lfzuniga/lfzuniga.github.io) (specifically in the `theme-redesign-zero`), but I thought these changes were the ones worth highlighting as I didn't find any in depth resource that really goes over how to edit a jekyll theme. I believe this is because every jekyll theme is significantly different so the steps on how to customize it will vary significantly from theme to theme.

[^1]: Twitter and pretty much any other social media website is a good example of a dynamic website.
[^2]: You can also modify the `_base.scss` but I would only advise changing this file if you are changing something very basic about the website, such as how the images or code blocks are presented in the website.