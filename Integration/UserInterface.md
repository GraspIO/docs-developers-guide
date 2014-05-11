# User Interface Integration

You can embed Grasp UI (specifically, workbench and/or model editor) into your own web application so that users can edit models relevant to your application without leaving it.

## Load Grasp Script and Add HTML Markup

In order to embed Grasp workbench you need to add the following script to your web page:

`<script type='text/javascript' src='http://www.grasp.io/js/grasp/embedded.js'></script>`

The script uses configuration variable which must be defined before the script tag. This variable must be named as `graspConfig`. It can contain the following configurtion attributes:

* `server` - GRASP server URL, which will be used for data download and synchronization.
* `onload` - name of the callback JavaScript function which will be executed when GRASP is ready for use.

Example:

```html
<script type="text/javascript">
	graspConfig = {
		server : "http://www.grasp.io",
		onload : function() {
			//TODO some staff
		}
	};
</script>
<script type="text/javascript"
	src="http://www.grasp.io/js/grasp/embedded.js"></script>
```

You also need to add an empty HTML DIV element to the page and assign it ID by which it will be referenced in the workbench loader configuration:

```html
<div id="MyGraspWorkbench"></div>
```

## Check if Grasp is Ready

During the above step a global `GRASP` object will be created in the window scope, so it can be checked in the next way:

```html
<script type="text/javascript">
    var _graspOnLoad = function() {
    	alert(GRASP ? "Grasp is loaded" : "Grasp is NOT loaded");
    }

	graspConfig = {
		server : "http://www.grasp.io",
		onload : _graspOnLoad
	};
</script>
```

## Initialize and Show Workbench

`GRASP` object has public method `openWorkbench()`. It takes one argument - configuration object, which can contain the following attributes:

* `id`: string, required - ID of this workbench instance.
* `placeHolder`: string, required - ID of an existing DOM node (DIV element) that will be used as a container for the workbench.
* `repository`: string, optional - GUID of the repository that you want to load into this workbench.
* `showExplorer`: boolean, optional, default is `true` - whether to show workbench explorer or just the editor.
* `model`: string, optional - which model to open automatically when workbench is loaded (you can also do it programmatically via methods of the `Grasp.Workbench` class.

Full example:

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Grasp embedded test</title>
<script type="text/javascript">
	var _graspOnLoad = function() {
		GRASP.openWorkbench({
			id : "firstWorkbench",
			placeHolder : "graspWorkbenchContainer",
			repository : "publicExamples",
			showExplorer : false
		});
	}

	graspConfig = {
		server : "http://www.grasp.io",
		onload : _graspOnLoad
	};
</script>
<script type="text/javascript"
	src="http://www.grasp.io/js/grasp/embedded.js"></script>
</head>
<body>
	<div id="graspWorkbenchContainer" style="width: 1600px;"></div>
</body>

</html>
```
