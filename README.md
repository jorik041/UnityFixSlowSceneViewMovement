# UnityFixSlowSceneViewMovement
If the scene camera keeps moving after you released all keyboard keys, this is a fix for you. In fact, it is a fix for everybody as this also makes Unity run faster when moving in the scene.

```
When pressing a keyboard key the operative system repeats the key press many times.
Unity decides to queue all of those repeated key presses when moving in the scene view and generates several "slow" events
that trigger OnGUI Repaints and more. So many events that the queue keeps growing if the computer can't process all of them
fast enough, to the point of keep moving after long after the keys have been released.

Events that get queued until all of them are performed. If your computer is not fast enough, it means that the editor will keep
on executing those key presses long after you stopped touching the keyboard.

This scripts changes the Windows settings of the keyboard, slowing down as much as it can the settings of key press repeat speed,
while moving on the scene. Then restores the previous settings.
```

### How to use?
Copy paste the contents of the folder `FixSlowSceneViewMovement` anywhere you want inside the Assets folder of your Unity project

### Limitations
Only works for Windows users. It should work on Unity 2017, 2018 and 2019.

### I don't know what problem are you talking about
Add this script to any gameobject in your scene and try to move around. Be sure to move the mouse while pressing wasd for some time. You should go flying into space
```cs
// Make the editor slow by simulating something costly being executed.
using System.Threading;
using UnityEngine;

[ExecuteInEditMode]
public class MakeUnitySlow : MonoBehaviour {
    public int milliseconds = 100;
    void Update() {
        Thread.Sleep(milliseconds);
    }
}
```
Now follow the `How to use` step described before and, without doing anything else, try again. The editor will keep being slow, but you won't end up in orbit anymore.
