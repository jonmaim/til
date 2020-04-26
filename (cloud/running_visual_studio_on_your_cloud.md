# Running Visual Studio Code on your cloud

[Code-server](https://github.com/cdr/code-server) is the project that allows you to run VS Code (+ extensions) in the cloud and use a local browser to access it. 
[Sshcode](https://github.com/cdr/sshcode) is the way to go to use a SSH connection to install VS Code on your server and spawn the local browser.

## Install

* [Go](https://golang.org/dl)
* `go get -u go.coder.com/sshcode`
* `~/go/bin/sshcode ubuntu@server.cloud "~/vscode/project1"`

If you get this error: `mkdir: cannot create directory ‘/home/ubuntu/.local/share/code-server’: Permission denied`, make sure `~/.local` is owned by `ubuntu`.
