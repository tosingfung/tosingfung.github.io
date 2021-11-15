---
layout: post
title: "Personalize PubMed"
tag: css
---

![](/images/pubmed-1.png)

#### Personalize the search result page

![](/images/pubmed-2.png)

#### Personalize the abstract page.

<!--more-->

The  new PubMed has been around for sometime. It looks much better both on the desktop and on mobile browser. That is, compared with its old version. Some of the lethal design faults include... 

- fonts too damn small
- header too damn big
- too many useless stuff
- subtle color change for visited links
- NO IMPACT FACTOR !!!

Using the chrome plug-in stylish and some rudimentary css knowledge, I have redesign the display. Change the fonts and make them bigger, hide all unnecessary contents, highlight the journal name and IF. For example:

```css
.docsum-title:visited { color: #0000bc !important }
/* make visited links appear in a specific color */

.ncbi-header { display: none !important }
/* hide the NCBI header */
```