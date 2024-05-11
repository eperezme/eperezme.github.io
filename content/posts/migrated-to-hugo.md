---
title: "Migrated to Hugo and enabling KaTeX"
date: 2024-05-11T13:52:58+02:00
lastmod: 2024-05-11T13:52:58+02:00
author: ["Edu"]
categories: 
- latex
- html
tags: 
- code
- blog
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

So I have migrated my older blog to a [Hugo](https://gohugo.io/) template named [PaperMod](https://github.com/adityatelange/hugo-PaperMod).

And had to enable the latex support as noted by [this user](https://kiwamizamurai.github.io/posts/2022-03-06/)

# Content
## Setup
First of all, create a file `layouts/partials/extend_head.html` with the following content.
```html
{{ if or .Params.math .Site.Params.math }}
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.2/dist/katex.min.css" integrity="sha384-MlJdn/WNKDGXveldHDdyRP1R4CTHr3FeuDNfhsLPYrq2t0UBkUdK2jyTnXPEK1NQ" crossorigin="anonymous">
<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.2/dist/katex.min.js" integrity="sha384-VQ8d8WVFw0yHhCk5E8I86oOhv48xLpnDZx5T9GogA/Y84DcCKWXDmSDfn13bzFZY" crossorigin="anonymous"></script>
<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.2/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>

<!-- for inline -->>
<script>
document.addEventListener("DOMContentLoaded", function() {
    renderMathInElement(document.body, {
        delimiters: [
            {left: "$$", right: "$$", display: true},
            {left: "$", right: "$", display: false}
        ]
    });
});
</script>
{{ end }}
```

Then add to your `hugo.yml` or `config.yml` the following parameter:
```yml
params:
    math: true
```

Aaaand thats all :D
