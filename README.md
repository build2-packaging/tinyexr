# build2 Package for tinyexr

This project is a [build2](https://build2.org) package repository that provides access to [`tinyexr`](https://github.com/syoyo/tinyexr), a small, single-header-only C++ library to load and save OpenEXR (`.exr`) images.

[![Official](https://img.shields.io/website/https/github.com/syoyo/tinyexr.svg?down_message=offline&label=Official&style=for-the-badge&up_color=blue&up_message=online)](https://github.com/syoyo/tinyexr)
[![build2](https://img.shields.io/website/https/github.com/build2-packaging/tinyexr.svg?down_message=offline&label=build2&style=for-the-badge&up_color=blue&up_message=online)](https://github.com/build2-packaging/tinyexr)
[![cppget.org](https://img.shields.io/website/https/cppget.org/libtinyexr.svg?down_message=offline&label=cppget.org&style=for-the-badge&up_color=blue&up_message=online)](https://cppget.org/libtinyexr)
[![queue.cppget.org](https://img.shields.io/website/https/queue.cppget.org/libtinyexr.svg?down_message=empty&down_color=blue&label=queue.cppget.org&style=for-the-badge&up_color=orange&up_message=running)](https://queue.cppget.org/libtinyexr)

## Usage
Make sure to add the stable section of the `cppget.org` repository to your project's `repositories.manifest` to be able to fetch this package.

    :
    role: prerequisite
    location: https://pkg.cppget.org/1/stable
    # trust: ...

If the stable section of `cppget.org` is not an option then add this Git repository itself instead as a prerequisite.

    :
    role: prerequisite
    location: https://github.com/build2-packaging/tinyexr.git

Add the respective dependency in your project's `manifest` file to make the package available for import.

    depends: libtinyexr ^1.0.9

The library can be imported by the following declaration in a `buildfile`.

    import tinyexr = libtinyexr%lib{tinyexr}

## Configuration
There are no configuration options available.

## Issues and Notes
- The test data in the `libtinyexr-tests` package is more than 240 MiB in size and, as a consequence, not publishable on `cppget.org` because it is too large. Thus, it is not declared as the mandatory external tests package of `libtinyexr`. It can and should still be used for local testing and for CI runs.
- By using the macros `TINYEXR_USE_THREAD` or `TINYEXR_USE_OPENMP`, `tinyexr` is able to support multithreading by either using C++11 threads or OpenMP. Please note that the package's build system is not automatically adding dependencies and flags for `pthread` or OpenMP.
- Currently, the configuration of dependencies for `tinyexr` is not handled by the package's build system. `tinyexr` uses `miniz` by default and it does not provide specific tests for other configurations. Furthermore, support for `zlib` and `stb`'s implementation of `zlib` only seems to be useful when using `tinyexr` without a build system as drop-in header file. So, for now, please refrain from using the following macros.
    + `TINYEXR_USE_MINIZ`
    + `TINYEXR_USE_STB_ZLIB`
- `tinyexr` adds ZFP compression only as an experimental support on Linux and MacOS. Currently, it is not supported by the packgage's build system. Hence, please, refrain from using the following macro.
    + `TINYEXR_USE_ZFP`
- The compilation of the tests package `libtinyexr-tests` is not supported on target configurations `windows*-clang**` due to the wrong encoding of `win32-filelist-utf16le.inc`. Presumably, this will not be fixed as it is an upstream issue. Please note that the compilation and execution of the basic tests still works on these configurations. Thus, the library should work without flaws on those platforms.
- For Windows, the file `'日本語.exr'` and the test `utf8filename` had to be removed from distribution and execution, respectively. Please, see [this issue](https://github.com/build2/build2/issues/307) for more information.
- Emscripten is not supported.
- The examples are not supported by the package's build system, yet.
- For now, the fuzzers are not compiled and run.

## Contributing
Thank you in advance for your help and contribution to keep this package up-to-date.
Please, file an issue on [GitHub](https://github.com/build2-packaging/tinyexr/issues) for questions, bug reports, or to recommend updating the package version.
If you're making a pull request to fix bugs or update the package version yourself, refer to the [`build2` Packaging Guidelines](https://build2.org/build2-toolchain/doc/build2-toolchain-packaging.xhtml#core-version-management).
