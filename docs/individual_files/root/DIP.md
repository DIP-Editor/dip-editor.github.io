<h1 align="center">DIP.py</h1>

> The main file of DIP-Editor. It contains the `DIP` class, which represents an instance of the application, and the `MainApp` class, which represents the application itself.


## Classes

### `DIP`

The `DIP` class is the instance class of the application. In DIP, there is a special window manager. The way it works is by having a hidden `Tk` method that is used to create instances of the application. The `DIP` class is the class that represents these instances. While the `DIP` class inherits from the `Toplevel` class, it works like a normal window.

#### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `master` | `MainApp` | The parent window. |
| `style` | `Style` | The style of the app. |

#### Attributes

___
| Attribute | Type | Description |
| --------- | ---- | ----------- |
| `master` | `MainApp` | The parent window. |
| `style` | `Style` | The style of the app. |
| `tabs` | `List[Tab]` | A list of `Tab` objects that represent opened files. |
| `upon_open_paths` | `List[str]` | A list of file paths to open at app launch. |
| `main_frame` | `Frame` | The main frame of the app. |
| `statusbar` | `StatusBar` | The status bar at the bottom of the app. |
| `bar_items` | `List[BarItem]` | A list of `BarItem` objects that display additional information in the status bar. |

#### Methods

### Menubar Methods:

The `MainApp` class automatically creates a menubar full of methods that would take up too much space to document here and are quite easy to grasp on their own with how simple they are. The methods are:

 - `copy()`
 - `cut()`
 - `paste()`
 - `undo()`
 - `redo()`
 - `select_all()`
 - `move_line_up()`
 - `move_line_down()`
 - `duplicate_line_up()`
 - `duplicate_line_down()`
 - `comment()`
 - `uncomment()`
 - `indent()`
 - `unindent()`

### `add_all_menu_items()`

This method adds all the previous menu items to the menubar.

#### `reload()`

`Reload()`, as the name suggests, reloads the instance of the application. It hides the current instance and double checks all settings and variables and changed to fit these values. After that, it shows the instance again.

#### `create_editor()`

This method creates a `Tab` object and adds it to the list of tabs. These `Tab` objects are used to store information about the tabs. For more information, see the [Tab](../DIP_module/tab.md) page.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `lang_name` | `str` | The name of the language to use. |
| `path` | `str` | The path to the file being edited. |
| `*args` | `Any` | Any additional arguments to pass to the `Editor` class. |
| `**kwargs` | `Any` | Any additional keyword arguments to pass to the `Editor` class. |

#### `argv_open_files()`

This method opens files passed as arguments to the application during launch or passed to the application during runtime.

#### `update_extensions()`

`update_extensions()` updates the extensions of the application. It does this by checking the `extensions` folder for any new extensions and adding them to the list of extensions.

#### `resize_app()`

This method detects the minimum size required for each widget in the application and resizes the application to fit these values so that the application fits across all screen sizes, resolutions, and OS's.

#### `set_base_statusbar()`

This method sets the base statusbar of the application. In particular, it adds the `Reload` button and the `Highlight Language` button.

#### `change_highlight_language()`

This method shows a context menu of possible languages to highlight with and is called when the `Highlight Language` button is pressed in the statusbar. If a language is chosen, the `change_tab_lex()` method is called.

#### `change_tab_lex()`

The `change_tab_lex()` method changes the actual language of the tab. It does this by changing the lexer in the `Editor` class of the tab which changes the syntax highlighting.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `lang_name` | `str` | The name of the language to use. |

#### `open_file()`

This method opens a file in a new tab and adds it to the list of tabs. It takes in a path to the file to open and from this it will determine the language to use and retrieves the text to insert into the tab.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `file_path` | `str` | The path to the file to open. |

#### `update_titlebar()`

This method updates the titlebar to line up with the current tab. It does this by getting the path of the current tab and setting the titlebar to the name of the file.

#### `close_app()`

Close the instance of the application instance.

### `MainApp`

The `MainApp` class is the main class of the application. It is the class that oversees everything going on (including all window instances) and therefore gives access to everything the app has access to. When the application is launched, the `MainApp` class is instantiated and a `DIP` instance is created with it. The `MainApp` class is also used to create the menubar of the application.

#### Attributes

___
| Attribute | Type | Description |
| --------- | ---- | ----------- |
| `version` | `str` | The version of the application. |
| `menubar` | `Menu` | The menubar of the application. |
| `app_menu` | `Menu` | The app menu of the application. |
| `app_instances` | `list[DIP]` | A list of `DIP` objects that represent instances of the application. |
| `extension_manager_open` | `bool` | Whether or not the extension manager is open. |
| `master_settings` | `dict` | The settings of the application. |
| `langs_settings` | `dict` | The settings of the languages. |
| `style` | `Style` | The style of the application. |

#### Methods

##### `create_instance()`

This method creates an instance of the application and adds it to the list of instances.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `verbose_creation` | `bool` | Create a new instance of the application even if one already exists. |

##### `about()`

This method shows the about window and is called when the `About` button is pressed in the menubar.

##### `check_for_updates()`

Also called from the menubar, this method checks for updates to the application and shows a message box telling the user if there is an update or not.


##### `open_extension_manager()`

This method opens the extension manager and is called when the `Extensions` button is pressed in the menubar. The extension manager is a GUI for managing extensions that allows one to get details and enable or disable an extension. For more information, see the [ExtensionManager](../DIP_module/extensions.md) page.

##### `disable_extension()`

This method is called when the `Disable` button is pressed in the extension manager. It disables the extension selected in the extension manager across all `DIP` instances and returns whether the extension was successfully disabled or not.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `extension` | `str` | The name of the extension to disable. |


##### Returns

___
| Return | Type | Description |
| ------ | ---- | ----------- |
| `success` | `bool` | Whether or not the extension was successfully disabled. |

##### `enable_extension()`

Contrasting the `disable_extension()` method, this method enables the extension selected in the extension manager across all `DIP` instances. This method, however, does not return anything.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `extension` | `str` | The name of the extension to enable. |

##### `reload()`

This method, similar to the `reload()` method of the `DIP` class, reloads the application. It hides all `DIP` instances and double checks all settings and variables and changed to fit these values. After that, it shows all `DIP` instances again.

##### `create_binds()`

Create the keybinds for the application based on the settings file passed as an argument. This method is called when the application is launched and during a reload.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `settings` | `dict` | The settings of the application. |

##### `handle_instance_close()`

This method handles the closing of an instance of the application. It removes the instance from the list of instances and checks if there are any instances left. If the OS is not MacOS, it then closes the application. However, if the OS is MacOS, it will allow you to create more instances of the application from the Dock and must be closed from the Dock.

##### Parameters

___
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `instance` | `DIP` | The instance being closed. |

##### `close_app()`

This method closes the application. It does this by closing all instances of the application and then closing the application itself.

##### `update_extensions()`

This method updates the extensions of the application. It does this by checking the `extensions` folder for any new extensions and adding them to the list of extensions.

## [Next: `DIP_module` Overview](../DIP_module/overview.md) | [Back to Overview](./overview.md)