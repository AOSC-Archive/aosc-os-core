# AOSC OS Core
AOSC OS Core takes effect as of AOSC OS4's begginning of development. AOSC OS Core will be taken from the original AOSC OS, and be turned into a shared Linux "standard base" and tool chain for AOSC OS itself and its derivatives.

## Rationale
AOSC OS is a decently large project, with more than 2,800 packages included in the community portal at https://repo.anthonos.org and many of its mirrors. Maintaining such large amount of packages is not merely an easy job for the developers - under the circumstances of security vulnerbilities, major updates, and mass rebuilds, AOSC OS developers may not be effective at finishing the tasks in a timely fashion. Added on periodic full system build updates, AOSC OS will be too time consuming for many of the maintainers.

Therefore, AOSC OS Core will serve a standard for **ALL** AOSC OS builds with a version definition of its counterpart, AOSC OS may be released on a non-regulated schedule, thus saving time and potential frustration for developers.

## In practice
The following practices will be taken into account for AOSC OS Core development:

* AOSC OS Core will take the "AOSC OSn" (where "n" is a natural number) version counting rules, however it will count in form of "x.y.z" version numbers;
* aosc-aaa will be included as the only base-line definition for AOSC OS Core, with filesystem structure and basic configurations that may affect essential system behaviors;
* AOSC OS Core will **NOT** be presented in a rolling-release sense, any major version bump should be first discussed (fork it if you do need to update, and PR if you feel like doing so);
* Only tool chain level packages like gcc, llvm, and glibc, etc. will be included;
* **ALL** security updates will be provided when applicable.

### An example of update cycle
AOSC OS3, after being released as the last versioned build release (it will start rolling while AOSC OS Core is still versioned), it will release versions like follows:

* Stable series: 3.1, 3.2, 3.3, ..., 3.10, 3.11, ...
* Experimental (playground) series: 3.99.1, 3.99.2, ..., 3.99.10, 3.99.11, ...

![update_model](https://github.com/AOSC-Dev/aosc-os-core/raw/master/assets/images/AOSC%20OS%20Core%20Rationale%2C%20update%20model.png)

Stable and Experimental series will not affect each other, nor do they have a "testing - release" relationship. 3.99 series (Experimental) will become the future 4.0 series... And the cycle continues.

## Packages
AOSC OS Core will include the following packages:

### Essential sector

* linux+api, "Linux API Headers for glibc"
* zlib, "A Massively Spiffy Yet Delicately Unobtrusive Compression Library"
* glibc, "GNU C Library"
* tzdata, "Time Zone Data"
* gmp, "GNU Multiprecision library"
* mpfr, "Functions for multiple precision math“
* mpc, "A library for the arithmetic of complex numbers"
* gcc-runtime, "GNU Compiler Collection (runtime libraries only)"
* gcc, "GNU Compiler Collection", (languages: c, c++, fortran, lto)
* binutils, "a set of programs to assemble and manipulate binary and object files"
* gdbm, "GNU Database Manager library"
* db, "Berkeley DB embedded database system"
* perl, "a highly capable and feature rich programming language"
* libffi, "portable foreign function interface library"
* readline, "GNU realine library"
* ncurses, "System V Release 4.0 curses emulation library"
* bash, "Bourne Again SHell"
* libtool, "GNU generic library support script"
* aosc-aaa, "bed rock level system definitions"

(total of 19 packages)

### Optional/Enhanced sector

* bzip2, "a freely available, patent free, high-quality data compressor"
* openssl, "the Open Source toolkit for Secure Sockets Layer and Transport Layer Security"
* ca-certs, "Certificate Authority Certificates"
* expat, "a stream oriented C library for parsing XML"
* sqlite, "SQLite software library"
* libedit, "command line editor library providing generic line editing, history and tokenization functions"
* llvm, "Low Level Virtual Machine Infrastructure"

(total of 7 packages)

## Building (theoretical)
A copy of BuildKit is recommended (instructions will be added when BuildKit is ready), BuildKit contains all packages for AOSC OS Core building (Autobuild3 and a script of AOCS OS Core automatic build).

## Derivatives of AOSC OS Core
Derivatives may be build upon AOSC OS Core, as the packages provided in AOSC OS Core may form a fully working chroot environment for developers to get started. However, BuildKit can still be used as BuildKit itself builds upon AOSC OS Core (convenient huh).

### Guidelines
The following guidelines is advised for AOSC OS Core derivatives:

* Usage of Autobuild3 as the build toolkit for the distribution/derivative;
* If the AOSC OS Core is modified, do not mark the distribution/derivative as one of the AOSC OS Core derivatives;
* Support for one of DPKG or RPM as the default package manager;
* Inclusion of lsb-release for identification of the distribution/derivative;
* Use Linux Kernel as the default kernel for the distribution/derivative;
* Use GCC as the default compiler for the distribution/derivative, unless otherwise demanded by packages included;

### Concerns and condemns
The following practices are strongly condemned:

* Inclusion of licensing-controversial software/packages/intellectual works;
* Release an "AOSC OS Core derivative" that is built upon a fork or a modified version of AOSC OS Core;
* Using an outdated AOSC OS Core as the foundation of the distribution/derivative;

## Seeking for help, and reporting bugs
Please seek for help, and report bugs in the "Issues" section of this repository.
