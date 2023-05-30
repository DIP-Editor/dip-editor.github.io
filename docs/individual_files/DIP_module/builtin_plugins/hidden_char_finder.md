<h1 align="center">hidden_char_finder.py</h1>

## What is the `hidden_char_finder` plugin?

The `hidden_char_finder` plugin is a plugin that finds hidden characters in the editor and marks them with a marker. It is useful for finding hidden characters that are causing problems in the editor.

## How do I use the `hidden_char_finder` plugin?

The plugin is on by default so just leave it on or enable it from the ExtensionsManager (accessible from the `DIP` menu). If you want to disable it, simply disable it from the ExtensionsManager.

## File Documentation:

### Lines 1-11:

These lines are basic imports that call the `tkinter` module, the `PIL` module, the `DIP_module` folder, and the `__main__` module.

### Code:
```python
from __future__ import annotations

from tkinter import Event, Text
from tkinter.ttk import Label, Style

from __main__ import DIP
from PIL import Image, ImageDraw, ImageFont, ImageTk

from DIP_module.editor import Editor
from DIP_module.folder_path import static_folder
from DIP_module.tooltip import ToolTip
```

## Lines 14-47:

These lines define the `create_img()` function. This method creates an image of the character that will be used as the marker. It takes the `Editor` object as a parameter and returns an `ImageTk.PhotoImage` object.

### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `editor` | `Editor` | The `Editor` object to use. |

### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `errimg` | `ImageTk.PhotoImage` | The image of the character. |

### Code:
```python
def create_img(editor: Editor) -> ImageTk.PhotoImage:
    # Define the size of the image and the character
    char_size = 50
    end_image_size = (7, 7)
    char = "+"

    # Set font
    font = ImageFont.truetype(
        f"{static_folder}/Roboto-Regular.ttf", char_size, encoding="unic"
    )

    # Get text width and height
    text_width = int(font.getlength(char))
    text_height = text_width

    # Create the image
    img = Image.new("RGBA", (text_width, text_height), editor.winfo_rgb(editor["bg"]))

    # Draw the character
    draw = ImageDraw.Draw(img)
    fill_color = Style().lookup("CharMarker", "foreground", default="#000000")

    # Draw the character at the center of the image
    draw.text(
        (0, -text_height / 1.85), char, font=font, fill=fill_color
    )  # x and y has to be customized for each character, PIL is weird

    # Resize the image back down to its original size
    img = img.resize((end_image_size[0], end_image_size[1]), Image.LANCZOS)

    # Convert the Image object into a TkPhoto object
    errimg = ImageTk.PhotoImage(img)

    return errimg
```

## Lines 50-83:

These lines define the `Marker` class. The `Marker` class is used to represent help usees find the hidden character. It inherits from the `tkinter.Label` class and has a `set_mark()` method that sets the mark to the marker's index.

### Class attributes

___
| Attribute | Type | Description |
| --------- | ---- | ----------- |
| `char` | `str` | The character to mark. |
| `tooltip` | `ToolTip` | The tooltip of the marker. |
| `index` | `str` | The index of the marker. |
| `text` | `Text` | The `Text` object to use. |

### Class methods

#### `set_mark()`

This method sets the mark to the marker's index.

### Code:
```python
class Marker(Label):
    """A marker for a hidden character"""

    def __init__(self, master: Editor, char: str, index: str, text: Text) -> None:
        # Make the label
        super().__init__(master)

        # Set attributes
        self.char = char
        self.tooltip = ToolTip(self, f"Hidden char: {Extension.hidden_chars[self.char]}")
        self.index = index
        self.text = text

        # Create the image and convert it to a PhotoImage object
        self.errimg = create_img(master)
        self.config(image=self.errimg)

        # Bind events
        self.bind("<Button-1>", self.set_mark)

    def set_mark(self, _: Event) -> None:
        """Sets the mark to the marker's index"""

        del _

        self.text.mark_set("insert", self.index)

    def destroy(self):
        """Destroys the marker and its tooltip"""

        self.tooltip.destroy()
        super().destroy()
```

## Lines 86-199:

These lines define the `Extension` class. The `Extension` class is used to find hidden characters in the editor and mark them with a marker. It inherits from the `tkinter.Label` class and has a `set_mark()` method that sets the mark to the marker's index.

### Class attributes

