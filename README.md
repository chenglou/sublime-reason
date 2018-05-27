# Sublime Text package for [Reason](https://github.com/facebook/reason)

## Features

This plugin provides syntax highlight and snippets for Reason.

All other Reason editor functionalities are independently provided by our [language server](https://github.com/freebroccolo/ocaml-language-server#server-capabilities).

Both installations instructions are below.

## This Plugin's Installation

- Go to Sublime Text -> Preferences -> Browse Packages
- In the terminal, `cd` into that folder (if you're on macOS, you can click & drag the folder icon into your terminal window)
- `git clone https://github.com/reasonml-editor/sublime-reason`

## Language Server Installation

The other 90% of Reason's editor experience (intelligent autocompletion, type hint, formatting, jump-to-definition, etc.) is provided by ocaml-language-server (a code analysis backend shared by all editors).

> **Heads Up!**
> `nodenv` is known to cause various issues so make sure to install an npm package with the system version of Node

- Install the [global binaries](https://reasonml.github.io/docs/en/global-installation.html).
- Install [ocaml-language-server](https://github.com/freebroccolo/ocaml-language-server) itself through `npm install -g ocaml-language-server`.
- Install [LSP](https://github.com/tomv564/LSP), the sublime text plugin that communicates with ocaml-language-server.

Restart sublime after installing these.

### Language Server Configuration

**Nothing**. Sublime's LSP above has built-in OCaml/Reason support. But you might want to set up some keyboard shorcuts for common actions. See them [here](https://lsp.readthedocs.io/en/latest/#features). They're exposed as [these functions](https://github.com/tomv564/LSP/blob/604df779ee63daa1c008b9e1b12169a61f4007ea/Menus/Context.sublime-menu).

Our recommendations:

- Go to Command Palette (`cmd-shift-p`) -> Preferences: Key Bindings
- Add the following to your configuration:

  ```json
  [
    // ...whatevever config you had before
    {
      "keys": ["super+alt+enter"],
      "command": "lsp_symbol_definition",
      "context": [
        {
          "key": "selector",
          "operator": "equal",
          "operand": ["source.reason", "source.ocaml"]
        }
      ]
    },
    {
      "keys": ["super+shift+c"],
      "command": "lsp_format_document",
      "context": [
        {
            "key": "selector",
            "operator": "equal",
            "operand": ["source.reason"]
        }
      ]
    }
  ]
  ```

  (`super` means `command` on macOS) so you can do e.g. `cmd-shift-c` to format your Reason files.
