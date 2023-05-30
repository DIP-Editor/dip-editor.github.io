<h1 align="center">tab.py</h1>

> The `Tab` class represents a tab in the text editor and is used to store information about the tab.

This class represents a tab in a text editor. It contains information about the path to the file being edited, the index of the tab, the language being used, and an instance of the `Editor` class for the text editor to use.

## Class attributes
- `path`: a string representing the path to the file being edited.
- `index`: an integer representing the index of the tab.
- `language`: a string representing the language being used.
- `editor`: an instance of the `Editor` class.

## Class methods
### `__init__()`
This method initializes the `Tab` object with the given parameters.

#### Parameters
___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `master` | `Misc` | The parent widget. |
| `path` | `str` | The path to the file being edited. |
| `index` | `int` | The index of the tab. |
| `language` | `str` | The language being used. |
| `editor` | `Editor` | An instance of the `Editor` class. |

### `reload()`
This method reloads the tab with new path, index and language values. If a parameter is not passed, the current value of the corresponding attribute is used.

#### Parameters
___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `new_path` | `str` | The new path to the file being edited. |
| `new_index` | `int` | The new index of the tab. |
| `new_language` | `str` | The new language being used. |

## [Next: ]