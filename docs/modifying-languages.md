<h1 align="center">Modifying Languages</h1>

## How do `DIP` languages work?

`DIP` languages have a very rigid structure that must be fulfilled. The language information is located in a central `langs.toml` file in the `languages` folder for `DIP` (see [Editing Themes](./edit-themes.md)). 

An example of a language in the `langs.toml` file is as follows:
```toml
languages = [
  "python",
  "example_language",
  "tcl"
]
# A list of the languages that are supported by DIP
# Please ensure that your language is added to this list
...
[example_language]
lexer = "pygments" 
# Options are "pygments", "tree-sitter", and "none" 
# none means that the language has no syntax highlighting 
# either because it isn't in either pygments or tree-sitter 
# or because you don't want it to have syntax highlighting
extensions = [ "*.example" ]
# The file extensions that the language uses
indent_size = 4
# The number of spaces that are standard for indentation 
# in the language
default_indent_style = "space"
# Whether the language uses spaces or tabs for indentation
end_of_line = "lf"
# The character(s) that are used to denote the end of a line
charset = "utf-8"
# The character set that the language uses
trim_trailing_whitespace = true
# Whether the editor should trim trailing whitespace for the language
insert_final_newline = false
# Whether the editor should insert a newline at the end of the file
max_line_length = 80 # TODO: Make a line through the editor at this length
# The maximum number of characters that a line should be
comment_prefix = "#"
# The character(s) that are used to prefix comments in the language
# Whether the language converts tabs to spaces

  [Example_Language.command]
  Windows = ""
  Linux = ""
  Darwin = ""
  # The commands that are used to run the language on the 
  # different operating systems from the terminal

  [Example_Language.indent_regexes]
  indent = ""
  dedent = ""
  # The regexes that are used to detect whether to indent or
  # dedent the next line of code or to keep the indentation
```

## How do I add a language to `DIP`?

To add a language, simply fill the template above and be sure to fill every key.If a key is not filled `DIP` may not work properly while editing for your language and may even crash. If you add a language that you believe should be supported by `DIP` but isn't, please open an issue on the `DIP` repository with the language info. Most important to adding these languages is that the indent and dedent regexes work well. If you would like to learn how to write these regexes, please see [Regex101](https://regex101.com/) or try joining your IRC servers `#regex` channel.


## [Next: Extensions/Plugins](./extensions.md) | [Previous: Editing Themes](./edit-themes.md) | [Back to Overview](./overview.md)