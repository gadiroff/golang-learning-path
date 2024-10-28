# golang-learning-path
Steps to learn coding in Golang programming language


### Project Layout
https://github.com/golang-standards/project-layout?tab=readme-ov-file

### Go best practices
https://github.com/codeship/go-best-practices

### What is $GOPATH???
Before Go modules (introduced in Go 1.11), $GOPATH was critical in organizing Go code, as all Go packages and binaries had to be in the $GOPATH directory structure to be properly managed by the 
Go toolchain.

	Defaults: If you don’t set $GOPATH, Go uses a default path:
	On Linux and macOS, it’s $HOME/go
	On Windows, it’s %USERPROFILE%\go
 
Using $GOPATH with Go Modules: With the introduction of Go modules, $GOPATH is now less central. You can now work outside of $GOPATH as Go modules manage dependencies and code organization. However, $GOPATH is still used for caching modules (in $GOPATH/pkg/mod) and storing executable binaries from commands like go install.

Setting up $GOPATH:

To set $GOPATH, add it to your shell configuration file (like .bashrc or .zshrc):

	export GOPATH=$HOME/go
	export PATH=$PATH:$GOPATH/bin  # Add the bin directory to PATH

This setup makes it easy to run Go binaries globally since they are stored in $GOPATH/bin.

