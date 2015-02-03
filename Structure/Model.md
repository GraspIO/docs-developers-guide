# Model Organization

Pretty much all content in Grasp is stored as a model document that is structured accordingly to its grammar.

Model is a JSON document with a hierarchical data structure that consists of nested elements (JSON objects) which in turn can have fields, called features.

Just like repositories, models are uniquely identified by a GUID - a short string by which Grasp can easily locate and serve any model in its document-oriented database.

Model JSON document is comprised of several main sections:

* Identification and version control fields:
    * GUID;
    * repository reference;
    * workbench reference;
    * grammar reference;
    * model and grammar version numbers;
    * creation date;
    * original author reference;
    * last modification date.
* Head - an element of a special grammar type that stores model metadata: name, description, tags and so on. Different model types can have different head element types, described by a separate grammar.
* Body - the content of the model itself (AST) accordingly to the schema declared in the model's grammar.
* Index of model elements and references.

Model elements can have the following attributes:

* **id** - a unique identifier of the element within the model.
* **GUID** which is auto-generated as `[model-GUID]_[element-ID]`.
* **_class** - type of this element: a reference to the Class element in the grammar.
* Element features, as dictated by its class:
    * simple attributes - strings, numbers, etc.
    * complex attributes, or containments - sub-elements described by their own class in the grammar.
    * references to other elements defined in the same or different model in the Grasp repository.
    * Features can be required, optional and arrays.

Models have references to the repository and, if not checked in yet, to the workbench in which they were created or modified. Repositories and workbenches are defined in their own special Grasp models, so the references are simply GUIDs pointing at them.

Model body can contain one or more top-level elements, also called root elements. Together with their sub-elements they form an Abstract Syntax Tree (AST) of the model, from which any number of concrere representations (projections) can be generated.

Here is an example of a model that has one root element with features of different kinds (a simple attribute, a reference and a sub-element):

```javascript
{
    "GUID": "NuUAjXUQ25",
    "head": {
        "_class": "r_Model",
        "id": "icxnki",
        "name": "Example model"
    },
    "body": [
        {
            "_class": "azZfyXRWiC_e9dk5a",
            "id": "v1nz4q",
            "stringFeature": "some text value",
            "booleanFeature": true,
            "referenceFeature": "NuUAjXUQ25_v1nz4q",
            "complexFeature": {
                "_class": "azZfyXRWiC_e9dk5a",
                "id": "v1nz4q",
                "stringFeature": "some other value",
            }
        }
    ],
    "grammarRef": "azZfyXRWiC",
    "version": 4,
    "created": "2015-01-01T10:00:00.000Z",
    "grammarVersion": 5,
    "createdByRef": "testUser",
    "modified": "2015-04-10T05:02:06.614Z"
}
```

Such grammar-driven AST structure with built-in reference management is a powerful way of organizing structured information, from data records to scripts.

GUID-based element identification and referencing may appear confusing when looking at the JSON representation, but in the UI all such references are shown as user-friendly values, such as element's name or label.

The main benefit of GUID-based identification is that it becomes easy to rename elements and move them around without breaking references to them from the same or other models in the repository.
