## UnityPlatforms
A simple and complex easy to use configuration for setting up all types of platforms! from moving, to rotating, this is the package you'll need!
<br><br>
# Documentation(PRE-V4):
PRE-V4 MPC Docs


Add the <code>PlayerPlatformDetector.cs</code> to the <code>GameObject</code> with the PlayerController on it! (Rigidbody not yet fully-supported!)

If this is not added properly, the character will not stick to the platforms!


All platforms must be defined with the <code>Platform</code> tag. Make sure its the <code>GameObject</code> that has the Collider & The <code>MovingPlatform.cs</code> script attached to it.

Platform ID Docs {

All reverse & Forwards points are set by using the platforms ID and creating a tag, like this:

<code>ExampleMovingPlatformID_REVERSE</code>

<code>ExampleMovingPlatformID_FORWARDS</code>

These tags must be applied to a start and stop point mesh renderer (or trigger) gameObject, as is doen in the example platforms prefab.
if the points are incorrectly applied, then the platform will glitch through the reverse/forwards object, 
or if its using TriggerMode, go right through it.
}


Documentation:

MP = Moving Platform,
RP = Rotating Platform
MPC = Moving Platform Controller (MovingPlatform.cs)
PCS - Platform Controller Script (PlatformController.cs)
| = or

PlatformController.cs {

Update (bool) - This updates the platforms options LIVE, if running in unity.
This setting only applies to Platform type MP.

Rotating Platforms (List) -
This is where you add all types of rotating platforms.
any object added, will rotate.

Rotating Platforms (List), Element 0+ (options, class) {

    Rotating Platform (GameObject) - The gameObject to rotate
    Rotate Switch (bool) - Switches the direction of the RP
    Local Rotation Speed (float, Range[0.0001 - 0.5]) - Local rotation speed of the RP
    ID (int) - The ID of the RP, mainly used for interacting with a certain RP from a script
}

Moving Platforms (List) -
This is where you add all types of Moving Platforms.
any added object, will move.

Moving Platforms (List), Element 0+ (options, class) {

    Moving Platform (GameObject) - The gameObject to move
    Delay Ammount (float) - Ammount of delay to Switch Directions when the platform hits a forwards/reverse point.
    Local Platform Moving Speed (float, Range[0.001 - 0.3]) - Local speed of the MP
    UsingTrigger (bool) - defines whether or not the reverse/forward points are triggers, or collidable objects. (false = collider, true = trigger)
    X (bool) - Moves the platform on the X Axis if true. Can be combined with Y Axis
    Y (bool) - Moves the platform on the Y Axis if true. Can be combined with X | Z Axis
    Z (bool) - Moves the platform on the Z Axis if true. Can be combined with Y Axis
    Direction Switch (bool) - switches the direction of the platform, useful if merging X | Z W/ Y
}
}

MovingPlatform.cs {

    Forwards (bool) - True if the Moving Platform is moving forwards
    Reverse (bool) - True if the Moving Platform is moving in reverse
    Moving Platform ID (string) - Refer to Line 11 of this Documentation
}


Global Functions/Methods (Developer Stuff) {

To use global methods for Platforms please add 
"using Platforms" to your script.


Legend:
CLASS.METHOD( PARAMETERS ) ( RETURN TYPE ) get; set; - DEFINITION

RetreivePlatformsLength{

RetreivePlatformsLength.MP() (int) get; - Returns all MPS length
RetreivePlatformsLength.RP() (int)  get; - Returns all RPs length
RetreivePlatformsLength.All() (Array) get; - Returns all platforms lengths in scene

}

RotationSpeed {

    RotationSpeed.SetGlobal(float speed) (void) set; - Set the global rotation speed for all RPs
    RotationSpeed.SetLocal(float speed, string ID) (void) set; - Sets the local rotation speed of a RP via ID
    RotationSpeed.GetLocal(string ID) (float) get; - Gets the local rotation speed of a RP via ID

}

MovementSpeed {

    MovementSpeed.SetGlobal(float speed) (void) set; - Set the global movement speed for all MPs
    MovementSpeed.SetLocal(float speed, string ID) (void) set; - Sets the local movement speed via ID
    MovementSpeed.GetLocal(string ID) (float) get; - Gets the local movement speed via ID

}

GetPlatform {

    GetPlatform.MovingPlatformGameObject(string ID) (GameObject) get; - Get a moving platforms gameObject
    GetPlatform.RotatingPlatformGameObject(string ID) (GameObject) get; - Get a rotating platforms gameObject
    GetPlatform.Exists(string ID, int method) (bool) get; - check if a certain platform exists via ID

}
!MORE SOON!
}
