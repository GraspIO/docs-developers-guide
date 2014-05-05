# Model Organization

Pretty much everything in Grasp is represented by a model that is structured accordingly to its *grammar*.

> Model/grammar format and structured editor's implementation is based on the modified version of Martin Tiede's [Concrete Editor](http://concrete-editor.org). You can get an alternative description of it from [here](http://concrete-editor.org/docs), just be mindful of Grasp's differences such as GUID-based identification scheme.

Model is a JSON document that describes the structure and the content of an information entity stored in the repository.

Model is uniquely identified by a *GUID* - short string by which Grasp can easily locate and serve any model in its database. GUID is an equivalent of a primary key in a relational database.

There are 3 main parts in the model's JSON document:

* Basic fields, such as:
    * GUID
    * repository reference
    * workbench reference
    * grammar reference
    * version number
* Model's **head** - a special embedded model that contains metainformation: name, description, tags, etc. The structure of the head model is controlled by its own grammar and can be customized.
* Model's **body** - the content of the model itself.

Model consists of *elements*. Each element is stored as a JSON object within model's body. Elements have the following attributes:

* **id** - unique identifier of the element within the model. To make a globally unique identifier out of it, element's GUID is automatically generated as `[model-GUID]_[element-ID]`.
* **_class** - reference to the GUID of the *Class* element in the model's grammar that describes the type of this element.
* Other attributes that contain element's own properties, called features, in accordance to its Grasp type:
    * simple attributes - strings, numbers, etc.
    * complex attributes, or *containments* - sub-elements described by their own class in the grammar.
    * references to other elements defined in the same or different model in the Grasp repository.

Models have references to the repository and, possibly, workbench in which they were created or modified. Both the repository and the workbench are represented by their own Grasp models, so the references are simply GUIDs of those models.

Model body can contain one or more top-level elements, also called *root* elements.

An element can contain multiple features. Depending on the class definition in the grammar, some features can be made required, some are optional, and some can represent arrays of values.

The element/feature structure essentially describes a *syntax tree* of the model, from which any number of concrere representations can be generated.

Here is a very simple example of a model which has one root element with some simple features (attributes and references) and a sub-element:

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
            "stringFeature": "someValue",
            "booleanFeature": true,
            "referenceFeature": "NuUAjXUQ25_v1nz4q",
            "complexFeature": {
                "_class": "azZfyXRWiC_e9dk5a",
                "id": "v1nz4q",
                "stringFeature": "someValue",
            }
        }
    ],
    "grammarRef": "azZfyXRWiC",
    "version": 4,
    "created": "2014-01-01T10:00:00.000Z",
    "grammarVersion": 5,
    "createdByRef": "testUser",
    "modified": "2014-04-10T05:02:06.614Z"
}
```

This grammar-driven element/feature structure with reference management is an extremely powerful way of organizing data that can be used to describe all kinds of information of knowledge, from simple to very complex.

GUID-based element identification and references may appear confusing when you first look at the model's JSON representation, but typically you will need to be concerned with them. In Grasp editor all such references are replaced by their user-frienly descriptive counterparts, such as element's name or label.

The main benefit of this is that you can easily rename elements or move them around without breaking all the references to them from the same or other models in the repository. In other words, it makes your repository more stable and easier to maintain in the long term.
