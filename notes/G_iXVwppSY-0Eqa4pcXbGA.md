---
title: 'MISRA C:2012 Checker'
disqus: hackmd
---

# Misra C:2012 Checker

C++ Static Checker for Misra C++:2008 Guidelines

This is a plugin of Clang 6.0

## Compilation
* Prepare LLVM and Clang (llvm/tools/clang) source code. 
* Put Misra C++ checker source code under Clang.
* Add subdirectory command in `clang/CMakeLists.txt`.

```
add_subdirectory( <MisraCppCheckerDir> )
```
* Create build directory out of source `mkdir build`.
* `cmake <llvm_src_path>` at `build`.
* Compile all files `make`.
* After that you can use `make MisraPlugin` to re-compile this project if needed.



## Usage

Note that the program to check should be compiled error-free.

### Show all checkers
you can use this command to find checkers name
`clang -cc1 -load <build>/lib/MisracppChecker.so -analyze -analyzer-checker-help` 

### Check single file
`clang -cc1 -load <build>/lib/MisracppChecker.so -analyze -analyzer-checker=<MisraCPP.X_X_X> <src>`

Or use scan-build

`scan-build -load-plugin <build>/lib/MisracppChecker.so -enable-checker <MisraCPP.X_X_X> -k clang <src> -fsyntax-only`

### Check a project
`scan-build -load-plugin <build>/lib/MisracppChecker.so -enable-checker <MisraCPP.X_X_X> -k <build command>`



## Development

### RecursiveASTVisitor Checker

#### File Structure

`MainCallChecker.cpp` the sample code to call RecursiveASTVisitor in static analyzer
`visitor/OctVisitor.cpp` the RecursiveASTVisitor 
`visitor/fcd.cpp` the sample code for libtooling to call RecursiveASTVisitor and create a stand alone execution file.

#### Add new visitor Checker

Check lib/visitor/visitors/template.cpp


### Use BugReporter
the simplest way to use bugreporter
```
      	BR.EmitBasicReport(AC->getDecl(), Ch,
                     "Misra C++ Rule X_X_X",
                     "MisraCPP",
                     "{message of checker}", ELoc, SR);
 
```
`ELoc` is location of source which you want to be point out (type is PathDiagnosticLocation)
`SR` is range of source which you want to line it. (type is SourceRange)

e.g.
int a = 01234567;
	^~~~~~~~
       ELoc SR


### Add ASTMatcher checker tool
Now we can write checker by ASTMatcher. you have define a class inherit `basematcher`
and define the node match expression in the `match()` and action of the match called `run` 

### Coding Style

Execute tools/git-hook/install.sh to install pre-commit git hook. It will automatically use clang-format to keep .c .h file in good style.
