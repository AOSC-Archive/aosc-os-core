AOSC OS Core
============

AOSC OS Core is introduced after the final debut of AOSC OS3 (the last version
of AOSC OS with a versioned name), designed to be a standardized base of:

- Core runtime libraries.
- Basic toolchains.

For AOSC OS and its potential derivatives.

The Core also serves as a versioning agent for AOSC OS (provided by the
`aosc-aaa` package - the base rock definition of AOSC OS).

Rationale
---------

AOSC OS is a decently large project, holding more than 3,500 packages in the
[ABBS Tree](https://github.com/AOSC-Dev/aosc-os-abbs/) and is available for
six architectures:

- AMD64/x86_64 Intel/AMD compatible personal computers, workstations, and
  servers.
- ARMv7 32-bit development boards, phones, and tablets.
- ARMv8 64-bit development boards, phones, tablets, and servers.
- MIPS64r2 N64 (Little Endian) personal computers, workstations, and servers.
- PowerPC 32-bit (Big Endian) personal computers, Macintosh, workstations,
  and servers.
- PowerPC 64-bit (Big Endian) personal computers, Macintosh, workstations,
  and servers.

Maintaining such large amount of packages across multiple architectures is
not an easy job for the maintainers of the project: under the circumstances
of security vulnerbilities, major updates, and mass rebuilds, AOSC OS
developers may not be effective at finishing the respective tasks in a
timely fashion. 

Added on with annual/semi-annual (or schedules of similar fashion) releases,
AOSC OS could be too time consuming for our limited team of maintainers.

Therefore, AOSC OS Core will serve a standard for **ALL** AOSC OS ports 
with a version definition of its counterpart - released on a non-regulated
schedule, thus saving time and potential frustration for the maintainers.

In practice
-----------

The following practices is defined for AOSC OS Core development:

* AOSC OS Core will take in place of the "AOSC OSn" (where "n" is a natural
  number) versioning rules, however it will be versioned in "x.y.z" format.
* `aosc-aaa` will be included as the only base-line definition for AOSC OS
  Core, with filesystem structure and basic configurations that may affect
  system behaviors
* AOSC OS Core will **NOT** be updated as soon as new components were
  released, any major version bump should be first discussed (fork it if you
  do need to update, and PR if you feel like doing so).
* Only tool chain level packages like will be included (by definition).
* **ALL** security updates will be provided when applicable.

### An example of update cycle

AOSC OS3, after being released as the last versioned release (it will start
rolling while AOSC OS Core is still versioned), it will release versions 
like follows:

* Stable series: 3.1, 3.2, 3.3, ..., 3.10, 3.11, ...
* Experimental (playground) series: 3.99.1, 3.99.2, ..., 3.99.10, 3.99.11, ...

![update_model](https://github.com/AOSC-Dev/aosc-os-core/raw/master/assets/images/AOSC%20OS%20Core%20Rationale%2C%20update%20model.png)

Stable and Experimental series will not affect each other, nor do they have
a "testing - release" relationship. 3.99 series (Experimental) will become
the future 4.0 series... And the cycle continues.

Packages
--------

AOSC OS Core currently include the following packages:

* linux+api, "Linux API Headers for glibc"
* zlib, "A Massively Spiffy Yet Delicately Unobtrusive Compression Library"
* glibc, "GNU C Library"
* tzdata, "Time Zone Data"
* gmp, "GNU Multiprecision library"
* mpfr, "Functions for multiple precision math"
* mpc, "A library for the arithmetic of complex numbers"
* isl, "Library for manipulating sets and relations of integer points bounded by linear constraints"
* gcc-runtime, "GNU Compiler Collection (runtime libraries only)"
* gcc, "GNU Compiler Collection", (languages: c, c++, fortran, lto)
* binutils, "a set of programs to assemble and manipulate binary and object files"
* gdbm, "GNU Database Manager library"
* db, "Berkeley DB embedded database system"
* perl, "a highly capable and feature rich programming language"
* readline, "GNU realine library"
* ncurses, "System V Release 4.0 curses emulation library"
* bash, "Bourne Again SHell"
* make, "GNU Make, designed for code processing"
* aosc-aaa, "bed rock level system definitions"

(total of 19 packages)

Building the Core
-----------------

Please first refer to our 
[AOSC Cadet Training](https://github.com/AOSC-Dev/aosc-os-abbs/wiki)
handbook.

Derivatives of AOSC OS Core
---------------------------

Derivatives may be built upon AOSC OS Core, as the packages provided in
AOSC OS Core may form a fully working chroot environment for developers to
get started.

However, BuildKit can still be used as BuildKit itself was built upon AOSC OS 
Core (convenient huh) - and to be fair, a flavour of AOSC OS release on its
own.

You may obtain a copy of BuildKit [here](https://aosc.io/os-download).

Need help?
----------

All questions and bug reports should be filed to the "Issues" section of 
this repository.
