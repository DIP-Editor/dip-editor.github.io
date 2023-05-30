
<h1 align="center">DIP</h1>

<div align="center">
    <img src="./DIP_module/static/DIP.png"></img>
</div>

## Description (What it should be like when released)

`DIP` is a code editor designed for efficient programming in the fast-paced world of software development. Unlike other code editors, `DIP` is lightweight, low on CPU consumption, and has a minimal RAM footprint. Its design allows for easy development of extensions and integrates built-in git support, providing the ability to commit, pull, switch branches, and open GitHub or GitLab for pull requests. With a `.json` styling file, a `.toml` language support file, and `.json` highlighting file, the user has complete control over the application's appearance, and how many languages the editor will support. Not only will it support many languages natively but it will help you as you code by providing an autocomplete menu while typing. `DIP` also features an integrated terminal for running files and using command-line tools and compiler/interpreter functionality, allowing the user to run a file with the click of a button. When idle, `DIP` consumes less RAM and takes less storage space than VS Code, making it the ideal code editor for efficient programming. With `DIP`, programming can now be as fast-paced as the world around it.

## Documentation

 1. [Overview](./docs/overview.md)
 2. [Installation](./docs/installation.md)
 3. [Using `DIP`](./docs/use-dip.md)
 4. [Editing Themes](./docs/edit-themes.md)
 5. [Modifying Languages](./docs/modifying-languages.md)
 6. [Extensions/Plugins](./docs/extensions.md)
 7. [Keyboard Shortcuts](./docs/keyboard-shortcuts.md)
 8. [Request a Feature](./docs/feature-request.md)
 9. [License](./LISCENSE)
 10. [Contributing](./docs/contributing.md)

To get started, read the [overview](./docs/overview.md) and follow the guide.

## `DIP` Troubleshooting

If you are having trouble with `DIP`, please open an issue on the `DIP` repository. These issues need to be as detailed as possible and, if possible, an MRE (minimum reproducible example) is appreciated. An MRE is a piece of code that reproduces the issue with as little code as possible while being as easy to read as possible. MRE's help devs figure out what causes the issue and provides a testing space to see how the issue can be fixed. More info can be found on Wikipedia [here](https://en.wikipedia.org/wiki/Minimal_reproducible_example). An example of an MRE that was used for fixing bugs when making all widgets use ttk themes is as follows:

```python
from tkinter import Text, Tk
from tkinter.ttk import Style

from tklinenums import TkLineNumbers


class App(Tk):
    def __init__(self):
        Tk.__init__(self)
        self.style = Style()
        self.style.theme_create("TestTheme", parent="clam", settings={})
        # Fix (part 1):
        self.style.theme_use("TestTheme")
        # Cannot be used in reload()
        self.reload()
        self.text = TTKText(self, self.style)
        self.text.pack(side="right", fill="both", expand=True)
        self.linenumbers = TkLineNumbers(self, self.text, width=30)
        self.linenumbers.pack(side="left", fill="y")
        self.mainloop()

    def reload(self):
        self.style.configure("Font.NormalFont.TText", font=("Courier New bold", 15))
        # self.style.configure("TLinenumbers", foreground="red", background="blue")
        # Fix (part 2):
        self.style.theme_settings("TestTheme", settings={"TLineNumbers": {"configure": {"background": "red", "foreground": "blue"}}})
        # Must use theme_settings() to set TLineNumbers

class TTKText(Text):
    def __init__(self, master: Tk, style_instance: Style, *args, **kwargs):
        self.style_instance = style_instance
        Text.__init__(
            self,
            master,
            font=self.style_instance.lookup("Font.NormalFont.TText", "font"),
            *args,
            **kwargs,
        )

app = App()
```

# End Goal:
```
_____________________________________________________
| C | p |                TabSystem              | A |
| o | r |---------------------------------------| n |
| m | o |                                  | M  | n |
| m | j |                                  | i  | o |
| m | e |               Editor             | n  | u |
| m | c |                                  | i  | n |
| a | t |                                  | m  | c |
| n | s |                                  | a  | e |
| d |   |                                  | p  | m |
| s | b |                                  |    | e |
|   | a |---------------------------------------| n |
| b | r |                 Terminal              | t |
| a |   |                                       | s |
| r |   |                                       |   |
_________________________________________________   |
| Status Bar                                    |   |
_____________________________________________________
```
