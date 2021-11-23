---
title: Build RSS feeds with Feed43
layout: post
tag: RSS
---

- Built RSS feeds with Feed43 for:
- Nature News and Nature Book Review

<!--more-->

## Step 1

![image-20211123112523537](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123112523537.png)

#### Paste the url and type the encoding.

## Step 2

![image-20211123114911850](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123114911850.png)

#### In the Page Source, identify the repeating pattern and copy one to the search pattern. Here we are only interested in getting the feed title and link.

![image-20211123114936755](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123114936755.png)

#### Replace the feed title and link that blanketed `%`.

![image-20211123115015774](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123115015774.png)

#### Replace the other content with `{*}`. Even for line change (carriage return), you need to add `{*}`, otherwise the pattern will not be recognized.

## Step 3

![image-20211123113719548](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123113719548.png)

#### The feed titles and links have been extracted.

![image-20211123113912504](https://raw.githubusercontent.com/tosingfung/images/master/image-20211123113912504.png)

#### Simply enter the extracted parameters to the corresponding fields.

## Step 4

Finally, simply copy the `xml` link generated and paste it to Feedly or Innoreader. In innoreader the default refresh time is about 1h.