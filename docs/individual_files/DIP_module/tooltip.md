<h1 align="center">tooltip.py</h1>

> The `ToolTip` class provides tooltip functionality to a given `widget`.

### Class attributes
- `widget`: a `tkinter.Misc` object representing the widget that the tooltip is attached to.
- `tooltip_text`: a string representing the text to be displayed in the tooltip.
- `bg`: a string representing the background color of the tooltip. The default value is "yellow".
- `fg`: a string representing the font color of the tooltip. The default value is "black".
- `tooltip`: a `tkinter.Label` object representing the tooltip label.

### Class methods
#### `__init__()`
Initializes the `ToolTip` object with the given parameters.

##### Parameters
___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `widget` | `tkinter.Misc` | The widget that the tooltip is attached to. |
| `text` | `str` | The text to be displayed in the tooltip. |
| `bg` | `str`, optional | The background color of the tooltip. The default value is "yellow". |
| `fg` | `str`, optional | The font color of the tooltip. The default value is "black". |

#### `show_tooltip()`
Shows the tooltip label with one of a few alignments (automatically determined based on the position of the widget):

##### Alignments

| Alignment | Description |
| --------- | ----------- |
| `top-left` | The left side of the tooltip is aligned with the left side of the widget and goes directly above the widget. |
| `top-right` | The right side of the tooltip is aligned with the right side of the widget and goes directly above the widget. |
| `bottom-left` | The left side of the tooltip is aligned with the left side of the widget and goes directly below the widget. |
| `bottom-right` | The right side of the tooltip is aligned with the right side of the widget and goes directly below the widget. |

#### `hide_tooltip()`
Hides the tooltip label. This method is called automatically when the mouse leaves the widget or clicks down the mouse.