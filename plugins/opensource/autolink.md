---
layout: default
title: Autolink plugin
title_nav: Autolink
description: Automatically create hyperlinks.
keywords: link url urls
---

The Autolink plugin automatically creates hyperlinks when a user types a valid, complete URL. For example `www.example.com` is converted to `http://www.example.com`.

Note that this option won't convert incomplete URLs. For example `example.com` would remain as unlinked text and URLs must include `www` to be automatically converted.

> **Note**: Pasted URLs are automatically converted to `a` elements by {{site.productname}}'s core code, not by the autolink plugin. Therefore, behaviour and settings described here do not apply to pasted links.

## Basic setup

```js
tinymce.init({
  selector: 'textarea',  // change this value according to your HTML
  plugins: 'autolink'
});
```

## Options

{% include configuration/default_link_target.md %}

{% include configuration/link_default_protocol.md %}