___
| Attribute | Type| Description |
---------------------------------
| `version` | `str` | A version attribute for the Extension Manager |
| `author` | `str` | An attribute for authors to get credit for their work |
| `hidden_chars` | `dict[str, str]` | A dictionary of hidden characters and their names. |
| `master` | `DIP` | The `DIP` object to use. |
| `locations_and_markers` | `dict[str, Marker]` | A dictionary of the locations of the markers and the markers themselves. |

### Class methods

#### `turn_off()`

A builtin method required in all extensions and plugins. It is called when the extension is turned off.

#### `find_and_mark()`

A method that finds the indexes of hidden characters and will create `Marker`'s for each one to alert the user that there is a possibly unintentional character in that area.

Code:
```python
class Extension:
    """Hidden character finder"""

    version = "1.0.0"
    author = "Moosems"

    hidden_chars: dict[str, str] = {
        "\u00a0": "Non-breaking space",
        "\u180e": "Control char (Mongolian vowel separator)",
        "\u2000": "Control char (en quad)",
        "\u2001": "Control char (em quad)",
        "\u2002": "Control char (en space)",
        "\u2003": "Control char (em space)",
        "\u2004": "Control char (three-per-em space)",
        "\u2005": "Control char (four-per-em space)",
        "\u2006": "Control char (six-per-em space)",
        "\u2007": "Control char (figure space)",
        "\u2008": "Control char (punctuation space)",
        "\u2009": "Control char (thin space)",
        "\u200a": "Control char (hair space)",
        "\u200b": "Control char (zero-width space)",
        "\u202f": "Control char (narrow no-break space)",
        "\u205f": "Control char (medium mathematical space)",
        "\u3000": "Control char (ideographic space)",
        "\ufeff": "Control char (byte order mark)",
    }

    def __init__(self, master: DIP) -> None:
        # Set master
        self.master = master

        # Set other variables
        self.locations_and_markers: dict[str, Marker] = {}

        # Make binds
        for bind in (
            "<Key>",
            "<<ContentChanged>>",
            "<Button-1>",
            "<Configure>",
            "<<HandleScrollHorizontalStatrting>>",
            "<<HandleScrollVerticalStatrting>>",
        ):
            self.master.bind(bind, self.find_and_mark, add=True)

    def turn_off(self) -> None:
        """Called when an extension is turned off"""

        self.master.unbind("<Key>")
        self.master.unbind("<Button-1>")
        self.master.unbind("<Configure>")
        for marker in self.locations_and_markers.values():
            marker.destroy()

    def find_and_mark(self, _: Event | None = None) -> None:
        """Finds all hidden characters and marks them"""

        del _

        # Get the editor widget
        editor: Editor = self.master.tabs[0].editor

        # Get the text in the editor
        text: list[str] = editor.get("1.0", "end-1c").splitlines()

        # Find all hidden characters
        hidden_char_indexes: list[str] = []

        for line_index, line in enumerate(text):
            for char_index, char in enumerate(line):
                if char in Extension.hidden_chars:
                    hidden_char_indexes.append(f"{line_index+1}.{char_index}")

        # Add markers
        for index in hidden_char_indexes:
            # Check if a marker already exists at that location
            if index in self.locations_and_markers or index == "":
                continue
            self.locations_and_markers[index] = Marker(
                self.master.tabs[0].editor, editor.get(index), f"{index}+1c", editor
            )

            # Get the coordinates of the character
            bbox = editor.bbox(index)

            # Check that the character is visible and in view
            start: str = editor.index("@0,0")
            end: str = editor.index(f"@{editor.winfo_width()},{editor.winfo_height()}")
            in_view: bool = editor.compare(start, "<=", index) and editor.compare(
                index, "<=", end
            )

            # Check that the bbox is not None
            if bbox is None or not in_view:
                self.locations_and_markers[index].destroy()
                del self.locations_and_markers[index]
                continue

            # Get the coordinates of the character
            x: int = bbox[0]
            y: int = bbox[1] - 7 # 7 is the height of the marker

            # Make sure the y is fully visible
            if y < 0:
                y = 0

            # Place the marker
            self.locations_and_markers[index].place(x=x, y=y)

        # Remove markers that are no longer needed
        for index in list(self.locations_and_markers.keys()):
            if index not in hidden_char_indexes:
                self.locations_and_markers[index].destroy()
                del self.locations_and_markers[index]

```

## [Previous: [`json_toml_formatter.py`](json_toml_formatter.md)] |  [Back to overview: [`builtin_plugins`](overview.md)] | [Back to Main Page](../../../overview.md)
