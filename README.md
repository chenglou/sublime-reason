# Sublime Text package for [Reason](https://github.com/facebook/reason)

To have the complete Sublime Text Reason experience, there are two plugins to install: this one, and [language-server](https://github.com/jaredly/reason-language-server).

This one provides syntax highlight, snippets for Reason and allows related features to recognize the Reason syntax.

Language-server provides all the others (autocompletion, type hint, jump-to-definition, etc.).

## This Plugin's Installation

The plugin's [published on Package Control](https://packagecontrol.io/packages/Reason).

- Go to Command Palette (`cmd-shift-p`) -> Package Control: Install Package.
- Choose Reason.

## Language Server Installation

See https://github.com/jaredly/reason-language-server#sublime-text for language-server installation and configuration.

If you're doing native development, instead of reason-language-server, you can try [ocaml-language-server](https://github.com/freebroccolo/ocaml-language-server#installation-1).

### Bonus Language Server Configuration

In addition to the installation & configuration above, you might want to set some extra keyboard shortcuts.

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
          "operand": ["source.reason"]
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

`super` means `command` on macOS, so you can do e.g. `cmd-shift-c` to format your Reason files.

[Here](https://github.com/tomv564/LSP/blob/master/Menus/Context.sublime-menu) are all the `command`s you can assign shortcuts to.
