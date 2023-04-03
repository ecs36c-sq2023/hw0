# Homework 0

> Due: 04-12-2023 11:59:59 PM

The goal of this homework is for you to

- setup and get familiarized with the development environment, build tools, and
  homework submission process;
- review C++ basics by implementing Insertion Sort.

**Corresponding Topic**: Design and Analysis of Algorithms, C++ Basics, Using
CMake

## Table of Contents

1. [Homework Spec](#homework-spec)
2. [Setup Dev Env & Run/Debug Your Program](#setup-dev-env--rundebug-your-program)
3. [CMakeFiles](#cmakefiles)

## Homework Spec

> ⚠️ DO NOT change the section marked with
>
> ```cpp
> /** DO NOT CHANGE **/
> ...
> /** DO NOT CHANGE **/
> ```

1. Setup your environment using one of options in the next section.

2. Edit `main.cpp` to implement the I/O Interface.

   - We will only check for `./main [INPUT_FILE] [OUTPUT_FILE]` and compare the
     output files with expected for final grading

3. Implement the necessary functions to store the input file into `IntSequence`.

4. Edit `insertion_sort.cpp` to implement Insertion Sort

### Input Format

We will provide some sample tests in `input/` folder. The input file format is
the following:

- Line 1 is a single integer $n$;
- Line 2 is a series of $n$ integer(s) separated by a space.

You can assume the input format is consistent for all test cases.

### Output Format

The expected output, provided in `expected/` is a single line with sorted list
of integers separated by a space and ended with a line break.

### Submitting your Homework

- Run `./generate_submission.sh` to create a zip file `hw0-submission.zip`.
- Transfer `hw0-submission.zip` to your host (if necessary).
  - If you are in VS Code with Dev Container / Remote SSH / WSL2, you can right
    click on `hw0-submission.zip` and click `Download`.
  - If you are using a terminal, you can use `scp` or `sftp`.
- Submit `hw0-submission.zip` on Gradescope.

## Setup Dev Env & Run/Debug Your Program

Use one of the following options to setup your environment.

> ⚠️ If you're a student, **DO NOT FORK** this repository because you cannot
> change the visibility of a forked repo to private. If you plan to use Git for
> version control (which is encouraged), run `rm -rf .git && git init` after
> setting up using one of the options below and push to your **private**
> repository. Any public repository containing part of this homework solution
> will be reported to SJA.

### Option 1: VS Code with Local Dev Container

> This option provides a Graphical User Interface (GUI) for code editing and
> debugging.

> This option does not require internet connection when coding after initial
> setup.

- Install/update the following software on your local OS:

  - [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) (Required for
    Windows only) (Docker will use WSL2 as backend on Windows)
  - [Docker Desktop](https://www.docker.com/products/docker-desktop/)
    - Make sure you install the correct version based on your hardware
      (especially for Apple-chip powered Macbook and ARM-based Windows PC)
  - [Visual Studio Code](https://code.visualstudio.com/)

- Start Docker Desktop and keep it running in the background.

- Click the following button to setup the environment.

  [![Setup Local Dev Container](https://img.shields.io/static/v1?label=Local%20Dev%20Container&message=Setup&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/ecs36c-sq2023/hw0)

- When asked for selecting a Kit to configure CMake, choose **GCC**.

- Click **Run -> Start Debugging** to run the program.

  - project is automatically (re)built (no need to run `make` or `cmake`
    initially or after making code modifications).
  - you can supply command line args in `.vscode/launch.json` through `args`
    array.
  - you may set breakpoints by hovering over the left of each line number and
    click the red dot.

### Option 2: VS Code with CSIF

> This option provides a Graphical User Interface (GUI) for code editing and
> debugging.

> Connecting to CSIF computer may require UC Davis Library VPN.

- Install/update the following software on your local OS:

  - [Visial Studio Code](https://code.visualstudio.com/)
  - [Remote SSH Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

- Open **VS Code**

- Click the little green button in the bottom-left corner of the window to open
  **Remote - SSH** extension

- Click **Remote-SSH: Connect to Host...**

- Select **csif** if you configured
  [Passwordless Login to CSIF](https://github.com/HazyFish/ucdavis-csif-passwordless)

  - If not, in the textbox prompted, enter `username@pcXX.cs.ucdavis.edu` (you
    need to replace `username` and `XX`), press **enter**, and then enter your
    password for CSIF

- Wait for VS Code to install VS Code Server on CSIF automatically

  - VS Code Server will be installed in `/home/<username>/.vscode-server` so
    other users don't have access to it
  - Retry if you get any error

- Install **C/C++ Extension Pack** (on Remote Server)

- Open an integrated terminal inside VS Code (**Terminal Menu** -> **New
  Terminal**)

  - Notice that this terminal is already connected to the CSIF

- Run the following command inside the integrated terminal

  `git clone https://github.com/ecs36c-sq2023/hw0 ecs36c-hw0`

- Run `code ./ecs36c-hw0` to open the folder

- When prompted to configure CMake, confirm and choose **GCC** when prompted for
  kit selection.

- Click **Run -> Start Debugging** to run the program.

  - project is automatically (re)built (no need to run `make` or `cmake`
    initially or after making code modifications).
  - you can supply command line args in `.vscode/launch.json` through `args`
    array.
  - you may set breakpoints by hovering over the left of each line number and
    click the red dot.

### Option 3: Terminal with CSIF

> This option works but you will have to use print statements or command-line
> `gdb` for debugging. It is recommended that you try one of the other options
> to have more efficient, developer-friendly way of debugging.

> Connecting to CSIF computer may require UC Davis Library VPN.

- SSH into a CSIF computer

- Run the following commands

  ```bash
  git clone https://github.com/ecs36c-sq2023/hw0 ecs36c-hw0
  cd ./ecs36c-hw0
  mkdir build
  cd build
  cmake ..
  make
  ```

- To rebuild after code modification, run `make` in `build` folder.

- To run the program, run `./main [INPUT_FILE] [OUTPUT_FILE]` in `build` folder.

### Other Options

You could use other options such as running it directly on your macOS or WSL2,
but you'll be responsible for having the correct build tools and making sure
your submission works on Gradescope.

## CMakeFiles

The official description:

> CMake is an open-source, cross-platform family of tools designed to build,
> test and package software. CMake is used to control the software compilation
> process using simple platform and compiler independent configuration files,
> and generate native makefiles and workspaces that can be used in the compiler
> environment of your choice

In short: **CMake** is a very sophisticated tool for you to
build/run/test/deploy C++ programs.

CMake is:

1. Open-source - Meaning we don't have to pay to use it

2. Cross-Platform - You can run this tool on any\* operating system.

3. used to Build + Test + Package Software

Like all tools, the meaning of its existence is to allow people to use itself.
Since this course is based off of C++, taking this opportunity to learn how to
build with CMake will be great benefit to your future as a software engineer.

### CMakeLists File

For line-by-line description, refer to [CMakeLists File](./CMakeLists.txt) in
homework 0.

`CMakeLists.txt` file defines the configuration for cmake.

## CSIF Docs

Information about using CSIF computers, such as how to remotely login to CSIF
computers from home and how to copy files to/from the CSIF computers using your
personal computer, can be found at
[http://csifdocs.cs.ucdavis.edu/about-us](http://csifdocs.cs.ucdavis.edu/about-us)
csif-general-faq.
