# Setting up Fortran + CMake on modern systems

The following document is a brief guide on how to set up Fortran on various systems.

The purpose is to have something up and running as quickly as possible, which means that
this guide uses whatever Fortran tools are most readily available.

This document is not intended to be comprehensive; it assumes basic knowledge of working
with terminals, compilers, build systems, code editors and Linux environments.

## Windows 10 and later, native

This method uses the `ifx` Fortran compiler, maintained by Intel; and the MSVC C compiler, maintained by Microsoft.

### Installing the tools

1.  Open a `cmd` terminal and install a Fortran compiler, a C compiler and other necessary tools:
    ```
    winget install Kitware.CMake
    winget install Ninja-build.Ninja
    winget install Microsoft.VisualStudio.2022.BuildTools --override "--passive --wait --add Microsoft.VisualStudio.Workload.VCTools;includeRecommended"
    winget install Intel.FortranCompiler --accept-package-agreements
    ```

### Installing the code editor

#### Visual Studio Code

1.  Install Visual Studio Code, for example by running these commands in a `cmd` terminal:
    ```
    winget install vscode
    ```
1.  Install the necessary extensions for Visual Studio Code:
    ```
    code --install-extension ms-vscode.cpptools-extension-pack
    code --install-extension fortran-lang.linter-gfortran
    ```

### Using the code editor

#### Visual Studio Code

Open a `cmd` terminal and run the following commands to open Visual Studio Code in the required environment:

1.  Initialize the environment:
    ```bat
    call "%ProgramFiles(x86)%\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvars64.bat"
    call "%ProgramFiles(x86)%\Intel\oneAPI\setvars.bat"
    ```
1.  Start the code editor:
    ```
    code
    ```

## Windows 10 and later, via WSL

This method uses the `gfortran` Fortran compiler and the `gcc` C compiler, both maintained by the GNU Project.

### Installing the tools

1.  Install the Windows Subsystem for Linux (`wsl`). This step is not complicated,
    however the instructions are different depending on your version of Windows,
    and is therefore not covered here. Follow
    [this official guide](https://learn.microsoft.com/en-us/windows/wsl/install)
    from Microsoft.
1.  Open a `wsl` terminal and install a Fortran compiler, a C compiler and other necessary tools:
    ```
    sudo apt install build-essential gfortran ninja-build gdb cmake
    ```
### Installing the code editor

#### Visual Studio Code

1.  Install Visual Studio Code, for example by running these commands in a `cmd` terminal:
    ```
    winget install vscode
    ```
1.  Install the WSL extension for Visual Studio Code:
    ```
    code --install-extension ms-vscode-remote.remote-wsl
    ```
1.  Install the necessary extensions for Visual Studio Code:
    ```
    code --install-extension ms-vscode.cpptools-extension-pack
    code --install-extension fortran-lang.linter-gfortran
    ```
1.  Open the app normally from Windows, then click on the `><` button in the lower left
    corner of the window, then choose `Connect to WSL`.
1.  Open a `wsl` terminal and install the same extensions as on Windows, using the same commands.

### Using the code editor

#### Visual Studio Code

Open Visual Studio Code in WSL mode, using one of the following methods:

-   Open the app normally from Windows, then click on the `><` button in the lower left
    corner of the window, then choose `Connect to WSL`.
-   Open a `wsl` terminal and simply run the `code` command.

## Linux

This method uses the `gfortran` Fortran compiler and the `gcc` C compiler, both maintained by the GNU Project.

### Installing the tools

1.  Open a `bash` terminal and install a Fortran compiler, a C compiler and other necessary tools:
    ```
    sudo apt install build-essential gfortran ninja-build gdb cmake
    ```
### Installing the code editor

#### Visual Studio Code

1.  Install Visual Studio Code, for example by running these commands in a `bash` terminal:
    ```
    sudo apt update
    sudo apt install software-properties-common apt-transport-https wget -y
    wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
    sudo apt install code
    ```
1.  Install the necessary extensions for Visual Studio Code:
    ```
    code --install-extension ms-vscode.cpptools-extension-pack
    code --install-extension fortran-lang.linter-gfortran
    ```

### Using the code editor

#### Visual Studio Code

Open a `bash` terminal and run the following command to open Visual Studio Code:

1.  Start the code editor:
    ```
    code
    ```

## macOS

TODO

## Fortran tools in Visual Studio Code

Optionally, you can enhance your development experience by installing various helper tools for use within Visual Studio Code.
The tools consist of:

-   `findent` - a formatter
-   `fortls` - a language server.

To install them, follow these steps:

1.  Install a Python distribution or a Python distribution manager, for example:
    -   Debian-like Linux systems:
        ```
        sudo apt install python3 python-is-python3 python3-pip python3-venv
        python -m venv ~/.venv/fortran
        ```
    -   Windows:
        ```
        winget install Python.Python.3.10
        python -m venv %userprofile%\.venv\fortran
        ```
1.  Whenever you initialize the environment, before you start the code editor, perform the following additional commands:
    -   On Windows:
        ```bat
        %userprofile%\.venv\fortran\Scripts\activate
        ```
    -   On Linux:
        ```sh
        source ~/.venv/fortran/bin/activate
        ```
1.  The very first time, before you start the code editor, install the tools:
    ```
    python -m pip install findent fortls
    ```
