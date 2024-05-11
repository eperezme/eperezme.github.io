---
title: "Added Emoticons"
date: 2023-12-18T13:42:23+02:00
lastmod: 2024-05-11T13:42:23+02:00
author: ["Edu"]
categories: 
- code
- blog
tags: 
- code
- markdown
description: ""
weight: # 1 means pin the article, sort articles according to this number
slug: ""
draft: false # draft or not
comments: true
showToc: true # show contents
TocOpen: true # open contents automantically
hidemeta: false # hide information (author, create date, etc.)
disableShare: true	# do not show share button
showbreadcrumbs: true # show current path
searchHidden: true
ShowReadingTime: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: ""
    caption: ""
    alt: ""
    relative: false
editPost:
    URL: "https://github.com/eperezme/eperezme.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

# The problem

While creating this blog I realized that the emoticons were not possible to add because the Strapi database does not accept unicode characters and emojis.

So it was clear that if I wanted to add emoticons to the blog I must render them on the client side.

# The solution

I came up to the awesome package: ReactMarkdown

This allowed me to use multiple plugins to render the markdown contents super easy with only one line of code (one tag) and avoiding the `dangerouslySetInnerHTML` property.

```jsx
<ReactMarkdown remarkPlugins={[remarkGfm, emoji, remarkMath]} rehypePlugins={[rehypeKatex, rehypeHighlight]}>
    {content}
</ReactMarkdown>
```

## Code Highlight

Now I can highlight code syntax

This blog post is actualy rendered with:




```html
<div>
  <h1>
    <ReactMarkdown remarkPlugins={[remarkGfm, emoji, remarkMath]} rehypePlugins={[rehypeKatex, rehypeHighlight]}>
	  {post.title}
    </ReactMarkdown>
  </h1>
<div className="date-line">
  <span role="img" aria-label="calendar"></span>
    {formattedDate}
</div>
  <ReactMarkdown remarkPlugins={[remarkGfm, emoji, remarkMath]} rehypePlugins={[rehypeKatex, rehypeHighlight]}>
    {post.content}
  </ReactMarkdown>
</div>
```

## LaTeX
Now the blog can render math ➗ with latex: $ E = mc^2 // e^{i\pi} = -1 $

## EMOJIIII 😊 ☺️
Using the github markdown emoji markup i can write :heart: to display the heart emoji ❤️