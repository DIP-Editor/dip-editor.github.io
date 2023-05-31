<h1 align="center">folder_path.py</h1>

> The `folder_path` module provides paths to various folders and files used by DIP-Editor.

## Constants

### `master_folder`

A `Path` object representing the path to the master folder. The value is `Path(f"{user_data_dir()}/DIP")`.

### `extension_folder`

A `Path` object representing the path to the extensions folder. The value is `Path(f"{master_folder}/extensions/")`.

### `master_location`

A `Path` object representing the path to the master file. The value is `Path(f"{master_folder}/master.json")`.

### `highlight_location`

A `Path` object representing the path to the highlight file. The value is `Path(f"{master_folder}/highlight.json")`.

### `langs_location`

A `Path` object representing the path to the langs file. The value is `Path(f"{master_folder}/languages/langs.toml")`.

### `keybind_location`

A `Path` object representing the path to the keybinds file. The value is `Path(f"{master_folder}/keybinds.json")`.

### `extension_manager_location`

A `Path` object representing the path to the extensionsManager file. The value is `Path(f"{master_folder}/extensions/extensionsManager.json")`.

### `folder`

A `Path` object representing the path to the folder containing the `DIP.py` file. The value is `Path(__file__).parent.parent`.

### `module_dir`

A `Path` object representing the path to the folder containing the `folder_path.py` file. The value is `Path(__file__).parent`.

### `static_folder`

A `Path` object representing the path to the static folder. The value is `Path(f"{module_dir}/static")`.

### `builtin_plugins_folder`

A `Path` object representing the path to the builtin plugins folder. The value is `Path(f"{module_dir}/builtin_plugins")`.