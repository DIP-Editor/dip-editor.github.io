<h1 align="center">Extensions/Plugins</h1>

## What are extensions/plugins in `DIP`?

In `DIP`, an extension is a piece of code imported that is allowed to do anythign it wishes over the app. As such, be careful when installing extensions. Extensions are installed in the `extensions` folder in the `DIP` directory (see [Editing Themes](./edit-themes.md)). The file structure of an extension is as follows:

```
DIP
├───extensions
│   └───example_extension_name
│       │   example_extension_name.py
│       │   example_extension_name.extra_file
...
```

In `DIP`, `example_extension_name.py` file is the main file of the extension. It must therefore also contain the `Extension` class.

## How do I create an extension?

To create an extension, start by creating the file structure shown above. Next, you must create the `example_extension_name.py` file. In this file, you must create the `Extension` class. An [example extension](../extensions/ExampleExtension/ExampleExtension.py) is as follows:

```python
"""Example extension (Docstring is for the extension manager)"""
from __future__ import annotations

from tkinter import Misc

from __main__ import DIP

# Move to the DIP internal folder to test and run extensions

"""
Necessary extension code:

 - Extension class
  - __init__ method
  - Extension.author and Extension.version attributes
  - turn_off() method
"""


class Extension:
    """Example extension"""
    version = "1.0.0"
    author = "Moosems"

    def __init__(self, master: DIP) -> None:
        self.master: DIP = master
        self.master.bind(
            "<<BackspaceHandlerStarting>>", self.backspace_handler_starting
        )
        self.master.bind("<<BackspaceHandlerEnding>>", self.backspace_handler_ending)

    def turn_off(self) -> None:
        self.master.unbind(
            "<<BackspaceHandlerStarting>>", self.backspace_handler_starting
        )
        self.master.unbind("<<BackspaceHandlerEnding>>", self.backspace_handler_ending)

    def backspace_handler_starting(self, event) -> None:
        textwidget: Misc = event.widget
        textwidget.insert("insert", "This is an extension insert")

    def backspace_handler_ending(self, event) -> None:
        textwidget: Misc = event.widget
        textwidget.insert("insert", "\nThis is also an extension insert ")
```

For the extension to run, it must have a few things:

 - The `Extension` class
  - The `__init__` method
  - The `Extension.author` and `Extension.version` attributes
  - The `turn_off()` method

Should one of these be missing, the extension might break. Something important to note about extensions is that, in the end, they have **_supreme_** power over the application. Anything the application does can be undone by an extension. This means that you should be careful when installing extensions. If you are unsure about an extension, please open an issue on the `DIP` repository or look at the code yourself.

## How do I install an extension?

To install an extension, simply move the extension folder into the `extensions` folder in the `DIP` directory (see [Editing Themes](./edit-themes.md)). The extension will then be loaded on the next startup of `DIP`. If you have already started `DIP`, you can use the `ExtensionsManager` to load the extension.

## How do I uninstall an extension?

To uninstall an extension, simply remove the extension folder from the `extensions` folder in the `DIP` directory (see [Editing Themes](./edit-themes.md)). The extension will then be unloaded on the next startup of `DIP`. This, however, will not stop the extension from running if it is already running. To stop the extension, you must use the `ExtensionsManager` to unload the extension.

## [Next: Request a Feature](./feature-request.md) | [Previous: Modifying Languages](./modifying-languages.md) | [Back to Overview](./overview.md)