[![GitHub package.json version](https://img.shields.io/github/package-json/v/xpack-3rd-party/raspberrypi-pico-sdk-xpack)](https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack/blob/xpack/package.json)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/xpack-3rd-party/raspberrypi-pico-sdk-xpack)](https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack/tags/)
[![npm (scoped)](https://img.shields.io/npm/v/@xpack-3rd-party/raspberrypi-pico-sdk.svg?color=blue)](https://www.npmjs.com/package/@xpack-3rd-party/raspberrypi-pico-sdk/)
[![license](https://img.shields.io/github/license/xpack-3rd-party/raspberrypi-pico-sdk-xpack)](https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack/blob/xpack/LICENSE)

# An xpm/npm package with the Raspberry Pi Pico SDK

This project provides a convenient way to integrate the
[pico-sdk](https://github.com/raspberrypi/pico-sdk) library
into the xpm/npm ecosystem, by allowing to install it as a package dependency.

The open-source project is hosted on GitHub as
[xpack-3rd-party/raspberrypi-pico-sdk-xpack](https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack).

## Maintainer info

This page is addressed to developers who plan to include this source
library into their own projects.

For maintainer info, please see the
[README-MAINTAINER-XPACK](README-MAINTAINER-XPACK.md) file.

## Install

As a source code library, this project can be integrated into another project
in the traditional way,
by either copying the relevant files into the target project, or by linking
the entire project as a Git submodule.

However, things can be further automated and the most convenient way is
to **add it as a dependency** to the project via **xpm**.

### Install with xpm/npm

Along with the source files, this project also includes a
`package.json` file with the metadata that allows it to be identified as an
**xpm/npm** package so that it can be directly installed from GitHub.

#### Prerequisites

A recent [xpm](https://xpack.github.io/xpm/),
which is a portable [Node.js](https://nodejs.org/) command line application
that complements [npm](https://docs.npmjs.com)
with several extra features specific to
**C/C++ projects**.

It is recommended to install/update to the latest version with:

```sh
npm install --global xpm@latest
```

For details please follow the instructions in the
[xPack install](https://xpack.github.io/install/) page.

Warning: Be sure **xpm** is not installed with administrative rights.

#### xpm

This project can be installed as a package from GitHub with:

```sh
cd my-project
xpm init # Unless a package.json is already present

xpm install github:xpack-3rd-party/raspberrypi-pico-sdk-xpack#v1.5.1-1 --save-dev --copy

ls -l xpacks/@xpack-3rd-party/raspberrypi-pico-sdk
```

#### npm

The package can also be installed with [npm](https://docs.npmjs.com)
or related, but
the features specific to C/C++ projects will not be available;
therefore, at least for consistency reasons, it is recommended
to use **xpm**.

### Add as a Git submodule

Besides manually copying the relevant files to the target
project, which will later require extra maintenance efforts to keep the
project up to date, a more convenient
solution is to link the entire project as a **Git submodule**,
for example below an `xpacks` folder:

```sh
cd my-project
git init # Unless already a Git project
mkdir -p xpacks

git submodule add https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack.git \
  xpacks/@xpack-3rd-party/raspberrypi-pico-sdk
```

## Branches

In addition to the original `main` branch, there are two
xPack specific branches:

- `xpack`, with the latest stable version (default)
- `xpack-develop`, with the current development version

All development is done in the `xpack-develop` branch, and contributions via
Pull Requests should be directed to this branch.

When new releases are published, the `xpack-develop` branch is merged
into `xpack`.

When there are new upstream releases:

- upstream `master` is merged into the local `master`
- the local `master` is merged into `xpack-develop`
- the project is tested
- `xpack-develop` is merged into `xpack`

### Status

The **xpack-3rd-party/raspberrypi-pico-sdk** package is fully functional.

The original README follows.

---

# Raspberry Pi Pico SDK

The Raspberry Pi Pico SDK (henceforth the SDK) provides the headers, libraries and build system
necessary to write programs for the RP2040-based devices such as the Raspberry Pi Pico
in C, C++ or assembly language.

The SDK is designed to provide an API and programming environment that is familiar both to non-embedded C developers and embedded C developers alike.
A single program runs on the device at a time and starts with a conventional `main()` method. Standard C/C++ libraries are supported along with
C level libraries/APIs for accessing all of the RP2040's hardware include PIO (Programmable IO).

Additionally the SDK provides higher level libraries for dealing with timers, synchronization, USB (TinyUSB) and multi-core programming
along with various utilities.

The SDK can be used to build anything from simple applications, to fully fledged runtime environments such as MicroPython, to low level software
such as RP2040's on-chip bootrom itself.

Additional libraries/APIs that are not yet ready for inclusion in the SDK can be found in [pico-extras](https://github.com/raspberrypi/pico-extras).

# Documentation

See [Getting Started with the Raspberry Pi Pico](https://rptl.io/pico-get-started) for information on how to setup your
hardware, IDE/environment and for how to build and debug software for the Raspberry Pi Pico
and other RP2040-based devices.

See [Connecting to the Internet with Raspberry Pi Pico W](https://rptl.io/picow-connect) to learn more about writing
applications for your Raspberry Pi Pico W that connect to the internet.

See [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk) to learn more about programming using the
SDK, to explore more advanced features, and for complete PDF-based API documentation.

See [Online Raspberry Pi Pico SDK API docs](https://rptl.io/pico-doxygen) for HTML-based API documentation.

# Example code

See [pico-examples](https://github.com/raspberrypi/pico-examples) for example code you can build.

# Getting the latest SDK code

The [master](https://github.com/raspberrypi/pico-sdk/tree/master/) branch of `pico-sdk` on GitHub contains the
_latest stable release_ of the SDK. If you need or want to test upcoming features, you can try the
[develop](https://github.com/raspberrypi/pico-sdk/tree/develop/) branch instead.

# Quick-start your own project

These instructions are extremely terse, and Linux-based only. For detailed steps,
instructions for other platforms, and just in general, we recommend you see [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk)

1. Install CMake (at least version 3.13), and GCC cross compiler
   ```
   sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib
   ```
1. Set up your project to point to use the Raspberry Pi Pico SDK

   * Either by cloning the SDK locally (most common) :
      1. `git clone` this Raspberry Pi Pico SDK repository
      1. Copy [pico_sdk_import.cmake](https://github.com/raspberrypi/pico-sdk/blob/master/external/pico_sdk_import.cmake)
         from the SDK into your project directory
      2. Set `PICO_SDK_PATH` to the SDK location in your environment, or pass it (`-DPICO_SDK_PATH=`) to cmake later.
      3. Setup a `CMakeLists.txt` like:

          ```cmake
          cmake_minimum_required(VERSION 3.13)

          # initialize the SDK based on PICO_SDK_PATH
          # note: this must happen before project()
          include(pico_sdk_import.cmake)

          project(my_project)

          # initialize the Raspberry Pi Pico SDK
          pico_sdk_init()

          # rest of your project

          ```

   * Or with the Raspberry Pi Pico SDK as a submodule :
      1. Clone the SDK as a submodule called `pico-sdk`
      1. Setup a `CMakeLists.txt` like:

          ```cmake
          cmake_minimum_required(VERSION 3.13)

          # initialize pico-sdk from submodule
          # note: this must happen before project()
          include(pico-sdk/pico_sdk_init.cmake)

          project(my_project)

          # initialize the Raspberry Pi Pico SDK
          pico_sdk_init()

          # rest of your project

          ```

   * Or with automatic download from GitHub :
      1. Copy [pico_sdk_import.cmake](https://github.com/raspberrypi/pico-sdk/blob/master/external/pico_sdk_import.cmake)
         from the SDK into your project directory
      1. Setup a `CMakeLists.txt` like:

          ```cmake
          cmake_minimum_required(VERSION 3.13)

          # initialize pico-sdk from GIT
          # (note this can come from environment, CMake cache etc)
          set(PICO_SDK_FETCH_FROM_GIT on)

          # pico_sdk_import.cmake is a single file copied from this SDK
          # note: this must happen before project()
          include(pico_sdk_import.cmake)

          project(my_project)

          # initialize the Raspberry Pi Pico SDK
          pico_sdk_init()

          # rest of your project

          ```

   * Or by cloning the SDK locally, but without copying `pico_sdk_import.cmake`:
       1. `git clone` this Raspberry Pi Pico SDK repository
       2. Setup a `CMakeLists.txt` like:

           ```cmake
           cmake_minimum_required(VERSION 3.13)

           # initialize the SDK directly
           include(/path/to/pico-sdk/pico_sdk_init.cmake)

           project(my_project)

           # initialize the Raspberry Pi Pico SDK
           pico_sdk_init()

           # rest of your project

           ```
1. Write your code (see [pico-examples](https://github.com/raspberrypi/pico-examples) or the [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk) documentation for more information)

   About the simplest you can do is a single source file (e.g. hello_world.c)

   ```c
   #include <stdio.h>
   #include "pico/stdlib.h"

   int main() {
       setup_default_uart();
       printf("Hello, world!\n");
       return 0;
   }
   ```
   And add the following to your `CMakeLists.txt`:

   ```cmake
   add_executable(hello_world
       hello_world.c
   )

   # Add pico_stdlib library which aggregates commonly used features
   target_link_libraries(hello_world pico_stdlib)

   # create map/bin/hex/uf2 file in addition to ELF.
   pico_add_extra_outputs(hello_world)
   ```

   Note this example uses the default UART for _stdout_;
   if you want to use the default USB see the [hello-usb](https://github.com/raspberrypi/pico-examples/tree/master/hello_world/usb) example.

1. Setup a CMake build directory.
      For example, if not using an IDE:
      ```
      $ mkdir build
      $ cd build
      $ cmake ..
      ```

   When building for a board other than the Raspberry Pi Pico, you should pass `-DPICO_BOARD=board_name` to the `cmake` command above, e.g. `cmake -DPICO_BOARD=pico_w ..`
   to configure the SDK and build options accordingly for that particular board.

   Doing so sets up various compiler defines (e.g. default pin numbers for UART and other hardware) and in certain
   cases also enables the use of additional libraries (e.g. wireless support when building for `PICO_BOARD=pico_w`) which cannot
   be built without a board which provides the requisite functionality.

   For a list of boards defined in the SDK itself, look in [this directory](src/boards/include/boards) which has a
   header for each named board.

1. Make your target from the build directory you created.
      ```sh
      $ make hello_world
      ```

1. You now have `hello_world.elf` to load via a debugger, or `hello_world.uf2` that can be installed and run on your Raspberry Pi Pico via drag and drop.
