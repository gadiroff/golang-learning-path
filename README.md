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


### Go Modules
Go modules are the standard way to manage dependencies in Go, introduced in Go 1.11 and made the default in Go 1.16. They provide a more flexible and powerful approach than the traditional $GOPATH-based workflow, allowing you to organize dependencies and version control outside of $GOPATH.

Key Features of Go Modules

	1.	Project-Specific Dependencies: Each project can specify its own dependencies and their versions using a go.mod file, allowing for project-specific dependency management.
	2.	Versioning and Dependency Tracking: Go modules allow you to specify exact versions of dependencies, enabling consistent builds and reproducible environments.
	3.	No Need for $GOPATH: You can store your project anywhere on your file system, and Go will still find and manage dependencies without requiring the $GOPATH/src structure.
	4.	Automatic Dependency Resolution: The Go toolchain can automatically resolve, download, and update dependencies, making it easy to manage libraries and frameworks.

Setting Up Go Modules

To set up a Go module for a project, follow these steps:

	1.	Initialize the Module:
Run go mod init <module-name> in your project directory. Typically, <module-name> is a URL path (e.g., github.com/username/projectname), but it can be any unique identifier for the module.

	go mod init github.com/yourusername/yourproject

This command creates a go.mod file in your project directory, which contains the module name and the version of Go used.


	2.	Adding Dependencies:
As you write code and import external packages, Go automatically adds them to the go.mod file the first time you run go build or go test. For example:

	import "github.com/gin-gonic/gin"
When you build or run your code, Go fetches the package and adds it to the go.mod file along with the version.

3.	Tracking Dependency Versions:
The go.mod file records each dependency and its version. Go manages versions automatically based on compatibility rules (e.g., it avoids upgrading to versions with breaking changes unless you specify).
	4.	go.sum File:
Alongside go.mod, Go creates a go.sum file, which records checksums for each version of every dependency. This file ensures the integrity of dependencies, providing protection against tampering or accidental modifications.

Common Go Module Commands

Here are some commonly used commands with Go modules:

	•	go mod tidy: Cleans up the go.mod file by removing any dependencies that are no longer in use.
	•	go get <package>@<version>: Adds or updates a specific version of a dependency. For example, go get github.com/gin-gonic/gin@v1.7.0.
	•	go list -m all: Lists all modules and their versions used by the project.
	•	go mod download: Downloads all dependencies to the module cache ($GOPATH/pkg/mod), useful for building the project in an offline environment.


### Download/Fetch Golang dependencies
We can do it by running:

	go mod get <module_name>

 When we run below commands the dependencies are downloaded/fetched automatically:

	go run
 	go test
  	go build


Update an Existing Dependency to a Specific Version:

	go mod get github.com/spf13/cobra@v1.2.1


 Upgrade All Dependencies to Their Latest Compatible Versions:

 	go mod get -u


  Upgrade All Dependencies to the Latest Major Versions (if compatible):

  	go mod get -u=patch



### Go Module Name Setup

It is best practice to specify go module name as below when initialize the module:

	go mod init github.com/gadiroff/go-projects/my-app

Here the github.com/gadiroff - is your github account, go-projects - is the repository name and the my-app - is the diretory where your app is located.
