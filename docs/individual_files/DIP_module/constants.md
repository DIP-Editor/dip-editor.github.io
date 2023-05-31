<h1 align="center">constants.py</h1>

> The `constants` module provides constants and functions for the DIP-Editor.

## Constants

### `SYSTEM`

A string representing the current operating system. The value is either `"Darwin"`, `"Linux"`, or `"Windows"`.

### `CONTMAND`

A string representing the name of the modifier key used for shortcuts. The value is either `"Command"` or `"Control"`.

### `STARTS`

A list of strings representing the characters that start a pair. The value is `["{", "[", "(", '"', "'", "<"]`.

### `ENDS`

A list of strings representing the characters that end a pair. The value is `["}", "]", ")", '"', "'", ">"]`.

### `PAIRS`

A list of tuples representing the pairs of characters. The value is `[("{", "}"), ("[", "]"), ("(", ")"), ('"', '"'), ("'", "'"), ("<", ">")]`.

### `EXCLUDE_PAIR_INDENT`

A list of strings representing the characters that do not indent when they are typed. The value is `['"', "'"]`.

### `SPECIAL_BIND_NAMES`

A dictionary representing the special names for the special binds. The value is `{"<": "<less>", ">": "<greater>"}`.

### `STRING_TYPES`

A list of strings representing the types of strings. The value is `['"', "'"]`.

### `FONT_WIDGETS`

A list of strings representing the widgets that can have their font changed. The value is `["TLabel", "TButton", "TText", "Treeview", "TEntry"]`.

### `FONT_SIZES`

A list of strings representing the font sizes. The value is `["NormalFont", "MediumFont", "LargeFont"]`.

## Functions

### `get_widget_center()`

Gets the center of a widget and returns it as a tuple of integers.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `widget` | `Misc` | The widget to get the center of. |

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `center` | `tuple[int, int]` | The center of the widget. |

## Decorators

### `event_create_decorator()`

Creates an event with the given string.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `event_string` | `str` | The string to use for the event. |
| `end` | `bool`, optional | Whether or not to create an ending event. The default value is `False`. |

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `result` | `Any` | The result of the function. |

### `event_create_with_if_decorator()`

Creates an event with the given string and if statement.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `event_strings` | `tuple[str, str]` | The strings to use for the event. |
| `if_statement` | `list[str, str]` | The if statement to use for the event. |
| `end` | `bool`, optional | Whether or not to create an ending event. The default value is `False`. |

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `result` | `Any` | The result of the function. |

### `self_focused_check()`

Checks if the widget is focused before running the function and returns the result.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `func` | `callable` | The function to run. |

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `result` | `Any` | The result of the function. |

## Classes
### `FauxEvent`
A class that represents a faux event. Used most in the menu bar to call function that require an event.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `widget` | `Misc` | The widget to use for the event. |
| `event` | `str` | The event to use for the event. |

#### Attributes

___
| Attribute | Type | Description |
| --------- | ---- | ----------- |
| `widget` | `Misc` | The widget to use for the event. |
| `event` | `str` | The event to use for the event. |
