<h1 align="center">extensions.py</h1>

## Classes

### `ExtensionManager`

A GUI for managing extensions.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `master` | `Toplevel` | The master widget. |

#### Methods

##### `insert_extension()`

Insert an extension into the treeview

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `extension` | `str` | The name of the extension. |
| `blacklisted_extensions` | `list[str]` | The list of blacklisted extensions. |
| `version` | `str` | The version of the extension. |
| `author` | `str` | The author of the extension. |

##### `reload()`

Reload the extension manager

##### `select()`

Select an extension

##### `enable()`

Enable an extension

##### `disable()`

Disable an extension

##### `filter()`

Filter the extensions

##### `close()`

Close the extension manager

## Functions

### `get_extension_info()`

Get the info of an extension.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `filename` | `str` | The filename of the extension. |
| `dir` | `str` | The directory of the extension. |
| `extensions_to_skip` | `list[str]`, optional | The list of extensions to skip. The default value is `[""]`. |
| `skip_the_skip` | `bool`, optional | Whether to skip the skip list. The default value is `False`. |

#### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `info` | `list[ModuleType, str, str]` | The info of the extension. |


### `load_extension()`

Load an extension.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `window` | `Tk` | The window to load the extension in. |
| `filename` | `str` | The filename of the extension. |
| `dir` | `str` | The directory of the extension. |
| `extensions_to_skip` | `list[str]`, optional | The list of extensions to skip. The default value is `[""]`. |
| `skip_the_skip` | `bool`, optional | Whether to skip the skip list. The default value is `False`. |

#### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `extension` | `ModuleType` (`Extension`) | The loaded extension. |

### `load_extensions()`

Load all the extensions in the extensions folder and the builtin_plugins folder.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `window` | `Tk` | The window to load the extensions in. |
| `extensions_to_skip` | `list[str]`, optional | The list of extensions to skip. The default value is `[""]`. |

#### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `loaded_extensions` | `list[list[Any, str]]` | The loaded extensions. |

### `all_extensions()`

Get all the extensions and builtin plugins and return them as a list.

#### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `extensions` | `dict[str, dict[str, str, str]]` | The extensions. |
