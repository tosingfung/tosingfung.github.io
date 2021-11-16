---
title: Install Ruby and Jekyll
layout: post
tag: GitHub page
---



## Install GitHub Desktop

This part was quite easy. Basically you just need to download and install [GitHub desktop](https://desktop.github.com/). It serves as a sync software like dropbox or nutstore, so that any change you modified on your local files can be sync to the repository online. Simply run GitHub desktop and click "**Clone a repository from the Internet**". Choose the repository and select a disk path for the local copy. Press **Clone** and close GitHub Desktop.

## Install Ruby and Jekyll

Download and install [Ruby](https://rubyinstaller.org/downloads/). Choose the (x64) one with Devkit. At the time or writing, it is version 3.0.2-1. After installation, there will be three new icons in the Ruby folder in the start menu. Click on the **Start Command Prompt with Ruby**. Type `gem install jekyll bundler` to install Jekyll. Next go to the local folder containing the above repository. Type `jekyll new . --force`. This will install the plain minima theme.

Type `bundle exec jekyll serve` to start a local server. This allows you to preview the changes in realtime. Simply open the web browser and go to `127.0.0.1:4000`. Changes to the site name and other core settings (site description ect) need to be done in the `_config.yml` file. **And you need to restart Jekyll serve to see the changes**. To restart, press `Ctrl-C` and type Y twice. Then retype `bundle exec jekyll serve`.

## Jekyll themes

There are many good (and free) Jekyll themes online. Simply download them and make necessary style changes, and you're ready to go. Sometimes you need to do `bundle install`. For new versions of Ruby 3.0+, you may also need to `bundle add webrick` before deploying the local server with `bundle exec jekyll serve`.

## Upload to GitHub

Finally, open GitHub Desktop and press **commit to main**, then **Push Origin**. It will tak 3-5 minutes before GitHub Pages finishes building your site. Also, if you have visited your site in the browser before, you may need to refresh several times (or clean up browser history) to see the modifications. In the future, if you just need to add a post or update a page, you can do so by uploading or editing files on GitHub in the web browser.
