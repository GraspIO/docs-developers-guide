# Reference Constraints

This section describes constraints that apply to reference features.

## Literal

Its meaning is the same as for similar value constraint. It restricts user choice to a single reference, or a list of references if multiple literal constraints are used together.

Literals have one required attribute: `value`. This is the reference that will be added to the element if this literal is selected from the list of available options.

If the literal's `label` attribute is set, user will see the label as a choice. Otherwise, the value will be shown.

## Reference Scope

This constraint control the search area for applicable references. There can be many elements of a given type in your repository, but often you need to remove options that are not related to the scope in which the model element is being edited.

If this constraint is not set, the entire repository will be searched.

It has the following attributes:

* `scope`: list of choices described below, required -  how broadly to search for referenceable elements;
* `ancestorClass`: Class, optional - class of an ancestor under which to search if the scope is 'ancestor';
* `ancestor`: Reference, optional - reference to the actual element in a model under which to search if the scope is 'ancestor',
* `model`: Model, optional - a model in the repository in which to search. If not set, the element's own model will be searched.

Scope Meaning:

* model: only references to elements in the current model or in the model specified in the "model" attribute
* ancestor: only references to elements that share the same ancestor element:
    * same root element with the referring element - if both ancestor and ancestorClass attributes are missing;
    * same ancestor with the referring element, and the ancestor is of type specified in ancestorClass attribute;
    * actual ancestor element is specified in the ancestor attribute (possibly as a parameter reference)

## Class Features

This constraint is meant to be used with the "Feature" reference type and limits the list of choice to features in the class specified in the constraint's `class` attribute.
