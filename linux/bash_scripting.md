# Bash scripting

## Skip operation if command-line parameter is present

  * `$@` is parameters passed to the script as a string.
  * `*"str"*` is string surrounded by wildcards, meaning string is leading and followed by 0 or more random characters.   

```bash
[[ "$@" == *"skip-op"* ]] && echo "skipping 🐗 op" || op p1 p2
```
