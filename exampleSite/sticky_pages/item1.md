---
title = "Main sticky page"
description = "Application for doing cool things."
date: '2017-07-23'
stickies:
  - main
weight: 1
---

## Sticky 1

This is the main page (weight: 1) that is shown entirely in the </stickies> or in the </sticky_pages/>.

### Sticky list pages

A special kind of posts list is implemented. This allows to show the first article completely and the other articles as a list with summaries. For that, we use the implemented template `list_first_plain_sticky.html` in `partial`. You can use it in two ways:  

1. With Taxonomy
This is implemented in the `exampleSite`.
    + Create a new taxonomy like 'sticky':
    
    ```
    [Taxonomies]
      tag = "tags"
      category = "categories"
      sticky = "stickies"
    ```
    + Create a folder `layout` > `taxonomy`
    + Create a html file named `sticky.html` with this code:
    
    ```
    {{ define "main" }}
      {{ if isset .Site.Taxonomies "sticky" }}
        {{ partial "list_first_plain_sticky" . }}
      {{ end }}
    {{ end }}
    ```
  
    + Add taxonomy `stickies` in a post or a page. The newest page or the page with `weight = 1` will be shown entirely before the other of the same taxonomy (that will only show a summary). In the exampleSite, pages in `sticky_pages` have this taxonomy.

