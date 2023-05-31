<h1 align="center">Editing Themes</h1>

## How do `DIP` themes work?

`DIP` themes work as a one to one with the `tkinter.ttk.Style.theme_use()` (ttk) system. As such, the theme system uses dictionaries like this:
```json
"TScrollbar": {
    "configure": {
        "background": "#ffffff",
        "foreground": "#4f4c4d",
        "troughcolor": "#bbbbbb",
        "arrowcolor": "#4f4c4d",
        "darkcolor": "#ffffff",
        "arrowsize": 15,
        "bordercolor": "#4f4c4d"
    }
}
```
What makes this so amazing is that `DIP` uses JSON for it's theme system as well. This means that you can copy paste a ttk dictionary into a `DIP` theme file and it will work perfectly (provided there are no variables in the dictionary). This also means that you can copy paste a `DIP` theme file into a `tkinter.theme_use()` dictionary and it will work perfectly. The one extra neat feature of all this is the `tkinter.theme_use()` uses a `parent` theme argument. This means that you can have a `DIP` theme that is a child of another builtin `tkinter` theme. Though this is a required key in `DIP` (`DIP` requires certain keys in `master.json` and `highlight.json`), it can simply be set to `default` to use the default `tkinter` theme.

## How do I edit a theme?

Theme files (`master.json`) are kept in your OS's user data directory. These are as follows:
 - MacOS: `~/Library/Application Support/DIP/`.
 - Windows: `{UserProfile}\AppData\Local\DIP\` (not roaming) or `{UserProfile}\AppData\Roaming\DIP\` (roaming).
- Linux: `~/.local/share/DIP/`.

Once the file is located, simply open the file and start editing the ttk theme. To find all the possible values and what they do, check out the [Tcl/Tk documentation](https://www.tcl.tk/man/tcl/TkCmd/contents.html) and click on any of the `ttk::widgetName` links, sroll down to "Styling Options", and edit away.

## [Next: Modifying Languages](./modifying-languages.md) | [Previous: Using `DIP`](./use-dip.md) | [Back to Overview](./overview.md)