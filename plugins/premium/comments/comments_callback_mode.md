---
layout: default
title: Configuring the Comments plugin in callback mode
title_nav: Callback mode
description: Information on configuring the Comments plugin in callback mode
keywords: comments commenting tinycomments callback
---

{% assign pluginname = "Comments" %}
{% assign plugincode = "comments" %}

**Callback mode** is the default mode for the Comments plugin. In the callback mode, callback functions are required to save user comments on a server. The Comments functions (create, reply, edit, delete comment, delete all conversations, resolve, and lookup) are configured differently depending upon the server-side storage configuration.

## Interactive example

The following example uses a simulated server (provided by [Polly.js](https://netflix.github.io/pollyjs/)) which has been hidden from the example javascript to keep the example code concise. The interactions between TinyMCE and Polly.js are visible in the browser console.

{% include live-demo.html id="comments-callback" %}

### How the comments plugin works in callback mode

All options accept functions incorporating `done` and `fail` callbacks as parameters. The function return type is not important, but all functions must call exactly one of these two callbacks: `fail` or `done`.

* The `fail` callback takes either a string or a JavaScript Error type.

* The `done` callback takes an argument specific to each function.

Most (create, reply, and edit) functions require an `id` identifying the **current author**.

Current author
: The Comments plugin does not know the name of the current user. Determining the current user and storing the comment related to that user, has to be configured by the developer.

After a user comments (triggering `tinycomments_create` for the first comment, or `tinycomments_reply` for subsequent comments), the Comments plugin requests the updated conversation using `tinycomments_lookup`, which should now contain the additional comment with the proper author.

## Configuration options

### Required options

When using callback mode, the Comments plugin requires callback functions for the following options:

* [`tinycomments_create`](#tinycomments_create)
* [`tinycomments_reply`](#tinycomments_reply)
* [`tinycomments_edit_comment`](#tinycomments_edit_comment)
* [`tinycomments_delete_comment`](#tinycomments_delete_comment)
* [`tinycomments_delete`](#tinycomments_delete)
* [`tinycomments_delete_all`](#tinycomments_delete_all)
* [`tinycomments_lookup`](#tinycomments_lookup)

The [`tinycomments_resolve`](#tinycomments_resolve) option is _optional_.

{% include configuration/tinycomments_create.md %}

{% include configuration/tinycomments_reply.md %}

{% include configuration/tinycomments_edit_comment.md %}

{% include configuration/tinycomments_resolve.md %}

{% include configuration/tinycomments_delete_comment.md %}

{% include configuration/tinycomments_delete.md %}

{% include configuration/tinycomments_delete_all.md %}

{% include configuration/tinycomments_lookup.md %}

{% include plugins/comments_open_sidebar.md %}

{% include plugins/comments_highlighting_css.md %}
