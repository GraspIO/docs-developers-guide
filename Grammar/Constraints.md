# Constraints

By using only data types and classes in your grammar, you can already achieve quite a bit. However, there are situations when it is not enough, for example the following use cases:

* Restricting allowed attribute values, e.g. to a list of choices.
* Restricting allowed reference by using some scope rules, e.g. only use elements defined in a specific model.
* Changing presentation of values, adding user-friendly descriptions, etc.

That is where constraints play important role.
Constraints are declarative rules that restrict the entire possible range of some data type or reference set to a subset of valid values, and, in some cases, describe how those values should be presented in the Grasp editor.

They can be defined either at the data type level, in which case they apply to all attributes created from that data type, or at the level of a feature defined in a class - in this case they will apply only to the attributes or references in the elements created from such class.

Here is an example of constraints applied at the attribute level in order to give user a set of values to choose from:

![Attribute constraints](img/AttributeConstraints.png)

Different constraint types are applicable to attributes/data types vs. references, as described below.

Each constraint describes one subset or single value. When several constraints are used together, at least one constraint must match in order for a value to be valid.

When there is a type hierarchy, constraints at the supertype level must be met before the constraints at the child type level can be checked.

Constraints can be inclusive or exclusive, which is controlled by a standard attribute called `exclude` (`boolean`, optional, default is `false`). Normally constraint defines which values are allowed. But if `exclude` is set to `true`, it means that all values, *excluding* specified subset, are allowed.

Another standard attribute is `label` (`string`, optional), which is used to give constraint values user-friendly descriptive names.

## Data Type and Attribute-level Constraints

This section describes constraints applicable at the data type or primitive attribute level.

### Literal

`Literal` is the most frequently used constraint type. It restricts user choice to a single value, or a list of values if multiple literal constraints are used together. This is how you build enumerated types and make the values appear in a dropdown in the editor. You have seen an example on the screenshot from above.

Literals have one required attribute: `value` (type varies). This is what will be stored in the model when user selects this literal from the list of available choices.

Depending on whether literal's `label` attribute is set, user will see either the same value on the screen or the label.

### Value Range

`Range` constraint has `from` and `to` attributes (type varies, optional) that describe a range of allowed (or excluded) values. Typically it is used with numeric fields, but can sometimes be used with strings and dates too.

### Regular Expression

`Regular Expression` constraint checks whether the value entered by a user matches against a regular expression. For example, by using it you can define a 'US phone number' data type that allows entering only valid phone numbers.

This constraint type has the following attributes:

* `pattern`: `regexp`, required - the regular expression itself. Please refer to Javascript documentation for details.
* `modifiers`: `string`, list of up to 3 non-repeating predefined values - regular expression flags:
    * `case-insensitive`
    * `global match`
    * `multi-line`

### Remote Data Source

This constraint retrieves a list of allowed values from the HTTP server. It expects the results of the call to return a JSON array of objects and has the following configuration attributes:

* `url`: `URL`, required - absolute or relative URL from which this constraint can retrieve the choices.
* `method`: 'GET' or 'POST', required, default is 'GET' - HTTP method to use when calling the server.
* `valueProperty`: `string`, required - name of an attribute in the returned JSON objects that contains the value to be stored if this option is selected.
* `labelProperty`: `string`, required - name of an attribute in the returned JSON objects that contains the value to be shown to the user for selection.
