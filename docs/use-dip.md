<h1 align="center">Using `DIP`</h1>

> **Note**
> `Contmand` is the expression used in `DIP` to refer to the `Control` key on Windows and Linux and the `Command` key on MacOS.
> Expressions sorround by `{}` are meant to express actions while test like `this` are meant to express the name of a button or menu item.

## File Management

### Opening Files

Bind: `Contmand` + `O`.\
GUI: `File` > `Open` or `File Explorer` > {Double click on file}.\
Behavior: 
 - Opens a file explorer window to select a file to open,
 - Opens the file in a new tab.

### Saving Files

Bind: `Contmand` + `S` or `Contmand` + `Shift` + `S`.\
> **Note**
> The `Contmand` + `Shift` + `S` bind is used to save under a different name or location in which case the `Save As` dialog is opened.
GUI: `File` > `Save` or `File Explorer` > {Right click on file} > `Save`.\
Behavior: 
 - Saves the file in the current tab,
 - If the file has not been saved before, opens a file explorer window to select a location to save the file.

### Creating New Folders or Files

Bind: `None`.\
GUI: `File Explorer` > {Left click on folder or file icon}.\
Behavior: 
 - Creates input field to enter name of new folder or file.

## Tabs
### Creating New Tabs

Bind: `Contmand` + `T`.\
GUI: `File` > `New Tab`.\
Behavior: 
 - Creates a new tab.


### Closing Tabs

Bind: `Contmand` + `w`.\
GUI: `File` > `Close Tab` or {Press close button on the right side of tab}.\
Behavior: 
 - Asks to save the file if it has been modified since the last save,
 - Closes the current tab.

## Reopen Last Closed Tab

Bind: `Contmand` + `Shift` + `T`.\
GUI: `File` > `Reopen Last Closed Tab`.\
Behavior: 
 - Reopens the last closed tab.

## Opening New Windows

Bind: `Contmand` + `Shift` + `N`.\
GUI: `File` > `New Window`.\
Behavior: 
 - Opens a new window.

## Editing Files

### Copying and Pasting

Bind: `Contmand` + `c` then `Contmand` + `v`.\
GUI: `Edit` > `Copy` and `Edit` > `Paste`.\
Behavior: 
 - Copies the selected text to the clipboard,
 - Pastes the text from the clipboard to the cursor location.

### Undoing and Redoing

Bind: `Contmand` + `z` and `Contmand` + `Shift` + `z`.\
GUI: `Edit` > `Undo` and `Edit` > `Redo`.\
Behavior: 
 - Undoes the last action,
 - Redoes the last action.

### Moving Text

Bind: `Option` + `Up` or `Option` + `Down`.\
GUI: `Edit` > `Move Line Up` and `Edit` > `Move Line Down`.
Behavior: 
 - Moves the selected text up or down.

## Duplicating Text

Bind: `Option` + `Shift` + `Up` or `Option` + `Shift` + `Down`.\
GUI: `Edit` > `Duplicate Line Up` and `Edit` > `Duplicate Line Down`.
Behavior: 
 - Duplicates the selected text up or down.

### Finding and Replacing Text

Bind: `Contmand` + `f`  + {Enter text to find} then {Use find/replace GUI to replace text (hover over buttons for more info)}.\
GUI: {Use find/replace GUI to find and replace text}.\
Behavior: 
 - Finds and replaces text.

### Commenting and Uncommenting Text

Bind: `Contmand` + `/`.\
GUI: `Edit` > `Comment Line` and `Edit` > `Uncomment Line`.\
Behavior: 
 - Comments or uncomments the selected line.

### Indenting and Unindenting Text

Bind: `Tab` and `Shift` + `Tab`.\
GUI: `Edit` > `Indent Line` and `Edit` > `Unindent Line`.\
Behavior: 
 - Indents or unindents the selected line or selection.

## Using the Terminal

### Opening the Terminal

Bind: `None`.\
GUI: {Left click and hold mouse, then drag to up till terminal appears} or `Terminal`.\
Behavior: 
 - Opens the terminal.

### Closing the Terminal

Bind: `None`.\
GUI: {Left click and hold mouse, then drag to down till terminal disappears} or `Terminal`.\
Behavior: 
 - Closes the terminal.

### Running Commands

Bind: `None`.\
GUI: {Type command in terminal and press `Enter`}.\
Behavior: 
 - Runs the command in the terminal.

## [Next: Editing Themes](./edit-themes.md) | [Previous: Using DIP](./use-dip.md) | [Back to Main](../README.md)