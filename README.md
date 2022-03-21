# A source library xPack with the Raspberry Pi Pico SDK

The project is hosted on GitHub as
[xpack-3rd-party/raspberrypi-pico-sdk-xpack](https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack).

## Maintainer info

This page is addressed to developers who plan to include this source
library into their own projects.

For maintainer info, please see the
[README-MAINTAINER](README-MAINTAINER.md) file.

## Install

As a source library xPacks, the easiest way to add it to a project is via
**xpm**, but it can also be used as any Git project, for example as a submodule.

### Prerequisites

A recent [xpm](https://xpack.github.io/xpm/),
which is a portable [Node.js](https://nodejs.org/) command line application.

For details please follow the instructions in the
[install](https://xpack.github.io/install/) page.

### xpm

Note: the package will be available from npmjs.com at a later date.

For now, it can be installed from GitHub:

```console
$ cd <project>
$ xpm init # Unless a package.json is already present

$ xpm install github:xpack-3rd-party/raspberrypi-pico-sdk-xpack
```

When ready, this package will be available as
[`@xpack-raspberrypi/pico-sdk`](https://www.npmjs.com/package/@xpack-raspberrypi/pico-sdk)
from the `npmjs.com` registry:

```console
$ cd <project>
$ xpm init # Unless a package.json is already present

$ xpm install @xpack-raspberrypi/pico-sdk@latest

ls -l xpacks/xpack-raspberrypi-pico-sdk
```

### Git submodule

If, for any reason, **xpm** is not available, the next recommended
solution is to link it as a Git submodule below an `xpacks` folder.

```console
$ cd <project>
$ git init # Unless already a Git project
$ mkdir -p xpacks

$ git submodule add https://github.com/xpack-3rd-party/raspberrypi-pico-sdk-xpack.git \
  xpacks/xpack-3rd-party-raspberrypi-pico-sdk
```

## Branches

Apart from the unused `master` branch, there are two active branches:

- `xpack`, with the latest stable version
- `xpack-develop`, with the current development version

All development is done in the `xpack-develop` branch, and contributions via
Pull Requests should be directed to this branch.

When new releases are published, the `xpack-develop` branch is merged
into `xpack`.

## User info

TBD

### Status

The ... are fully functional.

### Limitations

TBD

### Build & integration info

To include this package in a project, consider the following details.

#### Source folders

TBD

#### Include folders

TODO: list all header files.

#### Preprocessor definitions

TBD

#### Compiler options

TBD
#### C++ Namespaces

TBD

#### C++ Classes

TBD

### Examples

TBD

### Known problems

- none

### Tests

TBD

---

# Original Raspberry Pi README

The Raspberry Pi Pico SDK (henceforth the SDK) provides the headers, libraries and build system
necessary to write programs for the RP2040-based devices such as the Raspberry Pi Pico
in C, C++ or assembly language.

The SDK  is designed to provide an API and programming environment that is familiar both to non-embedded C developers and embedded C developers alike.
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

See [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk) to learn more about programming using the
SDK, to explore more advanced features, and for complete PDF-based API documentation.

See [Online Raspberry Pi Pico SDK API docs](https://rptl.io/pico-doxygen) for HTML-based API documentation.

# Example code

See [pico-examples](https://github.com/raspberrypi/pico-examples) for example code you can build.

# Quick-start your own project

These instructions are extremely terse, and Linux-based only. For detailed steps,
instructions for other platforms, and just in general, we recommend you see [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk)

1. Install CMake (at least version 3.13), and GCC cross compiler
   ```
   sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi
   ```
1. Set up your project to point to use the Raspberry Pi Pico SDK

   * By cloning the SDK locally (most common)
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

   * With the Raspberry Pi Pico SDK as a submodule
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

   * With automatic download from github
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

3. Setup a CMake build directory.
      For example, if not using an IDE:
      ```
      $ mkdir build
      $ cd build
      $ cmake ..
      ```

4. Write your code (see [pico-examples](https://github.com/raspberrypi/pico-examples) or the [Raspberry Pi Pico C/C++ SDK](https://rptl.io/pico-c-sdk) documentation
for more information)

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


5. Make your target from the build directory you created.
      ```sh
      $ make hello_world
      ```

6. You now have `hello_world.elf` to load via a debugger, or `hello_world.uf2` that can be installed and
run on your Raspberry Pi Pico via drag and drop.
