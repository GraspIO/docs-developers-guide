# Grammmar

Every model in Grasp is built in accordance with one or more *grammars*, also called *metamodels*. They are special models that describe how other models must be structured, what attributes can exist in each model element and which values those attributes can take.

In computer world there are many existing ways to describe the structure of some information in order to make it easier to handle in automated fashion. Just a few examples:

* Relational databases use DDL (data definition language) to describe the structure of the tables that store users' data.
* XML documents are often based on XSD (XML Schema Definition) that describes which elements and attributes are allowed in them.
* Programming languages are described using grammars in EBNF (Extended Backus–Naur Form) format that tells the compiler how to parse programs written in that lanugage.
* Business processes are frequently defined in BPMN (Business Process Modeling Notation) format that describes how they are organized into activities, flows and so on.

Grammars in Grasp are similar to that. You can create a grammar that describes a data structure, a language, a process, or something else that is relevant to your business domain.

And then you can give your users an editor that will help them to edit documents, or *models*, that conform to your grammar. You can also develop additonal components that will give you ability to transform such models into a form that your computer systems need and deliver user-created content to them.

Grammars, just like any other Grasp model, are stored in JSON (JavaScript Object Notation) format. As such, they can be read and edited even their text format, but of course we think it is more convenient to do via Grasp editor itself.

And as any other Grasp model, grammars too have a grammar that describes their structure. It is stored in a system repository that is automatically linked with all other repositories.

The main grammar from which model is created is referenced by the attribute `grammarRef` in the model document. However, classes from other grammars can also be used if they are referenced from the main grammar.

## Creating a Grammar
In order to create a grammar you need to have a proper permission for the repository. If you have it, you can click on the **⊕** button in the repository explorer and select "Grammar" from the dropdown.

As you build your new grammar, it will automatically be loaded into Grasp so that you can test it right away. Sometimes, however, you may need to refresh your browser in order to let the latest changes propagate through the workbench.
