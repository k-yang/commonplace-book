# modules
A go module is a collection of go packages stored in a file tree with a `go.mod` at its root. A `go.mod` file defines the `module path` and the `dependency requirements`. 

# modes of operation
The go command operates in either module mode or GOPATH mode. GOPATH mode is considered legacy and starting in Go 1.13, the default is module mode. Before, GOPATH mode was triggered when operating inside of `$GOPATH/src`. Now, module mode is used by default.

# GOPATH
GOPATH is the root path of your Go workspace. By default, it is `~/go` (`/Users/kevinyang/go`). It contains two folders: `pkg/` and `bin/`. There used to also be a `src/` directory but that was used in GOPATH mode and is no longer used, so it no longer exists.

`pkg/` contains compiled package code. `bin/` contains executables compiled by Go. 
# GOROOT
GOROOT is the path of your Go installation. It shouldn't be changed unless you plan on having different Go versions installed on your system concurrently. 

GOROOT is usually `/usr/local/go`. 

# go get
go get is only for adding, updating, or removing dependencies in `go.mod`.

Starting in Go 1.17, installing executables with `go get` is deprecated. `go install` may be used instead. 

In Go 1.18, `go get` will no longer build packages; it will only be used to add, update, or remove dependencies in `go.mod`. Specifically, `go get` will always act as if the `-d` flag were enabled.

# go install
go install is used for global installation of executable tools. e.g. `go install golang.org/x/tools/gopls@latest`. 

You can't do `go install package` without the `@version` suffix outside of a module directory. Inside a module directory, it is possible to run `go install package` without the `@version` suffix and run it in "module-aware" mode. 

