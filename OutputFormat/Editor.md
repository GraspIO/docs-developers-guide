# Editor

The editor for the output format model has the following sections:

* **Global settings** with attributes that apply to the entire format model:
    *  `Target`: `string`, required - the name of this format by which it will be identified by users and client applications, e.g. "javascript" or "XML".
    *  `Template engine`: 'EJS' - the templating language in which the templates are defined.

> Currently [EJS](http://embeddedjs.com/) is the only available choice for the template engine, but more engine types might be added in the future, or it may be replaced by a structured editor.

* **Templates** will contain 1 or more output templates associated with the classes in your grammar. When generator runs, it will automatically pick the template defined for the class of an element that is currently being processed.






