<a name="Title" />
# "Z is for Zombie" - Construct 2 - Demo Snippets #

---


##Pre-Requisites##

To follow the steps in the demo below, you will need the following: 

- Scirra's Construct 2 r149 or later. You can view the list of the [latest releases](https://www.scirra.com/construct2/releases) or downlod [r149](https://www.scirra.com/construct2/releases/r149) directly.  
- The latest version of these demo files from http://github.com/BretStateham/ZisForZombie

---

##Steps##

###Basic Demo###

 - [Create the Game Project](#CreateGame)
 - [Setup the Game Layers](#SetupTheGameLayers)
 - [Add the Standing "Z" To the Game](#AddStandingZ)
 - [Add the "Platform" and "Scroll To" Behaviors](#AddPlatformAndScrollToBehavior)
 - [Add Platforms](#AddPlatforms)
 - [Add Zombie Animations](#AddZombieAnimations)
 - [Add Zombie Movement Events](#AddZombieMovementEvents)
 - [Add the Enemy](#AddEnemy)
 - [Check for Zombie and Enemy Collisions](#CheckForZombieEnemyCollisions)
 - [Add Brians for the Zombie to Collect](#AddBrains)
 - [Add Background](#AddBackground)

<!-- ======================================================================= -->
<a name="CreateGame" />
### Create the Game Project ###
<!-- ======================================================================= -->
---

Create a new Windows 8 game in Construct 2

- Start **Construct 2**

- Create a **"New Windows 8 Project"**.  From the ribbon bar, click **"File"** | **"New"**, select **"New Windows 8 Project"**, then click **"Open"**

- In the **Projects** Bar, ensure that the new project is selected:

	![01NewProjectInProjectBar](images/01newprojectinprojectbar.png?raw=true "New Project in Project Bar")

- In the **Properties** Panel, change (leave all others at default):
	- **Name:** ZisForZombie
	- **Description:** Zombie Game
	- **Author:**  Your Name
	- **Window Size:** 1366x768

	![01NewProjectProperties](images/01newprojectproperties.png?raw=true "New Project Properites")

- In the **Projects** Panel, expand **ZisForZombie**
	- Rename **"Layouts"** | **"Layout 1"**, **"Game Layout"**
	- Rename **"Events"** | **"Event sheet 1"**, **"Game Events"**

	![02RenamedLayoutAndEvents](images/02renamedlayoutandevents.png?raw=true "Renamed Layout and Events")

- On the Layout designer, note the default **Share** and **Purchase** buttons, but then delete all the contents on the designer

	![03DeleteDefaultObjects](images/03deletedefaultobjects.png?raw=true "Delete Default Objects")

- Zoom out to show the entire designer surface

- On the design surface, Show that the Window Size (dotted line) is different thant the Layout size (white box)

	![04WindowsSizevsLayoutSize](images/04windowssizevslayoutsize.png?raw=true "Window Size vs Layout Size")

- Select **"Projects"** | **"Layouts"** | **"Game Layout"**.  In the **"Properties"** panel, change the **"Layout Size"** to: **2732,768**

	![05WideLayout](images/05widelayout.png?raw=true "Wide Layout")
 
	> **Note:** Thatis (1366x2)x728, or twice the width of the window.  


- From menu bar, select **"File"** | **"Save As Single File..."**.  Save the file as **"ZisForZombie.capx"** in the directory of your choice.  

	> **Note:** **.capx** files are basically **.zip** files that contain the entire projects assets.  They make it easy to share your project with others. For large projects, they can be slow, so using **"File"** | **"Save As Project..."** may be a better choice in that case. 



<!-- ======================================================================= -->
<a name="SetupTheGameLayers" />
### Setup the Game Layers ###
<!-- ======================================================================= -->
---

Setup the layers in the Game Layout

- With the **"Game Layout"** tab selected in the designer, switch to the **"Layers"** tab. 
- Select **"Layer 0"** and rename it to **"Background"**

	![06RenameLayer0ToBackground](images/06renamelayer0tobackground.png?raw=true "Rename Layer 0 to Background")

- Then in the **"Layers"** panel, click the **"+"** button at the top to add a new layer.
- Name the new layer **"Game"**

	![07AddGameLayer](images/07addgamelayer.png?raw=true "Add Game Layer")

<!-- ======================================================================= -->
<a name="AddStandingZ" />
### Add the Standing "Z" To the Game ###
<!-- ======================================================================= -->
---

We will start adding our hero, "Z" to the game.  He has multiple states (standing, walking, jumping, falling).  We'll start by adding him with the single "Standing" animation.  

- On the design surface, make sure you are on the **"Game Layout"** tab
- In the **"Layers"** panel, make sure the **"Game"** layer is selected.
- Right click on the layout in the designer, and select **"Insert new object"**

	![08InsertNewObject](images/08insertnewobject.png?raw=true "Insert New Object")

- Review the different types of objects that can be added.  
- Select the **"Sprite"** object type, set the name to **"Zombie"**, and click **"Insert"**

	![09InsertZombieSprite](images/09insertzombiesprite.png?raw=true "Insert Zombie Sprite")

- **Move the cross-hairs with the mouse** to place the center of the sprite over towards the **left edge of the layout**.
- The **sprite boundary** will appear on the layout, as will the **"Edit Image"**, **"Animations"**, and **"Animation frames"** windows.

	![10AnimationEditorWindows](images/10animationeditorwindows.png?raw=true "Animation Editor Windows")

- In the **"Animations"** window, rename the **"Default"** animation **"Standing"**

	![11RenameDefaultAnimationToStanding](images/11renamedefaultanimationtostanding.png?raw=true "Rename Default Animation to Standing")

- In the **"Animation frames"** window, right-click the white space, and select **"Import sprite strip..."** from the popup menu.

	![12ImportFromSpriteStrip](images/12importfromspritestrip.png?raw=true "Import From Sprite Strip")

- Navigate to the **"\Assets\Art\Z\Standing"** folder, select the **"StandingZombieNoOutline64.png"** file, and click **"Open"**

![13ImportZombieStandingSpriteStrip](images/13importzombiestandingspritestrip.png?raw=true "Import Zombie Standing Sprite Strip")

- In the **"Import sprite strip"** window, confirm the following and click *OK**:
	- **Number of horizontal cells**: 4
	- **Number of vertical cells**: 1 

	![14ConfirmStripSettings](images/14confirmstripsettings.png?raw=true "Confirm Strip Settings")

- In the **"Animation frames"** window, right click frame **0**, and choose **"Delete"** from the popup menu.

	![15DeleteFrome0](images/15deletefrome0.png?raw=true "Delete Frame 0")

- In the **"Edit image: Zombie (Standing, frame 0)"** Window, Hold down the **"Shift Key**" on the keyboard and click the **"Crop"** icon on the toolbar.  Holding the **"Shift Key"** down crops all frames at once, and trims the extra space off. 

	![16CropAnimationFrames](images/16cropanimationframes.png?raw=true "Crop Animation Frames")

- **Close** the **"Edit image: Zombie (Standing, frame 0"** window
- In the **"Animations"** window, select the **"Standing"** animation.
- In the **"Properites"** panel, set:
	- **"Speed:"** 5
	- **"Loop:"** Yes

	![17LoopStandingAnimation](images/17loopstandinganimation.png?raw=true "Loop Standing Animation")

- In the **"Animations"** window, **right-click** the **"Standing"** animation, and choose "Preview" from the popup menu to preview the animation.  Close the preview window when done.

	![18PreviewStandingAnimation](images/18previewstandinganimation.png?raw=true "Preview Standing Animation")

- From the **"Home"** ribbon along the top, click **"Run layout"** to run the game in the browser.  You may need to refresh the page in the browser to see the latest changes.

	![19RunLayout](images/19runlayout.png?raw=true "Run Layout")

- The game doesn't do anything right now.  Our Zombie just stands there and wobbles a little. Close the browser when you are done.  

	![20LayoutRunningInBrowser](images/20layoutrunninginbrowser.png?raw=true "Layout Running in Browser")

<!-- ======================================================================= -->
<a name="AddPlatformAndScrollToBehavior" />
### Add the Platform and Scroll To Behaviors ###
<!-- ======================================================================= -->
---

We need our Zombie to be able to move back and forth and jumpt to platforms (we havent' built any platforms yet though).  With Construct 2, that's easy to do using "Behaviors"

- With the **"Zombie"** sprite selected on the design surface, from the **"Properties"** panel, **click** the **"Behaviors"** link. 

	![21ZombieBehaviorsLink](images/21zombiebehaviorslink.png?raw=true "Zombie Behaviors Link")

- In the **"Zombie: Behaviors"** window click the **"+"** button along the top to add a new behavior

	![22AddBehavior](images/22addbehavior.png?raw=true "Add Behavior")

- In the **"Add behavior"** window, under the **"Movements"** header, select **"Platform"**, and click **"Add"**

	![23AddPlatformBehavior](images/23addplatformbehavior.png?raw=true "Add Platform Behavior")

- Again, In the **"Zombie: Behaviors"** window click the **"+"** button along the top
- This time, in the **"Add Behavior"** window, under the **"General"** header, pick **"Scroll To"** and click **"Add"**

	![24AddScrollToBehavior](images/24addscrolltobehavior.png?raw=true "Add Scroll To Behavior")

- Close the **"Zombie: Behaviors"** Window

	![25CloseBehaviorsWindow](images/25closebehaviorswindow.png?raw=true "Close Behaviors Window")

- In the **"Properties"** panel, expand **"Behaviors"** | **"Platform"**, and set:
	- **"Max Speed:"** 100
	- **"Jump Strength:"** 525
	- Leave all others at default.

	![26ZombiePlatformSettings](images/26zombieplatformsettings.png?raw=true "Zombie Platofrm Settings")

- From the **"Home"** ribbon along the top, click **"Run layout"** to run the game in the browser.  You may need to refresh the page in the browser to see the latest changes. 

	![27RunLayout](images/27runlayout.png?raw=true "Run Layout")
 
- **Notice that "Z" falls right off the screen**.  That is because we don't any any platforms for him to land on.  Close the browser when done.


<!-- ======================================================================= -->
<a name="AddPlatforms" />
### Add Platforms###
<!-- ======================================================================= -->
---

We need platforms for our Zombie to jump around on.  There are a number of platform blocks you can use in the game assets.  First, we'll set the layout grid to 16x16.

- **Right-click** the **"View"** ribbon tab, and **"de-select"** the **"Minimize the Ribbon"** option, to keep the ribbon bar visible. 

	![28TurnOffMinimizeRibbon](images/28turnoffminimizeribbon.png?raw=true "Turn Off Minimize Ribbon")

- Switch to the **"View"** ribbon.  Set the **"Grid Width"** and **"Grid Height"** both to **16**

	> **Note:**, the blocks and sprites we are using are all at sizes that are multiples of 16 (32x32,64x64).  The 16x16 grid size give us a conventient way to position items in the layout. 

	- Turn **ON** the **"Snap to grid"** checkbox.
	- Optionally turn **ON** the **"Show grid"** checkbox. 

	![29TurnOnGrid](images/29turnongrid.png?raw=true "Turn On Grid")

- Drag each of the **"Assets\Art\Blocks\Asphalt*.png"** images (**INDIVIDUALLY, NOT AS A GROUP**) into the design surface just to the left of the layout.  (off screen)

	![30DragBlockSprites](images/30dragblocksprites.png?raw=true "Drag Block Sprites")

- Each file will create a new sprite object and instance.
- Add the "Solid" behavior to each one (sorry, you need to do this one by one).

	![31AddSolidToBlock](images/31addsolidtoblock.png?raw=true "Add Solid Behavior to Blocks")

- Right click on the design surface and pick **"Insert new object"**.  
- In the **"Insert New Object"** window, select **"Tiled Background"**, set the name to **"GroundFill"** and click **"Insert"**, and use the cross hairs to place an instance to the left of the layout neard the block tiles. 

	![32AddGroundFill](images/32addgroundfill.png?raw=true "Add Ground Fill")

	- In the **"Edit image: GroundFill"** window, click the **"Resize"** button, and set the size to **32x32**

	![33SizeGroundFill](images/33sizegroundfill.png?raw=true "Size Ground Fill")

	- Click the **"Paint Bucket"** icon, **set the fill color** to **43,29,0,255** (**RGBA**), and fill the entire 32x32 image with the color. 

	![34SetGroundFillColor](images/34setgroundfillcolor.png?raw=true "Set Ground Fill Color")

	- Close the **"Edit image: GroundFill"** window.

- **Set the size of the GroundFill object to 32x32** by **selecting it on the designer**, then setting the size to **32,32** in the **Properties bar**

	![35SetGroundFillObjectSize](images/35setgroundfillobjectsize.png?raw=true "Set Ground Fill Object Size")

- Position platform blocks and ground fill to build a series of platforms.  You can easily copy existing blocks by holding down the CTRL key on the keyboard while you drag an existing block to a new location.  

	![36BlockLayout](images/36blocklayout.png?raw=true "Block Layout")


  - ***This can be time consuming***.  Just do a quick layout so you can test it.  There is a completed layout at **"Demo\End\02-AfterPlatformLayout-ZisForZombie.capx"**

- **Run the layout in the browser**. Use the left, right , up arrows to move Z.  Note that he doesn't walk.  Adjust platform distances, etc. as needed.  Close browser when done. 
    

<!-- ======================================================================= -->
<a name="AddZombieAnimations" />
### Add Zombie Animations ###
<!-- ======================================================================= -->
---

Add more animations to the Zombie

- On the design surface, double click on "Z" to open his animations. 
- In the **"Animations"** window, **right-click** and choose **"Add animation"**. 

	![37AddAnimation](images/37addanimation.png?raw=true "Add Animation")

- Name the new animation **"Walking"**, and make sure it is selected.

	![38WalkingAnimationSelected](images/38walkinganimationselected.png?raw=true "Walking Animation Selected")

- In the **"Animation frames"** window, right click and choose **"Import sprite strip..."**

	![12importfromspritestrip](images/12importfromspritestrip.png?raw=true "Import From Sprite Strip")

- Import the **"Assets\Art\Z\Walking\ZombieStompRightNoOutline64.png"** sprite strip. 

	![39ImportWalkkingAnimatoin](images/39importwalkkinganimatoin.png?raw=true "Import Walking Animation")
 
- Confirm the sprite strip settings, and click **OK**:
	- **Number of horizontal cells:** 4
	- **Number of vertical cells:** 1

	![40ConfirmSpriteStripSettings](images/40confirmspritestripsettings.png?raw=true "Confirm Sprite Strip Settings")

- **Delete frame 0**

	![41DeleteFrame0](images/41deleteframe0.png?raw=true "Delete Frame 0")

- **Shift-click** the **crop** button to crop the entire animation

	![42CropEntireImage](images/42cropentireimage.png?raw=true "Crop Entire Image")

- In the **"Properties"** panel for the **"Walking"** animation set:
	- **Speed:** 10
	- **Loop:** Yes

	![43SetWalkingProperites](images/43setwalkingproperites.png?raw=true "Set Walking Animation Properties")

- Add another new animation named **"Jumping"**
- In the **"Animation frames"** window, right-click and select **"Import Frames..."**.
- Import the single **"Assets\Art\Z\Jumping\JumpingZombieNoOutline64.png"** file.
- Delete Frame 0
- Click the "Crop" button to crop the image.

- Repeat the aboove two steps.  Create an animation called **"Falling"** and import the  **"Assets\Art\Z\Jumping\FallingZombieNoOutline64.png"** sprite. Be sure to delete frame 0 and crop the image.

- Close the **"Edit image.."** window

<!-- ======================================================================= -->
<a name="AddZombieMovementEvents" />
### Add Zombie Movement Events ###
<!-- ======================================================================= -->
---

So far we've done everything on the Layout page.  Now, we need to add some events to control which animation is showing for the Zombie based on his state.

- Open the **"Game Events"** page.  
- Notice that there are a number of events already there.  Those are there because twe used the **"New Windows 8 Project"** when we created our game.

	![44OriginalEvents](images/44originalevents.png?raw=true "Original Events")

- Select all of the existing events, and delete them.

	![45DeleteAllEvents](images/45deleteallevents.png?raw=true "Delete All Events")

- Click the **"Add event"** text at the end of the event list. In the "Add event" window

	![46ClickAddEvent](images/46clickaddevent.png?raw=true "Click Add Event")

- In the **Add event** window, click **Zombie** then click **Next**:

	![47SelectZombie](images/47selectzombie.png?raw=true "Select Zombie")

- Under the **"Platform"** heading, click **"Is moving"** then click **"Done"**

	![48IsMoving](images/48ismoving.png?raw=true "Select Is moving")

- **Right-click** the **"Zombie | Platform is moving"** event and select **"Invert"** to imply the condition is met with the Zombie is NOT moving. 

	![49InvertCondition](images/49invertcondition.png?raw=true "Invert Condition")

- Click the **"Add action"** link

	![50ClickAddAction](images/50clickaddaction.png?raw=true "Click Add Action")

- In the **"Add action"** window:
	- Select **"Zombie"** and click **"Next"**
	- Under the **"Animations"** header, click **"Set animation"** and click **"Next"**
- In the **"Parameters for Zombie: Set animation"** window, set:
	- **Animation:** "Standing" (include the quotes)
	- **From:** beginning
	- click **"Done"**
- **Right click** the **"Zombie | X Platform is moving"** event, select **"Add"** | **"Add 'Else' (X)"**
- Add an action to set the Zombie Animation to **"Walking"** (using the method above)

- Add a new event / action:
	- **Event Object:** Zombie
	- **Event Condition:** Platform Is Jumping
	- **Action Object:** Zombie
	- **Action:** Set Animation to "Jumping"

- Add a new event / action:
	- **Event Object:** Zombie
	- **Event Condition:** Platform Is Falling
	- **Action Object:** Zombie
	- **Action:** Set Animation to "Falling"

- Run the game in the browser to show the animations.  However, they only look right when the player is moving right.  Close the browser.

- Add a new event / action:
	- **Event Object:** Keyboard
	- **Event Condition:** On key pressed, Left Arrow
	- **Action Object:** Zombie
	- **Action:** **Set Mirrored** to "Mirrored"

- Add a new event / action:
	- **Event Object:** Keyboard
	- **Event Condition:** On key pressed, Right Arrow
	- **Action Object:** Zombie
	- **Action:** **Set Mirrored** to "Not Mirrored"
  

<!-- ======================================================================= -->
<a name="AddEnemy" />
### [Add the Enemy](#AddEnemy) ###
<!-- ======================================================================= -->
---

We need an enemy to avoid! We'll add that next

- On the **"Game Layout"**, insert a new sprite object named "Enemy"
- Import the animations from the **"\Assets\Art\Enemy\EnemyWalking64.png"** sprite strip: 
	- **Number of horizontal cells:** 
	- **Number of vertical cells:** 1
	- **Delete** frame **0**
	- **Crop** the entire image (**shift-click crop**)
	- Set the default animation speed to 10
	- Set the default animation to Loop

- Add the **"Platform"** behavior to it:
	- **Max Speed:** 100
	- **Default Controls:** No (keeps it from responding to the keyboard)

- We want the enemy to just pace back and forth.  We'll give it some objects to collide with that cause it to referse it's direction. 

- Right click the layout, and Insert a new sprite named "EnemyBoundary".  
	- Give the default frame a transparent yellowish fill (just so we can see it)
	- Set it's size to 32x32
	- Set it's **Initial Visibility** to **Invisible**
	- Position a couple of instances around your enemy(s) to where you want them to reverse direction

- **Select** one of the **Enemy** instances on the design surface.  In the **"Properties"** panel, click the **"Instance variables"** link 
- In the **"EnemyBoundary: Instance variables"** window, click the **"+"** button to add a new instance variable.
- Create a new variable with the following:
	- **Name:** Direction
	- **Type:** Text
	- **Initial value:** Left 
	- **Description:** Keeps track of the current direction of the enemy


- Add a new event / action:
	- **Event Object:** System
	- **Event Condition:** On start of layout
	- **Action Object:** Enemy
	- **Action:** Platform | Simulate Control | Left

- Add a new event :
	- **Event Object:** Enemy
	- **Event Condition:** On collision with EnemyBoundary

- Add a Sub Event:
	- **Event Object:** Enemy
	- **Event Condition:** Compare Instance Variable | Distance | = | "Left"
	- **Action Object:** Enemy
	- **Action:** Set Instance Variable | Distance | "Right"
	- **Action Object:** Enemy
	- **Action:** Set Mirrored | Mirrored

- Add and Else on the SubEvent
	- **Action Object:** Enemy
	- **Action:** Platform | Simulate Control | Left
	- **Action Object:** Enemy
	- **Action:** Set Mirrored | Not Mirrored

- Add a new event:
	- **Event Object:** System
	- **Event Condition:** For each Enemy
	- Add a Sub Event:
	- **Event Object:** Enemy
	- **Event Condition:** Compare Instance Variable | Distance | = | "Left"
	- **Action Object:** Enemy
	- **Action:** Platform | Simulate Control | Left
	- Add an else:
	- **Action Object:** Enemy
	- **Action:** Platform | Simulate Control | Right
  

<!-- ======================================================================= -->
<a name="CheckForZombieEnemyCollisions" />
### Check for Zombie and Enemy Collisions ###
<!-- ======================================================================= -->
---

Now, we want to check to see if Z collides with an enemy

- Import sounds **"\Assets\Sounds\Grunt\Grunt.wav"** and **"\Assets\Sounds\Dying\Dying.wav"**

- Modify the **"System"** | **"On Start of Layout"**
- Add an **Audio** | **Preload** | **Grunt**, and **Audio** | **Preload** | **Dying**

- Add a new event:
	- **Event Object:** Zombie
	- **Event Condition:** On collision with Enemy
	- Add a Sub Event:
	- **Event Object:** Zombie
	- **Event Condition:** Platform | Is Falling?
	- **Action Object:** Enemy
	- **Action:** Destroy
	- **Action Object:** Zombie
	- **Action:** Set Y Vector | -300
	- **Action Object:** Audio
	- **Action:** Play Grunt | Not Looping | Volume 0
  
- Add an else:
	- **Action Object:** Zombie
	- **Action:** Destroy
	- **Action Object:** Audio
	- **Action:** Play Dying | Not Looping | Volume 0


<!-- ======================================================================= -->
<a name="AddBrains" />
### Add Brians for the Zombie to Collect ###
<!-- ======================================================================= -->
---

We've got a hero ("Z") and some enemies.  Now let's add some Brains for "Z" to collect.  

- On the **Game Layout**, **Insert a new sprite object** name **"Brain"**:
	- Import from sprite strip: **"Assets\Art\Brains\BouncingBrain32.png"**
	- delete default frame 0
	- Crop entire image (**shift-click crop**)
	- Set speed to 5
	- Set looping to Yes

- Place multiple brains around the layout where Z has to jump to get them. 

- Import the "Brains" sound, and pre-load it
- Add an event to check for Zombie / Brain collisions
	- Destroy the brain
	- Play the Brains sound

<!-- ======================================================================= -->
<a name="AddBackground" />
### Add Background ###
<!-- ======================================================================= -->
---

Let's polish things up with a background graphic and sound

- With the **"Game Layout"** open in the designer, in the **"Layers"** panel, select the **"Background"** layer.  
- Drag the **"Assets\Art\Background\NightSkyBackground2049.png"** graphic onto the layout, and position it to the left edge of the layout. Notice that it doesn't fill up the entire width.  We're going to adjust the parallax so it scrolls slower than the rest.  
- Again, select the **"Background Layer"** and change the **"Parallax"** to **"50,0"**
- In the **"Layers"** Panel, click on the **"Lock"** icon next to the layer name to lock the layer. 
- Import the **"Assets\Sounds\Background Music\DungeonCrawl.wav"** sound
- Preload DungeonCrawl
- Add an action to the **System** | **On start of layout** to play it. 

