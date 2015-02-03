# CSS Class Reference

You already know about several standard HTML nodes and CSS classes that must be a part of every structured template:

There are several other CSS classes that you can use. Here is a complete list.

## Feature-related Classes

These CSS classes form the structure of the template, indicating where to place editors for element's features and values.

| CSS class        | Description   |
| ---------------- |---------------|
| `ct_attribute`    | Placeholder for a model attribute feature |
| `ct_reference`    | Placeholder for a model reference feature |
| `ctn_{feature-name}`   | Used together with `ct_attribute` or `ct_reference` to indicate which feature it is for |
| `ct_auto_hide`    | Used together with `ct_attribute` or `ct_reference` to hide this feature if it has no values |
| `ct_always_hide`  | Used together with `ct_attribute` or `ct_reference` to always hide this feature when element is not selected |
| `ct_slot`         | Slot for the actual attribute or reference values
| `ct_connector`         | Used inside `ct_slot` to separate individual values |

## Supporting Markup

These CSS classes mark control structures of the template and indicate special roles of some of the element's features.

| CSS class        | Description   |
| ---------------- |---------------|
| `ct_class_name` | Marks node with element's class name |
| `ct_feature_name` | Marks node with feature name |
| `ct_fold_button`    | Placeholder for the button that folds or expands element |
| `ct_handle` | Marks the node that, when clicked on, will open an editor to replace the element's class |
| `ct_move_handle` | Add to the node that you want to use for dragging the element around |
| `ct_element_icon` | Placeholder for element's icon |

## Dynamically Added Classes

These CSS classes are added to DOM nodes on as needed basis, so you don't need to put them into your template, but you can experiment with them in your stylesheet to achieve special look for your grammar.

| CSS class        | Description   |
| ---------------- |---------------|
| `ct_editor`     | The editor itself
| `ct_inline_editor`  | DOM node that wraps value editor
| `ct_selected`   | Marks selected element or feature
| `ct_empty`      | Empty value or element placeholder
| `ct_fold_open`  | Added to the fold button when the element is expanded
| `ct_fold_closed`    | Added to the fold button when the element is collapsed
| `ct_fold_empty` | Added to the fold button when the element has no sub-elements
| `ct_message_popup`  | Popup window shown when hovering over an element or feature
| `ct_info_message`   | Info message within the message popup window
| `ct_error_message`  | Error message within the message popup window
| `ct_error`  | Marks element or feature that has a validation error
