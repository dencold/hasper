# hasper

Hasper is a port of [Ghost's](https://ghost.org/) casper theme for the [Hugo](https://gohugo.io) static-site generator. It hopes to get you from zero to beautiful with minimal effort.

## Installing Hugo

If you haven't yet installed Hugo, I recommend reading [these instructions](https://gohugo.io/overview/quickstart/) first to get yourself acquainted with the process. Here's a quick summary to get Hugo working on your system:

0. Go to Hugo's [release page](https://github.com/spf13/hugo/releases) and grab the tar file that matches your OS and architecture (for example if you are on a Mac, you'd want `hugo_0.16_osx-64bit.tgz`).
0. Unzip the tar file and copy the hugo binary into your path:

```bash
$ mkdir hugo_0.16; tar xzvf hugo_0.16_osx-64bit.tgz -C hugo_0.16
$ cp hugo_0.16/hugo ~/bin
```

Now you should have Hugo installed and see its version:

```bash
$ hugo version
Hugo Static Site Generator v0.16 BuildDate: 2016-06-06T05:37:59-07:00
```

## Creating a new site

Hugo has a helper command to scaffold a new site together. It creates all of the files and initial directory structure you need to start writing content and getting things posted. Let's do this for the example site I am working on, bayactive.org:

```bash
$ hugo new site bayactive -f yaml
$ cd bayactive
```

When you run `ls` within the site's directory you should see output like the following:

```bash
$ ls -1
 archetypes
 config.yaml
 content
 data
 layouts
 static
 themes
```

That's all the organization you'll need to get your site going.

## Installing the theme

You've got Hugo installed and have the scaffolding for your site, it's finally time to install the hasper theme! All you'll need to do is clone the hasper repository into your theme directory for your site and you're done! We'll assume our sample site of `bayactive` here, but subsitute your site's name in the command below.

```bash
$ cd bayactive
$ git clone git@github.com:dencold/hasper.git themes/hasper
```

At this point, you can start using the theme immediately by issuing the following command at the root directory of your site:

`$ hugo server -t hasper`

But, you don't have any content currently, let's fix that.

## Creating your first post

We'll use another Hugo helper command to create a file that represents a new post on your site:

```bash
$ hugo new post/welcome.md -f yaml
```

That command creates a new file located at `content/post/welcome.md`. Also, a quick note on the `-f yaml` option I have been using. Hugo defaults to [toml]() for metadata, which I'm not a fan of. I prefer to use [yaml]() as my format for these settings. 

You can open up the `welcome.md` file in your favorite editor and you should see something resembling the following:

```yaml
---
date: 2016-06-27T17:09:17-07:00
draft: true
title: welcome
---

```

Let's add an actual welcome message here & make sure people know what the site is all about:

```yaml
---
date: 2016-06-27T17:09:17-07:00
draft: true
title: welcome
---

Thanks for visiting BayActive! We hope to be a helpful resource for finding hiking/biking/running routes in the bay area.
```

Save that file, and spin up hugo's internal webserver, using the hasper theme:

```bash
$ hugo serve -D --theme hasper
```

You should see Hugo spit out the following logs:

```
Started building site
1 of 1 draft rendered
0 future content
0 expired content
1 pages created
0 non-page files copied
2 paginator pages created
0 tags created
0 categories created
in 28 ms
Watching for changes in /home/coldwd/src/github.com/dencold/bayactive/{data,content,layouts,static,themes}
Serving pages from memory
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

## Sample configuration

Here is a sample configuration for a fictional Baywatch enthusiast site:

```yaml
---
baseurl: "http://baywatch.com/"
languageCode: "en-us"
title: "Memories of Baywatch"
paginate: 5
Copyright: "All rights reserved - 2016"
canonifyurls: true

params:
  description: "David Hasselhoff loves telling you about Baywatch."
  cover: "images/cover.jpg"
  author: "david"
  logo: "images/logo.png"
  googleAnalyticsUserID: ""
  RSSLink: "http://feeds.feedburner.com/..."
  githubName: "thehoff"
  twitterName: "thehoff"
  hideHUGOSupport: false
  highlightjsTheme: "tomorrow-night-eighties"
  sharing:
    twitter: false
    facebook: true
    google-plus: true

author:
  david:
    name: "David Hasselhoff"
    bio: "Don't Hassle the Hoff"
    location: "Baltimore, MD"
    thumbnail: "images/avatar.jpg"

menu:
  main:
    - name: "Blog"
      weight: -120
      identifier: "blog"
      url: "/"
    - name: "About"
      weight: -110
      identifier: "about"
      url: "/about"
```

## Configuring Multiple Authors

You can add as many authors as you like under the `author` section of the `config.yaml`. In the example above, we just had one author, David Hasselhoff, here's how we could add Pamela to the blog roll:

```yaml
author:
  david:
    name: "David Hasselhoff"
    bio: "Don't Hassle the Hoff"
    location: "Baltimore, MD"
    thumbnail: "images/avatar.jpg"
  pamela:
    name: "Pamela Anderson"
    bio: "Little known fact, I am vegan"
    location: "Canada"
    thumbnail: "images/pamela.jpg"
```

You can now reference either "david" or "pamela" on the author attribute of a post's [front-matter](https://gohugo.io/content/front-matter/) and their information will automatically get pulled in by hugo.

## Attribution

Hasper was originally [a fork](https://github.com/dencold/hugo-theme-casper) of the [hugo-theme-casper](https://github.com/vjeantet/hugo-theme-casper). However, the original author has not been responding to [pull requests](https://github.com/vjeantet/hugo-theme-casper/pull/41). Hasper now lives as its own separate repository and has been updated with the following improvements: 

* author thumbnail fixes across the site (original version only worked on list template): [25467fc](https://github.com/dencold/hasper/commit/25467fc92ca611ae7a6d517c16b47cdac0ae9dcb)
* switching from bespoke `.Site.Data.Author` in favor of Hugo's canonical `.Site.Author`: [25467fc](https://github.com/dencold/hasper/commit/25467fc92ca611ae7a6d517c16b47cdac0ae9dcb)
* icon aesthetic improvements, previous styles had ugly underlines: [2238091](https://github.com/dencold/hasper/commit/22380914098cbf0dad119be18d7727521f097a29)
* removing unused `page` directory which contained duplicate code: [8c2f9e8](https://github.com/dencold/hasper/commit/8c2f9e8c5b138d89e1b5e2c39d2d6210c928ad9f)
* allowing for external image linking (gravatar, twitter, etc), original theme hardcoded site's base url: [06afad2](https://github.com/dencold/hasper/commit/06afad23845e6e51c0ac55cef29c2e7caf7878d5)
* share icons are now user-configurable: [b334fed](https://github.com/dencold/hasper/commit/b334fed9c5e88447b98e5908c362f3d165e1ee02)
* full theme support for [highlightjs](https://highlightjs.org/) code blocks: [a8f2870](https://github.com/dencold/hasper/commit/a8f2870b03a5d48075129372ad7f499f0ac4c2d4)

