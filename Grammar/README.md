# Grammmar

Every document in Grasp is built in accordance with one or more grammars, also called metamodels. They are special models that describe how other models must be structured, what features their elements can contain and what values those features can take.

There are many existing ways in software industry to describe information structure to make it easier to process it in automated fashion. Some examples:

* Relational databases use DDL (data definition language) to describe tables that store data in rows and columns.
* XML documents are often based on XSD (XML Schema Definition) that describes which elements and attributes are allowed in them.
* Programming languages are specified using grammars in EBNF (Extended Backus–Naur Form) format, from which a parser can be generated.
* Business processes are often defined in BPMN (Business Process Modeling Notation) format that describes how they are organized into activities, flows and so on.

Grammars in Grasp are similar to that. You can create a grammar that describes a data structure, a language syntax, building blocks for a process, or something else that is relevant to your domain.

From such grammar an editor can be generated for documents that conform to it. You can also develop custom editor formats and code generators that convert model's AST into some other representation, e.g. a configuration file or programming code.

As any other Grasp model, grammar documents too have their own special grammar to describe their structure. It is stored in the core system repository that is automatically linked into all other repositories.

The main grammar from which a model is produced is referenced by the `grammarRef` attribute in its JSON document. Classes from other grammars can also be used if they are utilized by features declared in the main grammar.

> ### Creating a New Grammar
> In order to create a grammar click on the **⊕** button in the repository explorer and select the "Grammar" from the list of options.
