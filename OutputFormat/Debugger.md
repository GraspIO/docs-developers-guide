# Debugger

Generator debugger was already briefly mentiond in the Users Guide.

As a reminder, the Result view provides ability to generate some text from a model by using one the the output formats developed for its grammar. With it you can add breakpoints to the model and/or run generator in a step-by-step mode.

Once the output is generated, you can click on any place in it and this will highlight corresponding model's element that was a source of this text. And vice versa, you can select any element in the model and it will highlight the output generated from it.

Here is an example of what the editor with the output debugger open looks like:

![Debugger](img/Debugger.png)

And here is one possible sequence actions that could lead to this state:

1. A breakpoint was set by selecting model's element and clicking on the 'Add/remove breakpoint' button in debugger's toolbar (the hand on the right side) .
2. Desired output format ('EBNF') was selected from the dropdown that opens when clicking on the "eye" button in the result view.
3. Output generation started by clicking on the 'Run' button in debugger's toolbar (the triangle on the left side).
4. Generator ran, produced some output and stopped at the breakpoint.

As you can see from the screenshot, the output from the sub-elements that have not been visited yet is shown with yellow question marks. As you step into them by clicking on the second button from the left you will see how those placeholders get replaced with generated text and new placeholders appear inside of it, until all generation is done. This is often helpful for understanding why given model and format have produced an output that you see on the screen.

Instead of setting a breakpoint and clicking on 'Run' button, you can start generation by clicking on the 'Step into' button. This is equivalent to setting a breakpoint on the very first top-level element in the model.
