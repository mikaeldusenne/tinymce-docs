---
layout: default
title: Custom sidebar
title_nav: Custom sidebar
description_short: Introducing sidebar panel creation.
description: A short introduction to creating sidebars.
keywords: sidebar
---

{{site.productname}} allows developers to create sidebars and add custom UI widgets inside a constrained and easily accessible area of the editor. The sidebar is designed to allow administrators and plugin developers to provide additional tools that can be accessed by {{site.productname}} users.

## Editor sidebar API

The sidebar API allows developers to add sidebars on editor instances in a similar way as adding buttons or menu items. Developers can either add sidebars directly in the `tinymce.init` using the setup callback or inside your plugin.

This is the syntax for the addSidebar function: `editor.ui.registry.addSidebar(name:String, spec:Object)`

When a new sidebar is registered, a corresponding toolbar button for toggling the sidebar open and close is also created using the same name. This button can then be included in the toolbar by adding the sidebar name to the [`toolbar`]({{site.baseurl}}/configure/editor-appearance/#toolbar/) option.

### Specification object

#### `tooltip`

The `tooltip` specifies a tooltip to be displayed when hovering over the sidebar toggle button.

**Type**: `String`

#### `icon`

The `icon` specifies an icon for the sidebar toggle button. The icon should be the name of an icon provided by the {{site.productname}} skin or a [custom icon]({{site.baseurl}}/api/tinymce.editor.ui/tinymce.editor.ui.registry/#addicon/).

**Type**: `String`

#### `onSetup`

The `onSetup` specifies a function to be called when the panel is first created. It passes in an API object and should return a callback that takes an API. The default is `(api) => (api) => {}`.

`onSetup` is a complex property. It requires a function that takes the sidebar’s API and should return a callback that takes the sidebar's API and returns nothing. This occurs because `onSetup` runs whenever the sidebar is rendered, and the returned callback is executed when the sidebar is destroyed. Therefore the returned function is essentially an `onTeardown` handler, and can be used to unbind events and callbacks.

**Type**: `Function`

#### `onShow`

The `onShow` specifies a function to be called when the panel displayed. It passes in an API object.

**Type**: `Function`

#### `onHide`

The `onHide` specifies a function to be called when the panel is hidden. It passes in an API  object.

**Type**: `Function`

### API Object

#### `element():HTMLElement`

The `element():HTMLElement` function returns the root element of the sidebar panel.

## Example inside the tinymce.init

```js
tinymce.init({
  ...
  toolbar: 'mysidebar',
  setup: function (editor) {
    editor.ui.registry.addSidebar('mysidebar', {
      tooltip: 'My sidebar',
      icon: 'comment',
      onSetup: function (api) {
        console.log('Render panel', api.element());
      },
      onShow: function (api) {
        console.log('Show panel', api.element());
        api.element().innerHTML = 'Hello world!';
      },
      onHide: function (api) {
        console.log('Hide panel', api.element());
      }
    });
  }
});
```

## Example inside a TinyMCE plugin

```js
tinymce.PluginManager.add('myplugin', function (editor) {
  editor.ui.registry.addSidebar('mysidebar', {
    tooltip: 'My sidebar',
    icon: 'comment',
    onSetup: function (api) {
      console.log('Render panel', api.element());
    },
    onShow: function (api) {
      console.log('Show panel', api.element());
      api.element().innerHTML = 'Hello world!';
    },
    onHide: function (api) {
      console.log('Hide panel', api.element());
    }
  });
});
```
