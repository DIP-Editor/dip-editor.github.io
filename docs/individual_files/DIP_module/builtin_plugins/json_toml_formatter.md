<h1 align="center">json_toml_formatter.py</h1>

## What is the `json_toml_formatter` plugin?

The `json_toml_formatter` is a builtin plugin that will take the current tab, determine if the contents are a valid JSON or TOML file, and format the file accordingly allong with changing the syntax highlighting to match the file type if it is a blank file.

## How do I use the `json_toml_formatter` plugin?

The plugin is on by default so just leave it on or enable it from the ExtensionsManager (accessible from the `DIP` menu). If you want to disable it, simply disable it from the ExtensionsManager.

## File Documentation:

### Lines 1-18:

These lines are basic imports that call the `tkinter` module, the `json` module, the `toml` module, and the for items in the `DIP_module` folder.

Code:
```python
"""Automatically formats JSON and TOML files with the Contmand-Shift-F keybind"""

from __future__ import annotations

from json import dump
from json import dumps as json_dumps
from json import loads as json_loads
from json.decoder import JSONDecodeError

from __main__ import DIP, MainApp
from toml import dumps as toml_dumps
from toml import loads as toml_loads
from toml.decoder import TomlDecodeError

from DIP_module.folder_path import keybind_location
from DIP_module.settings import get_file_settings
from DIP_module.statusbar import BarItem
from DIP_module.tab import Tab
```

### Lines 21-49:

Lines 21-23 are quite generic by creating the `Extension` class and initializing it with the `MainApp` class. It also names the variables `version` and `author` in the `Extension` class for the `ExtensionManager` to use.

Lines 25-49 contain the `__init__()` method of the extension. It creates the variables `master` and `mainapp` along with `bi` (abbreviation of `BarItem`, the object used to add items to the statusbar). It also updates the keybinds file to have its own keybind ("Contmand-Shift-F"). It then binds the keybind to the `format_json_toml()` method. Finally, it adds the `bi` object to the statusbar.


Code:
```python
class Extension:
    version = "1.0.0"
    author = "Moosems"

    def __init__(self, master: DIP) -> None:
        # Set master and mainapp
        self.master: DIP = master
        self.mainapp: MainApp = self.master.master

        # Add keybind to keybinds.json
        with open(keybind_location, "r+") as f:
            keybinds: dict = json_loads(str(f.read()))
            # Override "<Contmand-Shift-F>" if it exists
            keybinds["<Contmand-Shift-F>"] = "<<json_toml_formatter>>"
            f.seek(0)
            dump(keybinds, f, indent=4)

        # Bind to json_toml_formatter
        self.mainapp.bind("<<json_toml_formatter>>", self.format_json_toml)

        # Add to statusbar
        self.bi = BarItem(
            self.master.statusbar,
            "JSON/TOML Formatter",
            self.master.statusbar.find_open_spot(),
            "Formats valid JSON or TOML in the current tab",
            click_command=self.format_json_toml,
        )
        self.master.statusbar.add_item(self.bi)
```

### Lines 51-55:

Lines 51-75 contain the `turn_off()` method, another required method for extensions. The `turn_off()` method should make the extension class go inactive and never run anything again. The method is called from the ExtensionManager to turn off the extension. It unbinds the keybind, removes the `bi` object from the statusbar, and destroys the `bi` object. Note that there is no `turn_on()` method as instead of reactivating the extension, the ExtensionManager will simply create a new instance of the extension class.

Code:
```python
    def turn_off(self) -> None:
        """Called when an extension is turned off"""
        self.mainapp.unbind("<<json_toml_formatter>>")
        self.master.statusbar.remove_item(self.bi)
        self.bi.destroy()
```

## Lines 57-105:

The last method in the `json_toml_formatter.py` file is the `format_json_toml()` method that can be called from the statusbar and the keybind. It gets the current tab, gets the text from the tab, and determines if the file is JSON or TOML. If it is neither, it returns. If it is JSON or TOML, it formats the text accordingly and sets the text in the tab. Finally, it sets the cursor position to 1.0 and sets the highlighter to the proper language.

Code:
```python
    def format_json_toml(self, *_) -> None:
        """Formats the JSON or TOML file"""

        del _

        # Get tab
        tab: Tab = self.master.tabs[0]
        # Get the current text
        text: str = tab.editor.get("1.0", "end-1c")
        # Determine if it is JSON or TOML
        language: str = tab.language
        # Check that it is JSON or TOML
        if language not in ["json", "toml", "text"]:
            return

        # Ensure the file is valid
        try:
            json_loads(text)
            if language == "text":
                language = "json"
        except JSONDecodeError:
            try:
                toml_loads(text)
                if language == "text":
                    language = "toml"
            except TomlDecodeError:
                tab.editor.focus()
                tab.editor.mark_set("insert", "1.0")
                tab.editor.see("1.0")
                return

        # Format the text
        if language == "json":
            json_settings = get_file_settings(tab.path)
            text = json_dumps(json_loads(text), indent=json_settings["indent_size"])
        elif language == "toml":
            text = toml_dumps(toml_loads(text))

        # Set the text
        tab.editor.delete("1.0", "end")
        tab.editor.insert("1.0", text)

        # Set cursor position to 1.0
        tab.editor.focus()
        tab.editor.mark_set("insert", "1.0")
        tab.editor.see("1.0")

        # Set the highlighter to the proper language
        self.master.change_tab_lex(language)
```

## [Next: [`hidden_char_finder.py`](json_toml_formatter.md)] | [Previous: [`builtin_plugins`](overview.md)] | [Back to Main Page](../../../overview.md)
