Nodes are the basis of the godot engine along scenes, but scenes are nodes that contain other nodes like a parent-child like behavior
# Node System in GODOT

+ It's a super dupper tool that helps you in having a good project structure by default
  + This means that without knowing and only doing godot makes you learn good practices by having this tree like project structure of nodes
  + Cause a scene is made of scenes, scenes are made of nodes, nodes are made of nodes and etc.
+ This made something called the RESPONSIBILITY SYSTEM
  + This is a POO term coined by the single responsibility principle(more on that on the Software-engineering/Design_Patterns section of the notes)
## CharacterBodyXD
## SpriteXD
First add an Sprite node (2D or 3D):
- Then into the texture we add the first sprite or frame or an image to actually render into the game
## AnimationPlayer
### Animate a Sprite
Click on the animation button and add new animation with a name.
Then let us explore the AnimationPlayerSections and what to configure for this tool to work for us.
![[AnimationPlayer.png]]

Here first we need to create a track let us click the + icon next to the filet tracks search bar:
- A track is basically a tool that would let us change something of our main node -> The one that is our parent
- To animate sprite we need to select the property track option
## CharacterBody3D
It is a node that add physics functionality to the node attached to it and it gives some programmable properties that we can use with our scripting.