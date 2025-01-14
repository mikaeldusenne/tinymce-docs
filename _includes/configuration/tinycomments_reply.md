### `tinycomments_reply`

The Comments plugin uses the `tinycomments_reply` function to reply to a comment.

The `tinycomments_reply` function saves the comment as a reply to an existing conversation and returns via the `done` callback once successful. Unrecoverable errors are communicated to {{site.productname}} by calling the `fail` callback instead.

The `tinycomments_reply` function is given a request (req) object as the first parameter, which has these fields:

`conversationUid`
: The uid of the conversation the reply is targeting.

`content`
: The content of the comment to create.

`createdAt`
: The date the comment was created.

The `done` callback should accept the following object:

```js
{
  commentUid: string // the value of the new comment uid
}
```

For example:

```js
function reply_comment(ref, done, fail) {
  let conversationUid = ref.conversationUid;
  let content = ref.content;
  let createdAt = ref.createdAt;

  fetch('https://api.example/conversations/' + conversationUid, {
    method: 'POST',
    body: JSON.stringify({ content: content, createdAt: createdAt }),
    headers: {
      Accept: 'application/json',
      'Content-Type': 'application/json',
    },
  })
    .then((response) => {
      if (!response.ok) {
        throw new Error('Failed to reply to comment');
      }
      return response.json();
    })
    .then((ref2) => {
      let commentUid = ref2.commentUid;
      done({ commentUid: commentUid });
    })
    .catch((e) => {
      fail(e);
    });
}

tinymce.init({
  selector: '#editor',
  plugins: 'tinycomments',
  tinycomments_mode: 'callback',
  tinycomments_create: create_comment,
  tinycomments_reply: reply_comment, // Add the callback to TinyMCE
  tinycomments_edit_comment: edit_comment,
  tinycomments_delete: delete_comment_thread,
  tinycomments_delete_all: delete_all_comment_threads,
  tinycomments_delete_comment: delete_comment,
  tinycomments_lookup: lookup_comment
});
```

