# Sublime Text package for [Reason](https://github.com/facebook/reason)

## Features

This plugin simply uses our [language server](https://github.com/freebroccolo/ocaml-language-server#server-capabilities). Every feature is supported. Additionally, we provide the basics: snippets and syntax highlighting.

## Installation (Sublime Text 3)

To install this plugin:

- Go to Command Palette (cmd-shift-p)
- Search `Package Control: Add Repository`
- Add `https://github.com/reasonml-editor/sublime-reason.git`
- Then do the normal `Package Control: Install Package` and install sublime-reason.

Other prerequisites:

- Install the [global binaries](https://reasonml.github.io/docs/en/global-installation.html)
- Install [LSP](https://github.com/tomv564/LSP)
- Install [ocaml-language-server](https://github.com/freebroccolo/ocaml-language-server) through `npm install -g ocaml-language-server`

You might have to restart sublime after installing everything.

## Configuration

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
