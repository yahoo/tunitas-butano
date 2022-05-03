# Tunitas Butano

This repository contains library components which implement the Interactive Advertising Bureau's (IAB) [Transparency and Consent Framework (TCF)](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework).  The project also provides some simple command-line utilities which are useful for constructing, decoding and displaying TCF strings.

The main body of documentation for the Tunitas family of components and services can be found with the [packaging](https://github.com/yahoo/tunitas-packaging) and with [build system](https://github.com/yahoo/temerarious-flagship]).  The overview and administrative declarations herein are necessarily summary in nature. The declarations and definitions in the packaging and build system areas are complete and should be interpreted as superceding these when the two are in conflict.

Current work with modern-generation tooling, <em>e.g.</em> circa Fedora 36+ and GCC 12+, is occurring around the <em>v2-themed</em> feature branches.
## Table of Contents

- [Background](#background)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Build](#build)
- [Usage](#usage)
- [Components](#compoonents)
- [Security](#security)
- [References](#references)
- [Contribute](#contribute)
- [License](#license)
- [Origin of the Name](#Origin_of_the_name)

[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

## Background

The Butano components are members of the Tunitas family of components and services. These components depends upon the the other core components of the Tunitas family.  These are:
  * [Tunitas Basics](https://github.com/yahoo/tunitas-basics) package for core components.
  * [Temerarious Flagship](https://github.com/yahoo/temerarious-flagship), the build system

## Dependencies

The [configuration](#configuration) step will check for many but not all required packages and operating system features.  There is a list of known [package-dependencies](https://github.com/yahoo/tunitas-butano/blob/master/PACKAGES.md) which you will need to install beyond your base operating system.

Generally, the dependencies are among:
- Certain other components of the Tunitas system; <em>e.g.</em> the [Basic Components](https://github.com/yahoo/tunitas-basic).
- A modern (C++2a) development environment.
- A recent Fedora, but any recent Linux distro should suffice.

The Tunitas project was developed on Fedora 27 through Fedora 30 using GCC 7 and GCC 8 with `-fconcepts` and at least `-std=c++1z`.  More details on the development environment and the build system can be found in [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/README.md).

## Installation

You may install this repo and its dependents by running the following command:

``` bash
git clone https://github.com/yahoo/tunitas-butano.git
```

This will create a directory called `tunitas-butano` and download the contents of this repo to it.

Alternatively, if your organization already has made available the packaged version, then the following recipe will install the service:

``` bash
sudo dnf install tunitas-butano
```

## Configuration

The build system is based upon [GNU Autotools](https://www.gnu.org/software/automake/manual/html_node/index.html).

The configuration of the repo consists of two steps which must be done once.
1. `./buildconf`
2. `./configure`

The first step performs some crude assessments of the build environment and creates the site-specific `configure'. Of course `configure --help` will explain the build options.  The general options to `configure` are widely [documented](https://www.gnu.org/prep/standards/html_node/Configuration.html).

The `buildconf` component is boilerplate and can be updated from [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/bc/template.autotools-buildconf) as needed.  The [Tunitas Build System](https://github.com/yahoo/temerarious-flagship) should be available in `/opt/tunitas` and the template at `/opt/tunitas/share/temerarious-flagship/bc/template.autotools-buildconf`

## Build

The project can be built with the following recipe:

``` bash
./buildconf &&
./configure &&
make &&
make check &&
make install &&
echo OK DONE
```

## Usage

The Butano repo produces components for a modern C++ development and runtime (specifically, C++2a).  These artifacts are at least: shared and static libraries, [modules](https://github.com/cplusplus/modules-ts) and "header files" containing declarations and (inline) definitions.  The stylistic and coding conventions of the Tunitas family of components is described in the documentation for the common build system used across the project, [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/README.md#References).

## Components

The major components of Tunitas Butano are outlined:

### Development Components (Libraries)

- `libtunitas-butano.la`, common TCF operations
- `libtunitas-butano-tcf.la`, the manipulations of TCF String and Objects.
- `libtunitas-butano-generation.la`, the generation of arbitrary of TCF String and Objects.

### Command Line Tools

Debugging
* `dump-iab` provides a report on the contents of a TCF string.
* `random-iab` produces a random TCF string.
* `vanity-iab` produces a vanity TCF string containing a particular message.

Testing
* `dump-base64`, does just that.
* `random-base64`, produces random base64-encoded string data.

## Security

This repo has no specific security concerns.  The implementation made available herein provides support for the IAB's TCF in the form of library components.  Those library components manipulate string representations constitute a data subject's (a person's) consent choices.  The components are expected to be made available in the form of a service offering such as [Apanolio](https://github.com/yahoo/tunitas-apanolio), [Montara](https://github.com/yahoo/tunitas-montara), [Rockaway](https://github.com/yahoo/tunitas-rockaway) or [Tarwater](https://github.com/yahoo/tunitas-tarwater).

## Contribute

Please refer to [the contributing.md file](Contributing.md) for information about how to get involved. We welcome issues, questions, and pull requests. Pull Requests are welcome.

## Maintainers
- Wendell Baker <wbaker@yahooinc.com>
- The Tunitas Team at Yahoo.

You may contact us at least at <tunitas@yahooinc.com>

## License

This project is licensed under the terms of the [Apache 2.0](LICENSE-Apache-2.0) open source license. Please refer to [LICENSE](LICENSE) for the full terms.

## Origin of the Name

The project is named after [Butano Creek](https://en.wikipedia.org/wiki/Butano_Creek), in San Mateo County, California.  There is a mountain and a state beach which carry the name. [Wikipedia](https://en.wikipedia.org/wiki/Butano,_California).
