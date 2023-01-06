# Barr C Linting Suite

This repository contains a few files to specify rules that provide automated compliance with the [2018 Barr Embedded C Coding Standard](https://barrgroup.com/sites/default/files/barr_c_coding_standard_2018.pdf). A full specification of what is covered by this repository is located in COVERAGE.md.

To accomplish compliance, `clang-format` is used for stylistic conformity (e.g., line length, bracket spacing, etc.) while `clang-tidy` is used for both stylistic conformity and for more complicated semantic issues (e.g., `constant == var` equality checking versus `var == constant`, and initializing all variables). Where possible, `clang-tidy` will attempt to provide fixes to the warnings it provides. 

Due to the way `clang-tidy` is designed, it was necessary to create a custom version of the package so that these checks would be integrated. This is included as a `tar.gz` file and is suitable for linux systems. 

The source files for these checks, along with their documentation and unit tests are located within the `src`, `docs`, and `test` subdirectories respectively.

# Future Work

A merge request has been created to introduce these checks into the main releases of `clang-tidy`. 

# Common Issues

### When I try to format my code with this `.clang-format` file, it doesn't seem to work!

This is most likely because your version of `clang-format` is not compatible with the options used in the `.clang-format` file. 

To check your `clang-format` version, run `clang-format --version`. If this version is less than the current supported version of the file (currently 16), you may have to comment some of the fixes that `clang-format` provides. 

A minimum version number has been provided next to each configured option in the `.clang-format` file - comment out any option(s) that are too recent for your version of `clang-format`.

Alternatively, you may want to download a newer version of `clang-format`. See the `clang` project documentation on instructions for your specific platform.