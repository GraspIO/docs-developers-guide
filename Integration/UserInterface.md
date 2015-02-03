# Embedded Editor

You can add Grasp editor to your own web application so that users can edit models without leaving it.

In order to embed Grasp workbench you need to add the following script to your web page:

`<script type='text/javascript' src='http://www.grasp.io/js/grasp/Grasp-embedded.js'></script>`

The script declares a class called GraspClient, which can be used to load a specific model into an embedded Grasp editor in your web page.

You need to add an empty HTML element to your page where the editor will be placed. You also need to write a small script to instantiate the Grasp client and create an embedded workbench with a configuration object that specifies which repository/model to load and where to put the workbench.

Example:

```html

<div id="MyGraspEditor"></div>

<script type='text/javascript' src='http://www.grasp.io/js/grasp/Grasp-embedded.js'></script>

<script type="text/javascript">
    var graspClient = new GraspClient();
	var graspConfig = {
        containerId: "MyGraspEditor",
        repository: 'repositoryGUID',
        model: 'modelGUID'
	};
	graspClient.openWorkbench(graspConfig);
</script>
<script type="text/javascript"
	src="http://www.grasp.io/js/grasp/Grasp-embedded.js"></script>
```
