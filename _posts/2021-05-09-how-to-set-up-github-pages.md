---
title: "Set up a GitHub page"
layout: post
tag: jekyll
---

- Try out some blog platforms
- Set up a Gibhub page repo
- Put up a single page (.md)

<!--more-->

I need somewhere to put my CV. Ten years ago, I used Blogger and it got the job done well, although I did spend much time with the layout. When I checked on the pages recently, everything was perfectly preserved, including all the uploaded images. But Blogger does not adapt well in mobile devices, and as with all other Google products, you can't access it in China. But still, one thing I like very much about Blogger is the powerful search function that allows you to quickly locate a post, and that you can post blogs by sending emails...

I also tried [Google sites](https://sites.google.com/view/tosingfung). It was very easy to use and required almost no knowledge of HTML. Compared with the Dreamweaver that I used to mess around over ten years ago, this is really a bless. The preset templates also come in handy. If a small business needs to set up a info site, it could be easily done within hours. However, I feel like that when there are more than 20 pages, it may be quite difficult to maintain. Also, I would prefer a more streamline approach to add new pages.

I also look at several Chinese sites powered by Markdown. [CSDN](https://www.csdn.net/) has tons of Ad. [简书](https://www.jianshu.com/) has fewer Ad, but you need to tie up your cell phone AND WeChat account before your blog can be published. I also checked on Wordpress, which adopted a new 'Block' editor that feels a bit like Google sites, although even more complicated. It has a lot of 'Block' templates for sharing images and videos, but all I need is a place to put some text, maybe sometimes with one or a few images. Plus, its editor starts slow as hell.

## Why GitHub?

As a layman of the coding world, I come across GitHub from time to time when searching for softwares or plug-ins that fulfill a specific task. I understand that it can help to track code modifications between different versions for software developers, which sounds very powerful to me. But I never quite grasped how the site is organized and where they put what. That doesn't really bother me until I realized GitHub can be used to host personal pages. So I gave it a try.

## Set up a single page

First, register a GitHub account with the user name: **tosingfung**. Create a **public** repository named: **tosingfung.github.io**  It seems you can only use this name for the repository, anything else (I tried tosingfung) would result in your page URL being tosingfung.tosingfung.github.info, which feels like a page for that that specific repository instead of a page for the account (the user). The repository is now. Next, in the **Setting** tab of that repository, go to **Page**, and click **Change theme**. Now choose any theme you like and click **Change theme**. Two files will be automatically generated:

- `_config.yml`
- `index.md`

Open `index.md` by clicking **Edit this file**. Do not modify the YAML front matter! Now you simply need to write in markdown, for example a CV. Remember to click **Commit change**. Now people can read this single page by going to the URL **tosingfung.github.io**
