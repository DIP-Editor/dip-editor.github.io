<h1 align="center">special_entry.py</h1>

> The `special_entry` module provides special entry widgets.

## Classes

### `TtkEntryFont`

A TTK Entry widget that gets font from the style instead of 'font='.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `master` | `Misc` | The master widget. |
| `style` | `str`, optional | The style to use. The default value is "TEntry". |
| `args` | `Any` | The arguments to pass to the `Entry` class. |
| `kwargs` | `Any` | The keyword arguments to pass to the `Entry` class. |

#### Methods

##### `update_font()`

Updates the font to be the same as the TTK theme.

### `FilledEntry`

An entry that fills itself with a string when empty.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `master` | `Misc` | The master widget. |
| `fill_string` | `str`, optional | The string to fill the entry with. The default value is "". |
| `bind_func` | `Callable`, optional | The function to bind to the entry. The default value is `lambda *args: None`. |
| `args` | `Any` | The arguments to pass to the `TtkEntryFont` class. |
| `kwargs` | `Any` | The keyword arguments to pass to the `TtkEntryFont` class. |

#### Methods

##### `check_empty()`

Check if the entry is empty and fill it if it is.

##### `check_empty()`

Check if the entry is empty and fill it if it is.