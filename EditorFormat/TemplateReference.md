# HTML Template Format

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

