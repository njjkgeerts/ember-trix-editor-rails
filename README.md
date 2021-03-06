# ember-trix-editor-rails

This is a Ember-Rails package of [Ember Trix Editor](https://github.com/lynnetye/ember-trix-editor) by 
[Lynne Tye] (https://github.com/lynnetye).

Ember Trix Editor is an Ember addon that wraps Basecamp's [Trix editor](https://github.com/basecamp/trix)
in an Ember component. [Visit our demo](https://lynnetye.github.io/ember-trix-editor/) to see it in action.
(Code for our demo is located in [tests/dummy/app](tests/dummy/app).)

The component is consistent with Ember's data-down actions-up pattern:

### "Data down" to `{{trix-editor}}`
* `attachmentsDisabled` (boolean; if truthy, calls preventDefault() on the trix-file-accept event)
* `autofocus` (boolean; if truthy, adds the HTML autofocus attribute to the trix-editor tag)
* `editorClass` (string; space-separated list of class names that will be passed to the class attribute of the trix-editor tag)
* `placeholder` (string; text that will show up in the editor when it's empty)
* `value` (string; text to pre-populate the trix-editor)

### "Actions up" from `{{trix-editor}}`
* `trix-attachment-add`
* `trix-attachment-remove`
* `trix-blur`
* `trix-change`
* `trix-file-accept`
* `trix-focus`
* `trix-initialize`
* `trix-selection-change`

All actions send up a jQuery event, from which the original event and editor
property can be extracted.
```js
actions: {
  handleTrixAttachmentAdd(jqEvent) {
    var attachment = jqEvent.originalEvent.attachment;
    if (attachment.file) {
      // update file to server
      // call attachment.setAttributes();
    }
  }
}
```
