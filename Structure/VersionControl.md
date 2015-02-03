# Version Control

Grasp has a built-in lightweight version control system designed to be fast, scalable and flexible enough without confusing non-technical users with difficult SCM concepts such as branching, merging and so on.

When a user connects to a repository, a private workbench is automatically created to persist changes until they are published into the main repository.

Only new and modified models are stored in the workbench. The rest of them is loaded directly from the main repository. This helps to isolate users without incurring the overhead of duplicating the entire repository for each of them.

Every time when model changes are published into the repository, a new incremental version number for it is assigned.

All versions of the same model have the same model GUID, so in order to get a specific version of the model you need to specify both the GUID and the version number. If you use only the GUID you will get either a private copy from your own workbench (if you have one) or the latest version from the repository.
