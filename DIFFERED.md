# Differed listing
Here lists some of the disagreements over the initial commit to the definitions of AOSC OS Core.

## GCC and LLVM split
Here discusses the possiblities and reasoning for splitting GCC and LLVM.

### Rationale
GCC and LLVM are two very big packages in the Core definition, especially LLVM, which contains multiple application level components (clang, compiler-rt, etc.). In practice, such phenomenom may result in a very large Core.

### In practices
GCC will be split into "gcc", and "gcc-lib", and LLVM will be split into "llvm", "clang", "clang-analyzer", "compiler-rt", "lldb".

### Negative considerations
Here lists possible negative outcomes of this operation:

* Users may be confused with the package names;
* A Core build may not be usable for development until the actual packages needed for compiling are installed;

### Positive considerations
Here lists possible positive outcomes of this operation:

* Significant decrease in system build sizes;
