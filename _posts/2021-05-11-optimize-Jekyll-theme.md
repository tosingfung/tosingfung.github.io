---
title: "Optimize Jekyll theme"
layout: post
tag: jekyll
---

- Choosing a Jekyll theme
- Customization with HTML/CSS

<!--more-->

The default layout of Jekyll is a bit too minimalistic. One important functionality it lacks is the tagging of a new blog, which becomes very important when there are more and more posts, each focusing on one or another unrelated topics. Ideally an internal blog search would be great, but it seems many of the available themes still link out to Google. I have several criteria when looking for a suitable theme:

- Free
- Tagging blog posts
- Good mobile site layouts
- Single column layout (no sidebar)
- Simple design and no fancy animation
- Simple CSS so I can personalize

After trying out a few themes, I settled on the current one call Scriptor made by a guy from Lithuania. The original theme looks quite nice already but I did made several adjustments. Luckily I have learned some basic HTML and CSS to understand what's going on. I removed things that I don't need, like the comment sessions under each post, the social media links at the footer, the thick border surrounding the whole body. I also adjusted the margins between posts and reduced the font size of both the post titles and the headings. I also set the timing of the fade-in effect to 0.1 second. These were all done by modifying the CSS and the SCSS files.

Basically, after everything is optimized, you don't really need Ruby and Jekyll anymore. Unless you need to preview the page using `bundle exec jekyll serve`, all new pages and posts (in md format) can simply be added to the root and `_post` folder respectively. In fact, you don't even need GitHub desktop, because you can simply bookmark the URL and upload the files when opening the GitHub folder in the web browser. (But do remember to click **Commit changes**). In other words, all the hustle beforehand is simply for the sake of deployment. Content management in the future becomes streamlined.
