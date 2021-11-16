---
title: Set up a simple GitHub Page
layout: post
tag: GitHub page
---



Recently I am trying to find somewhere to put my online CV. Ten years ago, I used Blogger and it got the job done well, although I did spend much time with the layout. When I checked on the pages recently, everything was perfectly preserved, including all the uploaded images. But Blogger does not adapt well in mobile devices, and as with all other Google products, you can't access it in China. But still, one thing I like very much about Blogger is the powerful search function that allows you to quickly locate a post, and that you can post blogs by sending emails...

I also tried [Google sites](https://sites.google.com/view/tosingfung). It was very easy to use and required almost no knowledge of HTML. Compared with the Dreamweaver that I used to mess around over ten years ago, this is really a bless. The preset templates also come in handy. If a small business needs to set up a info site, it could be easily done within hours. However, I feel like that when there are more than 20 pages, it may be quite difficult to maintain. Also, I would prefer a more streamline approach to add new pages.

I also look at several Chinese sites powered by Markdown. [CSDN](https://www.csdn.net/) has tons of Ad. [简书](https://www.jianshu.com/) has fewer Ad, but you need to tie up your cell phone AND WeChat account before your blog can be published. I also checked on Wordpress, which adopted a new 'Block' editor that feels a bit like Google sites, although even more complicated. It has a lot of 'Block' templates for sharing images and videos, but all I need is a place to put some text, maybe sometimes with one or a few images. Plus, its editor starts slow as hell.

## Why GitHub?

As a layman of the coding world, I come across GitHub from time to time when searching for softwares or plug-ins that fulfill a specific task. I understand that it can help to track code modifications between different versions for software developers, which sounds very powerful to me. But I never quite grasped how the site is organized and where they put what. That doesn't really bother me until I realized GitHub can be used to host personal pages. So I gave it a try.

## Set up a single page

1. Register a GitHub account.
   <br>I am using `tosingfung` as my username

2. Create a **public** repository named: `tosingfung.github.io`  

   > You must use this format, ie. `{username}.github.io`

3. In the **Setting** tab of that repository, go to **Page**, and click **Change theme**. Choose any one theme. Two files will be automatically generated:

   > _config.yml<br>index.md
   >
   
4. Open `index.md` by clicking **Edit this file**. 

5. Now you can write the page in markdown format. But it will be much easier to first write in any markdown editor (such as Typora), then paste the content here. Remember to click **commit changes** when you're done.

6. This page can now be accessed by visiting https://tosingfung.github.io

## What's next?

Of course this will only generate a single page, which suffices when you only need to showcase your product or cv. More complicated personal or business websites can be generated with Jekyll and hosted on GitHub.
