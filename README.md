# Go Notes

## Version
Go v1.18+

## Go Modules and Packages

- A single directory can only have one package
- The package name can be different from the directory name. When they are different, you should use the directory name with the `import` keywoard and reference the package name in your code. 
- When importing a package, you either specify its full path (even for a sub directory of the current project), or put the package in `$GOROOT/src` (searched first) or `$GOPATH/src` (searched second).

## Go.mod
### The [`replace` directive](https://go.dev/ref/mod#go-mod-file-replace)
Right hand side path:
  - If the path on the right side of the arrow is an absolute or relative path (beginning with ./ or ../), it is interpreted as the local file path to the replacement module root directory, which must contain a go.mod file. The replacement version must be omitted in this case.
  - If the path on the right side is not a local path, it must be a valid module path. In this case, a version is required. The same module version must not also appear in the build list.



