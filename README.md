# **TECH ARCH DAY - XR**

## Prerequisites
* You need a Laptop with a webcam for the exercises.
* Install unity https://unity3d.com/ 
    * When installing Unity select _Vuforia Augmented Reality Support_ from the available install packages in the installer.
    * You can install the monodevelop editor or use a code editor of your choice
* Clone repository https://github.com/Hippakaveri/tad-xr-handson.git that contains all assets and instructions needed for the session
    * If you're unable to clone it, you can also just download the zip from    https://github.com/Hippakaveri/tad-xr-handson
* We suggest bringing a mouse to the session because using the Unity editor with a trackpad can be difficult.

## Exercise 1 - Setting up the project

1. Open Unity and create a new project.
2. Save your scene once it has opened (File>Save Scene). Keep saving your progress often.
3. Delete the Main Camera (if there is one) from the scene and add an AR Camera from _GameObject>Vuforia>AR Camera_.
    * At this point Unity should download packages needed for vuforia development
4. Add an ImageTarget from _GameObject>Vuforia>Image_.
5. Add a cube to the scene from _GameObject>3D Object>Cube_.
6. Drag the created cube to the ImageTarget in the Hierarchy panel, to make it a child of the ImageTarget.
7. Select the cube in the Hierachy pane and you should see its information on the right in the Inspector pane. Change the position to (0,0,0) and scale to (1,1,1)
8. Go to _Edit>Project Settings>Player_. Under _XR Settings_ check the box for _Vuforia augmented reality support_.
9. Press the play button and test your application. You should see your webcam feed and when you show the printed out image to the camera, the cube you created should appear on top of it.
10. Try adding different shapes from _Gameobject>3D Object_ and repeating steps 6 and 7. You can try modifying the position, rotation and scale to get more familiar with the editor.

## Exercise 2 - Creating the game
##### 1. Import assets
   * Open the unity package file provided in the repository. An import pop-up should appear in unity. Click _All_ and then _Import_ to import the contents to your project.
   * Alternatively you can import the package from unity. Go to _Assets>Import Package>Custom Package_ and choose the provided package.

##### 2. Place Assets
* In the Unity editor, navigate to _Assets/Prefabs_ and drag the Maze prefab into the scene. Place the Maze inside the Image Target in the hierarchy. Make sure the position is _(0, 0.1, 0)_.
* From the same _Prefabs_ folder, drag the Ball prefab into the scene. Set it as a child of the Image Target and position it inside the maze on the outer edge. Make sure the ball is not touching any part of the maze.
* You can test your game now, but the game will probably not work as expected. We will fix this in step 3.


##### 3. Modify and test 
*By default Vudoria rotates the camera around the game world. for our purposes we need to move the game world instead. To change this select the AR Camera from the Unity scene. In the inspector under _Vuforia Behaviour (script)_ change the _World Center Mode_ to _DEVICE_.
* Vuforia disables colliders when tracking is lost. This makes the ball fall off the playfield easily. To disable this behaviour open _DefaultTrackableEventHandler.cs_ from _Assets/Vuforia/Scripts_ and comment out lines 101-102 & 106-112.
* The maze model and ball are very small in unity scale and with the default physics setting the ball might go through the colliders in the maze. To alleviate this go to _Edit>Project Settings>Physics_ and change the value of _Default contact offset_ to 0.01 or smaller.
* Press play to test you game. Try to get to the center of the maze!
* Congratulations, you have made an AR Game.

##### 4. Customise
* You can try modifying the position, rotation and scale of the assets to modify the game.
* You can alsso add more balls, change/modify materials or whatever you can come up with. 
