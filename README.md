# Minimal Fortran + Visual Studio Code project

This is a minimal template project for using Fortran on modern systems, including:

-   Windows 10 and later, via WSL
-   Windows 10 and later, native
-   Linux
-   macOS

For installation of tools and Visual Studio Code, see [SETUP.md](SETUP.md).

## Building the project

There are several methods to build the project, both from command line as well as from within Visual Studio Code.
To build the project from command line, follow these steps:

1.  Initialize the environment, if necessary
1.  Go into the root project of the directory
1.  Configure the project:
    ```
    cmake --preset Release
    ```
1.  Build the project:
    ```
    cmake --build build/Release
    ```
1.  Run the binary:
    ```
    # Windows
    .\build\Release\fortran_test.exe
    # Linux
    ./build/Release/fortran_test
    ```

## Deploying the binary

To run the binary on any other computer, you must install the appropriate runtime library on that computer.
For example:

-   For the `ifx` compiler, install the runtime which has [at least][ref-link-intel-forums] the same version as the compiler; ideally, you can just install the newest possible version. All runtime versions are available on [this webpage from Intel][ref-link-intel-runtimes].


[ref-link-intel-forums]: https://community.intel.com/t5/Intel-Fortran-Compiler/Fortran-DLL-run-time-dependencies/m-p/1539623#M168959
[ref-link-intel-runtimes]: https://www.intel.com/content/www/us/en/developer/articles/tool/oneapi-standalone-components.html
