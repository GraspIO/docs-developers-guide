# HTML Template Reference

## Template Structure

When rendered in the browser by the structured editor, models are represented by a HTML DOM tree marked with special CSS classes that indicate roles of its nodes:

* `ct_element` - model elements
* `ct_attribute` - element's attribute features
* `ct_reference` - element's reference features

Attribute and reference nodes are contained inside element nodes, possibly wrapped in some other DOM nodes.

Within each attribute or reference node, there has to be a special *slot* node marked by the CSS class `ct_slot`. This is the place where attribute values, reference values or child elements will be dynamically inserted by the editor.

When rendered, each attribute or reference value inside the slot is automatically wrapped into its own DOM node marked with the CSS class `ct_value`. It contains the display value of that attribute or reference.

Custom CSS classes may be added to all the nodes as long as ther names do not conflict with [reserved class names](CSSClassReference.md).

In order to identify attributes and references within the element, their nodes are annotated with CSS classes indicating their names in the model. The name of such CSS class consists of the prefix `ctn_` followed by the name of the feature. For example, an instance of the feature 'name' is marked with CSS class `ctn_name`.

## Implementing Your Own Template

When defining your own DOM template for some grammar class, you need to design the internal layout of the `ct_element` node up to the `ct_clot` level. For example, here is how a simple template HTML could look like:

```HTML
Element starts
<span class='ct_attribute ctn_feature1'>
  Feature 1: <span class='ct_slot'></span>
</span>
<span class='ct_reference ctn_feature2'>
  Feature 2: <span class='ct_slot'></span>
</span>
Element ends
```

The rest of the DOM structure is added by Grasp when model is opened in the browser.

When you add a template for a grammar class, Grasp automatically generates default template for that class to use as a starting point. It contains HTML elements for all features of the class, as well as other frequently used standard markup, which is described in the next section.

You can customize generated template to make the editor for this grammar class look the way you want.

## CSS Class Reference

You already know about several standard HTML nodes and CSS classes that must be a part of every structured template:

There are several other CSS classes that you can use. Here is a complete list.

### Feature-related Classes

These CSS classes form the structure of the template, indicating where to place editors for element's features and values.

| CSS class        | Description   |
| ---------------- |---------------|
| `ct_attribute`    | Placeholder for a model attribute feature |
| `ct_reference`    | Placeholder for a model reference feature |
| `ctn_{feature-name}`   | Used together with `ct_attribute` or `ct_reference` to indicate which feature it is for |
| `ct_auto_hide`    | Used together with `ct_attribute` or `ct_reference` to hide this feature if it has no values |
| `ct_always_hide`  | Used together with `ct_attribute` or `ct_reference` to always hide this feature when element is not selected |
| `ct_slot`         | Slot for the actual attribute or reference values |

### Supporting Markup

These CSS classes mark control structures of the template and indicate special roles of some of the element's features.

| CSS class        | Description   |
| ---------------- |---------------|
| `ct_class_name` | Marks node with element's class name |
| `ct_feature_name` | Marks node with feature name |
| `ct_fold_button`    | Placeholder for the button that folds or expands element |
| `ct_handle` | Marks the node that, when clicked on, will open an editor to replace the element's class |
| `ct_move_handle` | Add to the node that you want to use for dragging the element around |
| `ct_element_icon` | Placeholder for element's icon |

### Dynamically Added Classes

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
