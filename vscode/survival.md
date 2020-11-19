# Surviving VS Code on MacOS

## A shortcut for writing `console.log`

`SHIFT+COMMAND+P` and write 'keyboard shortcuts'. Choose option 'Open Keyboard Shortcuts (JSON)'. This opens a file called 'keybindings.json'. Modify it similarly to this:

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

## Shortcut to close Explorer

`COMMAND+B` (MacOS) or `CONTROL+B` (Windows).
