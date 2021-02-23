# Unity UI Handler

UI handling system for Unity. Allows for an easy screen stacking architecture. Takes into account Game Object activation/deactivation to properly dispatch coroutines.

Usage example:

```csharp
public class HUD: UILayer
{
    public override void OnScreenInitialize()
    {
        print("HUD Initialized");
    }
    
    public override void OnScreenUp()
    {
        print("Showing HUD");
    }
}


public class GameManager: MonoBehaviour
{
    //Assigned from the inspector. Usually attached to the canvas,
    //but there can also be multiple of these to handle different branches of the UI if necessary
    public UIHandler gameUI;

    private void Start()
    {
        gameUI.Initialize(); 
        //Outputs "HUD Initialized" as long as the HUD component is a child
        //from the UIHandler Game Object hierarchy
        
        gameUI.Show<HUD>(); //Outputs "Showing HUD"
    }
}
```
