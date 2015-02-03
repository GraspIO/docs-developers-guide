# Value Constraints

This section describes constraints that are applicable to primitive data types and attributes.

## Literal

`Literal` is the most frequently used constraint type. It restricts user choice to a single value, or a list of values if multiple literal constraints are used together. This is how you build enumerated types and make the values appear in a dropdown in the editor.

Literals have one required attribute: `value`. This is what will be added to the model if this literal is selected from the list of available options.

If the literal's `label` attribute is set, user will see the label as a choice. Otherwise, the value will be shown.

## Value Range

`Range` constraint has optional `from` and `to` attributes that describe a range of allowed (or excluded) values. Typically it is used with numeric fields, but can sometimes be used with strings and dates too.

## Regular Expression

`Regular Expression` constraint checks whether the value entered by a user matches against a regular expression. For example, by using it you can define a 'US phone number' data type that allows entering only valid phone numbers.

This constraint type has the following attributes:

* `pattern`: `regexp`, required - the regular expression pattern. Please refer to [Javascript documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) for format details.
* `modifiers`: `string`, list of up to 3 non-repeating predefined values - regular expression flags:
    * `case-insensitive` ('i')
    * `global match` ('g')
    * `multi-line` ('m')

## Remote Data Source

This constraint retrieves a list of allowed values from the HTTP server. It expects the results of the call to return a JSON array of objects and has the following configuration attributes:

* `url`: `URL`, required - absolute or relative URL from which this constraint can retrieve the choices.
* `method`: 'GET' or 'POST', required, default is 'GET' - HTTP method to use when calling the server.
* `valueProperty`: `string`, required - name of an attribute in the returned JSON objects that contains the value to be stored if this option is selected.
* `labelProperty`: `string`, required - name of an attribute in the returned JSON objects that contains the value to be shown to the user for selection.

## Allow User to Enter Custom Value

This constraint does what the name suggests: allows user to enter any value allowed by the data type. It is required in some cases where you want to give users a list of predefined options to begin with, but need to give them an ability to enter their own value if they have to. In such scenario you would add predefined options as literal constraints and add the "allow to enter custom value" to remove the exclusivity restriction.
