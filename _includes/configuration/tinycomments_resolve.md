### `tinycomments_resolve`

{{site.requires_5_8v}}

This option adds a _Resolve Conversation_ item to the dropdown menu of the first comment in a conversation.

The `tinycomments_resolve` function should asynchronously return a flag indicating whether the comment thread was resolved using the `done` callback. Unrecoverable errors are communicated to {{site.productname}} by calling the `fail` callback instead.

The `tinycomments_resolve` function is passed a (`req`) object as the first parameter, which contains the following key-value pair:

`conversationUid`
: The uid of the conversation the reply is targeting.

The `done` callback should accept the following object:

```js
{
  canResolve: boolean // whether or not the conversation can be resolved
  reason?: string // an optional string explaining why resolving was not allowed (if canResolve is false)
}
```

> **Note**: Failure to resolve due to permissions or business rules should be indicated by `canResolve: false`, while unexpected errors should be indicated using the `fail` callback.

For example:

```js
function resolve_comment_thread(ref, done, fail) {
  let conversationUid = ref.conversationUid;
  fetch('https://api.example/conversations/' + conversationUid, {
    method: 'PUT',
  }).then((response) => {
    if (response.ok) {
      done({ canResolve: true });
    } else if (response.status === 403) {
      done({ canResolve: false });
    } else {
      fail(new Error('Something has gone wrong...'));
    }
  });
}

tinymce.init({
  selector: '#editor',
  plugins: 'tinycomments',
  tinycomments_mode: 'callback',
  tinycomments_create: create_comment,
  tinycomments_reply: reply_comment,
  tinycomments_edit_comment: edit_comment,
  tinycomments_resolve: resolve_comment_thread, // Add the callback to TinyMCE
  tinycomments_delete: delete_comment_thread,
  tinycomments_delete_all: delete_all_comment_threads,
  tinycomments_delete_comment: delete_comment,
  tinycomments_lookup: lookup_comment
});
```

