# AIR.Sketch
A Sketch Framework for the Unity Editor.

## Description
AIR's sketch framework allows you to build and interactively run small code snippets (called "Sketches") in isolation, without needing to build them into a game or scene. Often, the best way to build new features are in isolation, and this framework facilitates that. Features built as sketches can be easily found, demonstrated and worked on, and much like tests, these sketches can then also serve as reference for certain feature working in isolation.

## Creating Sketches

### Prerequisites
For the Unity Editor to recognise sketches, they must satisfy two requirements:
1. The sketch class must exists inside of an assembly with a name ending in ".Sketches". eg `Example.Sketches.asmdef`.
2. The sketch class must have the `[SketchFixture]` attribute.

### Adding Descriptions
It is recommeneded that when creating a new sketch, you use the `[SketchDescription]` attribute on the class. Doing so provides developers more information about what the sketch is expected to demonstrate, and the text appears along with the test in in the sketch runner.

### Dependencies
The Sketch runner is coupled with [AIR.Flume](https://github.com/AnImaginedReality/Flume), which can provide sketches with dependency injection. If your sketch has a Dependency, add the `[SketchDependsOn(Type serviceType, Type serviceImplementation)]` attribute. By adding this attribute along with the given dependency type and implementation type, AIR.Sketch will create the necissary dependencies for your sketch to run. Note that dependencies don't have to be a sketch's direct dependency. A dependency will be injected for **any** object instantiated in the sketch.

## Sketch Runner
The sketch runner window can be found in the Unity Editor Window dropdown beside the test runner. To open the sketch runner, in the unity editor, navigate to:
```
Window > General > Sketch Runner
```
The sketch runner window will now appear, and list any/all valid sketches in your project, along with  names, descriptions, and run buttons for each. Feel free to dock it anywhere in your workspace.

<!-- 
TODO: Make editor tools for quickly making sketch assemblies.
TODO: Make shortcut (ctrl + shift + r) to re-run last sketch.
Sketch assemblies (unlike tests) may use many libraries in order to demonstrate their functions, and for this reason may have many assembly references.
-->
