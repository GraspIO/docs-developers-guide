# Version Control

Grasp has built-in lightweight version control system designed to be fast, scalable and give non-technical users enough freedom without confusing them with difficult concepts such as branching, merging and so on.

When user opens a repository, a private *workbench* is created to store changes made by the user to some of the models until they are published into the main repository.

Only models that have been modified are stored in the workbench, while the rest of the is loaded directly from the repository. This gives users sufficient level of isolation from each other without incurring the cost of duplicating the entire repository as it is typically required with some of the more traditional version control systems such as Subversion or Git.

Every time when model changes are published into the repository, a new version of it is created. Version numbers are incremental and assigned at the model level - i.e. you will have version 1 of your model, then version 2 and so on.

Different versions of the same model will have the same model GUID, so in order to get a specific version of the model you will need to specify both its GUID and the version number. If you use only the GUID you will get either a copy from your own workbench (if you have it) or the latest version from the repository.
