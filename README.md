# The Ignite.Key class provides several functions such as Pressed, which checks whether a key is pressed or not, Send, which allows you to send keys and strings, and finally the Hotkey class, which enables you to set a hotkey with a specific action.

**To call the ```Pressed``` function, you can use:**

```cs
Console.WriteLine (Ignite.Key.Pressed (1)); // true if button (Left mouse) is pressed or not
// You can use the predefined keys in the Keys class
Console.WriteLine (Ignite.Key.Pressed (Key.Mouse.LEFT)); // does the same as the example above
```

**To call the ```Send``` function, you can use:**

```cs
Ignite.Key.Send (Key.ENTER); // Sends the Enter key to the active application

// To send a string, you can simply use:

Ignite.Key.Send ("Hello World!"); // This works for every valid string
```

**To call the ```Hotkey``` class, you can use:**

```cs
var hotkey = new Ignite.Key.Hotkey (
    () => Console.WriteLine ("F12 was pressed"),
    Ignite.Key.F12); // If F12 is now pressed, the action will invoke

// You can use multiple keys that have to be pressed

var hotkey2 = new Ignite.Key.Hotkey (
    () => Console.WriteLine ("F11 and F12 were pressed",
    Ignite.Key.F11, Ignite.Key.F12)); // So now if F11 and F12 are being pressed, the action will invoke
```

**You can add a mode if you want a specific behavior. The following modes are supported:**
| Mode    |  Explanation                                                                            |
|---------|-----------------------------------------------------------------------------------------|
| Down    | The moment the button is pressed, the action will invoke - this is the default behavior |
| Up      | The moment the button is released, the action will invoke                               |
| Pressed | As long as the button is pressed, the action will invoke                                |

**You can call the Hotkey class with these modes the following way:**
```cs
var hotkey = new Ignite.Key.Hotkey (
    () => Console.WriteLine ("F12 was pressed and released"),
    Ignite.Key.Hotkey.Mode.Up,
    Ignite.Key.F12); // Of course, you can also add multiple Keys like before
```

**Lastly, to unsubscribe a hotkey, you can call the ```Unsubscribe``` function:**

```cs
var hotkey = new Ignite.Key.Hotkey (
    () => Console.WriteLine ("F12 was pressed"),
    Ignite.Key.F12);

DoSomeStuff();

hotkey.Unsubscribe();
```