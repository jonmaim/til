# Git auto-completion on MacOS

By far the easiest way to install both Git and git-completion is via [Homebrew](http://mxcl.github.com/homebrew/), so you should pick that one.

### Homebrew

1. [Install homebrew](https://brew.sh)

2. Install Git and bash-completion: `brew install git bash-completion` (Note: If this install fails with a 404 error, and you already have git installed, just remove the git part of this brew install)

3. Add bash-completion to your `~/.bash_profile`:

    ```
    [ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion || {
        # if not found in /usr/local/etc, try the brew --prefix location
        [ -f "$(brew --prefix)/etc/bash_completion.d/git-completion.bash" ] && \
            . $(brew --prefix)/etc/bash_completion.d/git-completion.bash
    }
    ```
