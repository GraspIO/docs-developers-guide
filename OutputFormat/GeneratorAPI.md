# Generator API

You don't call the generator yourself, except when debugging it. All generation happens automatically when necessary to update model targets.

However, EJS templates that produce the output may need to use Javascript objects and methods exposed by the generator in order to implement template's logic.

### element
`element` is a parameter within the template that indicates the currently processed model element. From it you can access element's features by their name, e.g. `element.myAttr` or `element['myAttr']`.

### next(child, connector)
The most important function is `next()` - it instructs generator to visit attribute(s) of the current element and apply their templates.

It takes two optional parameters:

* `child` - which child element to process next. If skipped or set to `undefined`, then all element's children will be processed in the order in which their containing attributes are declared in the class.
* `connector` - a string to insert between generated elements. It is often useful when your element's attribute is an array and you want to connect the output produced by them with some sort of delimiter.

To better understand the `connector` attribute, consider the following example: you need to generate a code 'A or B or C', where A, B and C are values in the 'listAttr' attribute. You can produce this output by putting `<% next(element.listAttr), ' or ' %>` into the template - it will automatically insert 'or' between each element.

### setHeader(header, value)

This method is used to add custom headers to the target document generated from the model. The semantics of the headers is up to you - the subscriber for the target should know what to do with the headers that your format generates.

The parameters that this method takes are the name of the header (string) and an arbitrary JSON value.

### resolve(ref)

Use this method to work with reference features of your element. It takes the reference GUID (i.e. the value of the feature) as a parameter and returns an actual model element for that reference. Then you can extract values from the element and insert them into your output, e.g.:

`<%- resolve(element.myRefFeature).someAttribute %>`

> Note that you **cannot** pass resolved references to the `next()` method in attempt to traverse the tree of another model - this can lead to unexpected results.

### parent(_element)

This method returns a parent of the current element (if parameter is not set) or an ancestor element that is up in the model tree (e.g. parent's parent).

You can use it to extract parent features and insert them into generated output of the current element.

### up(query, includeSelf)

Finds an ancestor of the current element that matches specified criteria. It will test every element until it reaches the root of the tree and will return the first element that matches the `query` criteria.

* `query`: function or string - test function (can use 'this' or first argument as tested element) or [JSONPath expression](http://code.google.com/p/jsonpath/)
* `includeSelf`: boolean - set to true if start test with the current element (i.e. look for ancestor or self); false if start with the parent.

### stack()

Returns a list with all elements that lead from the root to the current element.
