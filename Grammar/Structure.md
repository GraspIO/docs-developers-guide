# Basic Structure

Grammars can have the following elements in them:

* **Classes** describe complex structures that can contain features.
* **Data types** describe primitive types used as simple attribute values, such as strings or numbers.
* **Sections** are used to group related elements together. For example, you can have one section for classes and another one for data types.
* **Comments** are used to document the meaning of other elements and to provide rich formatting that you can use if you want to make your grammar look like a real document.

You can create any number of these elements at the top level. You can also add them into sections.

Grammars use customized head format, which adds important fields that help Grasp understand how models must be created from them:

![Grammar Head](img/GrammarHead.png)

* `root class` - zero or more classes declared in this grammar that can be used in the root of a model. If no classes are added to this list, then the grammar is considered *abstract*, i.e. users won't be able to create models directly from it, but its content can be used by other grammars.
* `headClass` - class to be used as a head class for models created from this grammar. You can leave the default value or create your own subclass of the Model class and add your own attributes to it.
* `minRootElments` and `maxRootElements` specify how many root elements can be added to the models created from this grammar.
    * If `minRootElements >= 1`, root classes will be instantiated in the order they are specified and added to the model until this requirement is satisfied.
    * `maxRootElements = -1` means there is no restriction on the maximum number.
* `defaultOutputTarget` specifies which output format must be used by default when the model is tested and deployed.
* `defaultModelEditor` specifies which editor format must be used by default when the model is opened for editing.
