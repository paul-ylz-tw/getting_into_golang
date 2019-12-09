# Getting into Golang

This document serves as a suggested route / reading list for getting into the Go programming language.

## Getting started

As usual, start at the [official 's mouth]: https://golang.org/
The documentation is lean and it is worthwhile going through at least:
- [Golang hello world video (5 mins)](https://www.youtube.com/watch?v=XCsL89YtqCs) gives you amazing amount of context in 5 mins
- [Getting Started](https://golang.org/doc/install) for installation and developer environment setup
- [A Tour of Go](https://tour.golang.org/welcome/1) for understand what's available in the language in an hour or so
- [How to Write Go Code](https://golang.org/doc/code.html) How to organize your project (trivial level), architecture of a Go program.
- Have a scan through [Effective Go](https://golang.org/doc/effective_go.html). There is a lot here to pick up on idioms, style, patterns, but it is also too much for early stage.

## Worth pointing out

- The function named `main` inside the package named `main` will always be the entrypoint of your program. You cannot have multiple entrypoints in a project.
- A `package` is a logical group of code. It is possible for multiple files to make up a package.
- "Exporting" names is the equivalent of making a thing public in OO languages. In Golang, names are exported by using uppercase, e.g. `pi` (not exported), `Pi` (exported). Exporting is required to use functions from another `package`. [see code](https://tour.golang.org/basics/3)
- In practice, although arrays exist, we only use [Slices](https://tour.golang.org/moretypes/7), because they are a more useful than arrays. (Slices are list abstractions that are backed by Arrays)
- When iterating over lists, Go provides the `for range` loop. There are different forms of this type of loop which imply different semantics. Considering how often we will do this, it is worth noting the subtleties outlined in this blog post: [For range semantics](https://www.ardanlabs.com/blog/2017/06/for-range-semantics.html)
- Pay attention to whether you're using value or reference semantics, and refrain from mixing usage of both together. If you're choosing between value and pointer
- Don't do OOP.
  * There's no such thing as a class. There are only structs. [ref Go by Example: Structs](https://gobyexample.com/structs)
  * You can write functions with a receiver, making them "methods", thus emulating an OOP-ish pattern. However, this is generally frowned upon. It's helpful to refer to the guidelines compiled from the [CodeReviewComments repo](https://github.com/golang/go/wiki/CodeReviewComments#receiver-type) about this.
  * Generally, simpler patterns emerge from using functions instead of methods in Go.
- Return `error` from every function and check/handle it from the caller [ref Error handling and Go](https://blog.golang.org/error-handling-and-go). Generally you would not `panic`, which is like throwing an exception.

## Editor Choice

The Go tool set includes formatters, linters and documentation lookup features and most IDE plugins will rely on these to provide the functionality. The tools are powerful so IDE choice will is easy. That said, popular choices are:
- As a ThoughtWorker you probably want to use [JetBrains Goland](https://www.jetbrains.com/go/), mostly for familiarity and version control tools.
- [Visual Studio Code](https://code.visualstudio.com/docs/languages/go) works extremely well for Golang and is the choice of most high profile Golang teachers.
- Vim also works very well using the [vim-go](https://github.com/fatih/vim-go) plugin. As with all things Vim, allow considerable time to set this up

## FAQ

### Package management
This is one of the rapidly changing areas in Golang. The legacy tools in this area are: `govendor` and `dep`. Moving forwards, use [Go Modules](https://github.com/golang/go/wiki/Modules)


### Code style
- Leave formatting to `gofmt`
- Short variable names, e.g. `w` for widget and `ws` for widgets
- Large files are ok, like Linux source code.
- The file containing package `main` and function `main` does not need to be called `main.go`, it's ok to be called `app.go` for example.
  * It's idiomatic to put this file inside a subdirectory called `cmd`.
## Important Blogs
- [Official blog](https://blog.golang.org/)
- [Dave Cheney](https://dave.cheney.net/practical-go)
- [CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments) is a highly approachable source to check on for "common mistakes"

## Learning resources
- JustForFunc Youtube channel
  * E.g. learn about [gRPC](https://www.youtube.com/watch?v=uolTUtioIrc) in your free time
- Organizing large-ish projects [Standard Package Layout](https://medium.com/@benbjohnson/standard-package-layout-7cdbc8391fc1)
- [GoByExample](https://gobyexample.com/) Very useful resource for seeing how to do things (e.g. how to write a `switch` statement)
- Deep dive... [Reading list from Ardan Labs](https://github.com/ardanlabs/gotraining/blob/master/reading/README.md)
- The official [Golang playground](https://play.golang.org/) for trying out simple code snippets
