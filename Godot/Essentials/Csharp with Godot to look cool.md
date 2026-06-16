These programming notes assume you have some basic programming knowledge and some knowledge on the specifics of how C# works.
## Basics on the godot override functions steps and other basics programming stuff
Attach an script to a node
And you will see this:
```c#
using Godot;

using System;

public partial class Player : CharacterBody3D
{
}
```
We have the import statement of the Godot library to use the GodotAPI this enables the classes that we inherit from to use godot stuff 
### PhysicsProcess
We don't add or pass the delta as a parameter to other physics engaging functions since, in the PhysicsProcess apply it by itself when running, so that the physics actually behave correctly even with different frame-rates (We might need to tweak this at a later date).
```c#
public override void _PhysicsProcess(double delta)
{
	base._PhysicsProcess(delta);
}
``` 
It is an overridable method from the [CharacterBody3D](NodeSystem#CharacterBody3D) Node to add well physics to a node
Here we can add velocity or modify the Velocity property that is defined by the [CharacterBody3D](NodeSystem#CharacterBody3D) Node and we can move our character with the MoveAndSlide method also provided by the previously mentioned node.
```c#
public override void _PhysicsProcess(double delta)
{
	Velocity = new();
	// If we don't multiply it our character will move really slow since the direction values go from -1 to 1
	Velocity *= 5;
	// It will move the player with the physics engine
	MoveAndSlide();
}
``` 

### Input
An overridable method that help us handle input from the system our game runs and it is connected to the input mapping system in godot.
It tracks whenever a key is pressed or released.
```c#
public override void _Input(InputEvent @event)
{
	Input.GetVector("MoveLeft", "MoveRight", "MoveBackward", "MoveForward");
}
```
### Ready

### Exporting Attributes
When adding this type of attribute remember to rebuild your project and assign the value to whatever nodes needed or you are gonna have bugs.
It uses a decorator keyword `[Export]` to make a member attribute available to the engine inspector. The export makes it that we can access our attributes like this
![[ExportAttr.png]]
This gives us a visual cue on what to add or what to assign to an attribute in this case it is to manage animations and sprites from a player controller scene
You can also group them with the `[ExportGroup("Name")]` decorator to have a better organized inspector.
```c#
public partial class Player : CharacterBody3D
{
	[ExportGroup("Required Nodes")]
	[Export] private AnimationPlayer animationPlayerNode;
	[Export] private Sprite3D sprite3DNode;
```
