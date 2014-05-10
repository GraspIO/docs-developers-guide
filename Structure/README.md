# Repository and Model Structure

First thing that Grasp developers need to understand is how content is organized and structured in it. From the user guide you already know that Grasp stores it in *repositories* that contain documents called *models*. A single Grasp installation can contain multiple repositories, each of which can contain multiple models.

A repository is identified by its GUID which is unique within Grasp installation.

Repositories belong to *organizations*, also known as *tenants*. Each organization can have multiple repositories.

A user in Grasp can belong to multiple organizations and will have access to all repositories of those organizations.

Users can also access repositories that are marked as 'public', although they will not be able to contribute to them unless they are members of the organization that owns such repository.

Within repository, there is no intrinistic folder structure by which models are grouped together. Instead, Grasp relies on dynamic organization strategies such as grouping all models of the same type, or dynamically generating folders based on models' tags.

