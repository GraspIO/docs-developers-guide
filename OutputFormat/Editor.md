# Editor

The editor for the output format model has the following sections:

* **Global settings** with attributes that apply to the entire format model:
    *  `Target`: `string`, required - the name of this format by which it will be identified by users and client applications, e.g. "javascript" or "XML".
    *  `Template engine`: 'EJS' - the templating language in which the templates are defined.

> Currently [EJS](http://embeddedjs.com/) is the only available choice for the template engine.

* **Before model**: optional template to run first when generation starts. It will take the model head as an "element" context parameter.
* **Templates**: 1 or more output templates associated with the classes in your grammar. When generator runs, it will automatically pick the template defined for the class of an element that is currently being processed.
* **All other classes**: optional template to apply to all grammar classes for which dedicated templates are not specified.
* **After model**: optional template to run at the very end after visiting all elements. It will take model head as an "element" context parameter.

Here is what a format editor looks like:

![Output Format Model](img/NewOutputFormatModel.png)





