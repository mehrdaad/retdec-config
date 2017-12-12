# RetDec Configuration

A C++ library and tool for managing RetDec configuration databases.

This repository contains the following libraries:
* `retdec-config` -- library for representing and managing RetDec configuration databases.

This repository contains the following tools:
* `retdec-configtool` -- frontend for the `retdec-config` library.

## Usage Example

### RetDec-config Library

For usage examples of the RetDec-config library, see the implementation of `retdec-configtool` (in `src/retdec-configtool`) and `retdec-config` unit tests (in `tests/retdec-config`).

### RetDec-config Tool

To set an entry point value to `0x1234` in a RetDec configuration database named `test.json` run:
```
./retdec-config test.json --write --entry-point 0x1234
```

To read a file format type from a RetDec configuration database named `test.json` run:
```
./retdec-config test.json --read --format
```

Run `./retdec-config --help` to list all the available options.

## Requirements

* A compiler supporting C++14
  * On Windows, only Microsoft Visual C++ is supported (version >= Visual Studio 2015).
* CMake (version >= 3.6)

## Build and Installation

* Recursively clone the repository (it contains submodules):
  * `git clone --recursive https://github.com/avast-tl/retdec-config.git`
* Linux:
  * `cd retdec-config`
  * `mkdir build && cd build`
  * `cmake .. -DCMAKE_INSTALL_PREFIX=<path>`
  * `make && make install`
* Windows:
  * Open MSBuild command prompt, or any terminal that is configured to run the `msbuild` command.
  * `cd retdec-config`
  * `mkdir build && cd build`
  * `cmake .. -DCMAKE_INSTALL_PREFIX=<path> -G<generator>`
  * `msbuild /m /p:Configuration=Release retdec-config.sln`
  * `msbuild /m /p:Configuration=Release INSTALL.vcxproj`
  * Alternatively, you can open `retdec-config.sln` generated by `cmake` in Visual Studio IDE.

You must pass the following parameters to `cmake`:
* `-DCMAKE_INSTALL_PREFIX=<path>` to set the installation path to `<path>`.
* (Windows only) `-G<generator>` is `-G"Visual Studio 14 2015"` for 32-bit build using Visual Studio 2015, or `-G"Visual Studio 14 2015 Win64"` for 64-bit build using Visual Studio 2015. Later versions of Visual Studio may be used.

You can pass the following additional parameters to `cmake`:
* `-DRETDEC_CONFIG_DOC=ON` to build with API documentation (requires Doxygen and Graphviz, disabled by default).
* `-DRETDEC_CONFIG_TOOLS=ON` to build with tools (disabled by default).
* `-DRETDEC_CONFIG_TESTS=ON` to build with tests (disabled by default).
* `-DCMAKE_BUILD_TYPE=Debug` to build with debugging information, which is useful during development. By default, the project is built in the `Release` mode. This has no effect on Windows, but the same thing can be achieved by running `msbuild` with the `/p:Configuration=Debug` parameter.

## Library Use

### Adding RetDec-config to your project via git submodule

A single target named `retdec-config` is exposed. It can be used as follows:
```cmake
target_link_libraries(project-that-needs-retdec-config retdec-config)
```

### Using RetDec-config via CMake `find_package` command

Not supported at the moment.

## API Documentation

You can generate the API documentation by yourself. Pass `-DRETDEC_CONFIG_DOC=ON` to `cmake` and run `make doc`.

## License

Copyright (c) 2017 Avast Software, licensed under the MIT license. See the `LICENSE` file for more details.

RetDec-config uses third-party libraries or other resources listed, along with their licenses, in the `LICENSE-THIRD-PARTY` file.

## Contributing

See [RetDec contribution guidelines](https://github.com/avast-tl/retdec/wiki/Contribution-Guidelines).
