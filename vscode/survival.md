# Surviving VS Code on MacOS

## Shortcuts

### Writing `console.log`

`SHIFT+COMMAND+P` and write _keyboard shortcuts_. Choose option _Open Keyboard Shortcuts (JSON)_. This opens a file called _keybindings.json_. Modify it similarly to this:

```json
// Place your key bindings in this file to override the defaults
[
  {
    "key": "ctrl+shift+l",
    "command": "editor.action.insertSnippet",
    "when": "editorTextFocus",
    "args": {
      "snippet": "console.log('${TM_SELECTED_TEXT}$1')$2;"
    }
  }
]
```

Now `SHIFT+CTRL+l` will write `console.log('|')` for you.

### Close Explorer

`COMMAND+B` (MacOS) or `CONTROL+B` (Windows).

### Show all opened files

`OPTION+COMMAND+TAB` (MacOS).
