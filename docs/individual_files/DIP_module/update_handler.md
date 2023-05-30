<h1 align="center">update_handler.py</h1>

> The `update_handler` module provides functions for checking for updates.

## Functions

### `get_version()`

Gets the latest version of DIP-Editor from the website and returns it as a string or `None` if the website is unreachable (no internet connection).

### `check_version_greater()`

Checks if the latest version of DIP-Editor is greater than the current version and returns `True` if it is, `False` if it is not, or `None` if the website is unreachable (no internet connection).
