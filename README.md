# Go Notes

## Version
Go v1.18+

## Go Modules and Packages

- A single directory can only have one package
- The package name can be different from the directory name. When they are different, you should use the directory name with the `import` keywoard and reference the package name in your code. 
- When importing a package, you either specify its full path (even for a sub directory of the current project), or put the package in `$GOROOT/src` (searched first) or `$GOPATH/src` (searched second).

## Go.mod

### The `replace` directive ([more details](https://go.dev/ref/mod#go-mod-file-replace))
Right hand side path:
  - If the path on the right side of the arrow is an absolute or relative path (beginning with ./ or ../), it is interpreted as the local file path to the replacement module root directory, which must contain a go.mod file. The replacement version must be omitted in this case.
  - If the path on the right side is not a local path, it must be a valid module path. In this case, a version is required. The same module version must not also appear in the build list.
  - replace directives only apply in the main module’s go.mod file and are ignored in other modules. See Minimal version selection for details. If there are multiple main modules, all main modules' go.mod files apply. Conflicting replace directives across main modules are disallowed, and must be removed or overridden in a replace in the go.work file.

### Pulling code when the GitHub tag/branch has been updated
This is a bad idea for published tags/releases. But for testing, you can just run `go get` with the module path and specific commit you desire.

If you use the `replace` directive in `go.mod`, `go get` does not seem able to use the given commit for the substitute module. Hence, you should edit the entry using `replace` in `go.mod` to specify the desired commit. After than, run `go get` with the original path (left side of the `replace` statement) **without** any commit or version, and `go get` would be able to update `go.mod` and `go.sum` the desired commit.


