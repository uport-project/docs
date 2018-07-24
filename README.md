uPort Docs
============

Our developer site that is built from this repository can be found here [developer.uport.me](https://developer.uport.me). The developer site generator is located [here](https://github.com/uport-project/uport-project.github.io).

## uPort markdown conventions for doc-site generation

The uPort site generator assumes convention over configuration.  For the  markdown to be included into our documentation site, consider the following.

### Header guidelines

1. Be consistent with header hierarchy.  Don't skip sizes.
1. Only use H1 headers for something intended to be a title (keep it short)
1. Both H1 and H2 headers are used for site navigation and category indexing.  Keep them shorter and contextual.
1. Always leave 1 space after a hash tag.
1. Avoid periods, special characters and punctuation in any H1 or H2 headlines.
1. For topics that are nested use a smaller-header hierarchy to represent a deeper nesting.
1. Avoid too-many H2 headers in a single document.  Use better information architecture.

### Front matter conventions

The front matter is the way to inform the site generator how to handle each file.  Each markdown document intended to be a source for the developer site should have a minimum set of front matter attributes, written in YAML.

Place a modified version of the following directly at the top of each markdown file with no preceding spaces.

```
---
title: "Attesting Credentials"
index: 1
category: "guides"
type: "content"
---

```

**The following keys are required:**
1. title
1. category
1. type

**The following are optional:**
1. index
1. announcement

#### Front matter (title)

  Used for the page title as well as navigation links.  They should be kept short and be the same as H1 headings in most cases.  There may be times when these should differ, for example, having a link to display by a different name than represented by the heading.

#### Front matter (index)

  Think of this as the display order for the content; it is used to sort each category and control the ordering of navigation links.  *Note:* if the frontmatter does not contain an index, the site-generator will assume it is sub-content that does not belong in table of contents or navigation menu.

#### Front matter (category)

  Categories are used to aggregate markdown for header menus and contextual relevancy.  The main categories are `guides`, `overview`, and `reference` but new categories may be added at any time.  When a new category is added that follows the proper conventions it will be included in the header navigation menu.  The previously mentioned categories default to the first three navigation sections in the header. New categories will added onto the end and displayed last.

#### Front matter (type)

  The type is important for publishing.  If the type is not "content" it will not be published or displayed.

#### Front matter (announcement)

  This is used to broadcast a message across all pages on the site.  Use sparingly.

### Repository guidelines

Please use this general guidance:
1. Keep the readme short and sweet and detail how to contribute / support.
2. Put detailed content, like implementation details in the /docs folder.
3. Docs folders can have:  guides, tutorials, sdk/api reference documentation.
4. Follow the documentation guidelines on the docs repo.

One suggestion I have is to use a similar nomenclature as this repo for the /docs folder.

Suggested:

* /docs
  * /guides
  * /reference
  * /overview
  * index.md (can use this if you want Oloron to have it’s own index. page, otherwise we default to the markdown-frontmatter’s first “guide” at index 0)
* readme.md (add install information, support and contribution information, NPM release badges, etc. )
