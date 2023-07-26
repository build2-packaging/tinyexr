<h1 align="center">
    build2 Package for tinyexr
</h1>

<p align="center">
    This project builds and defines the build2 package for <a href="https://github.com/syoyo/tinyexr">tinyexr</a>.
    tinyexr is a small, single header-only library to load and save OpenEXR (.exr) images. tinyexr is written in portable C++ (no library dependency except for STL), thus tinyexr is good to embed into your application.
</p>

<p align="center">
    <a href="https://github.com/syoyo/tinyexr">
        <img src="https://img.shields.io/website/https/github.com/syoyo/tinyexr.svg?down_message=offline&label=Official&style=for-the-badge&up_color=blue&up_message=online">
    </a>
    <a href="https://github.com/build2-packaging/tinyexr">
        <img src="https://img.shields.io/website/https/github.com/build2-packaging/tinyexr.svg?down_message=offline&label=build2&style=for-the-badge&up_color=blue&up_message=online">
    </a>
    <a href="https://cppget.org/libtinyexr">
        <img src="https://img.shields.io/website/https/cppget.org/libtinyexr.svg?down_message=offline&label=cppget.org&style=for-the-badge&up_color=blue&up_message=online">
    </a>
    <a href="https://queue.cppget.org/libtinyexr">
        <img src="https://img.shields.io/website/https/queue.cppget.org/libtinyexr.svg?down_message=empty&down_color=blue&label=queue.cppget.org&style=for-the-badge&up_color=orange&up_message=running">
    </a>
</p>

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

    depends: libtinyexr ^ 3.0.2

The library can be imported by the following declaration in a `buildfile`.

    import tinyexr = libtinyexr%lib{tinyexr}

## Configuration
There are no configuration options vailable.

## Issues
Currently, there are no known issues.

## Contributing
Thanks in advance for your help and contribution to keep this package up-to-date.
For now, please, file an issue on [GitHub](https://github.com/build2-packaging/tinyexr/issues) for everything that is not described below.

### Recommend Updating Version
Please, file an issue on [GitHub](https://github.com/build2-packaging/tinyexr/issues) with the new recommended version.

### Update Version by Pull Request
1. Fork the repository on [GitHub](https://github.com/build2-packaging/tinyexr) and clone it to your local machine.
2. Run `git submodule init` and `git submodule update` to get the current upstream directory.
3. Inside the `upstream` directory, checkout the new library version `X.Y.Z` by calling `git checkout vX.Y.Z` that you want to be packaged. Here, it is probably not a version but the newest commit from the master branch instead.
4. If needed, change source files, `buildfiles`, and symbolic links accordingly to create a working build2 package. Make sure not to directly depend on the upstream directory inside the build system but use symbolic links instead.
5. Update library version in `manifest` file if it has changed or add package update by using `+n` for the `n`-th update.
6. Make an appropriate commit message by using imperative mood and a capital letter at the start and push the new commit to the `master` branch.
7. Run `bdep ci` and test for errors.
8. If everything works fine, make a pull request on GitHub and write down the `bdep ci` link to your CI tests.
9. After a successful pull request, we will run the appropriate commands to publish a new package version.

### Update Version Directly if You Have Permissions
1. Inside the `upstream` directory, checkout the new library version `X.Y.Z` by calling `git checkout vX.Y.Z` that you want to be packaged. Here, it is probably not a version but the newest commit from the master branch instead.
2. If needed, change source files, `buildfiles`, and symbolic links accordingly to create a working build2 package. Make sure not to directly depend on the upstream directory inside the build system but use symbolic links instead.
3. Update library version in `manifest` file if it has changed or add package update by using `+n` for the `n`-th update.
4. Make an appropriate commit message by using imperative mood and a capital letter at the start and push the new commit to the `master` branch.
5. Run `bdep ci` and test for errors and warnings.
6. When successful, run `bdep release --tag --push` to push new tag version to repository.
7. Run `bdep publish` to publish the package to [cppget.org](https://cppget.org).