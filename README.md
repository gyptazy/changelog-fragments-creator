# Changelog Fragments Creator

<img align="left" src="https://gyptazy.ch/wp-content/uploads/2023/07/changelog-fragments-creator.jpg"/>
<br>

<p float="center"><img src="https://img.shields.io/github/license/gyptazy/changelog-fragments-creator"/><img src="https://img.shields.io/github/contributors/gyptazy/changelog-fragments-creator"/><img src="https://img.shields.io/github/last-commit/gyptazy/changelog-fragments-creator/main"/><img src="https://img.shields.io/github/issues-raw/gyptazy/changelog-fragments-creator"/><img src="https://img.shields.io/github/issues-pr/gyptazy/changelog-fragments-creator"/></p>


## Table of Content
* General
* Structure
  * General
  * Overview
  * Details
    * Changelog Meta Information
    * Changelog Fragments
* Usage
  * Parameters
  * Supported Systems
  * Dependencies
  * How to Use
  * Quick Start
* Motivation
* Misc
  * Bugs
  * Contributing
  * Author(s)

## General
`Changelog Fragments Creator` may be used in development setups where working on a single `CHANGELOG.md` file might result in ongoing merge conflicts due to too many changes on the same file. This is where `Changelog Fragments Creator` steps in to solve this by creating `YAML` based files for each PR according to its planned release version.

The output format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Structure
### General
The file structure is easy and simple for developing with several developers at the same time even when supporting multiple releases at the same time. Next to this, changes are easy to cherry-pick. Therefore, no worries about ongoing backports etc.

### Overview
```
    └── changelog-fragments
        ├── 0.9
        │   ├── 123_initial_build.yaml
        │   ├── 124_remove_dependency.yaml
        │   └── release_meta.yml
        ├── 1.0
        │   ├── 487_initial_stable_release.yml
        │   └── release_meta.yml
        ├── 1.11
```

### Details
Within the previously mentioned overview you can already see, that there is just a single directory containing all release versions. This may be older, current and also upcoming release. Therefore, there is not any `Unreleased` chapter. However, if you like you can still create one and it is honored, but you may also directly set the files according to the planned release version.

As a result we have a directory with sub-directories representing their release version:
```
   └── changelog-fragments
        ├── 0.9
        ├── 1.0
        ├── 1.11
        ├── 1.11b
        ├── 1.12
        ├── 12.0.3
```

#### Changelog Meta Information
Within each of this directories a single `release_meta.yml` file in `YAML` syntax is needed which contains the meta information for the according release version. This also includes the release date. A minimal version looks like:
```
date: 2023-07-20
description: Initial release
```

#### Changelog Fragments
The changelog fragments represent a single line within generic changelog and are also simple to create. Each fragment is written in a `YAML` syntax and should represent the following naming convention:
```
VAR:
$PR_$description.yml
Example:
0001_adjusting_docs.yml
```
However, this is just a convention and different names schemas may also work. By default, the file extensions must be `.yml` or `.yaml` but other ones may be optionally included (see also parameters section). 

The content of this file is the most important and will be integrated within the final changelog file. The structure for this file is also small and easy. For example it might look like:
```
removed:
  - Removed unneeded dependencies [#124]
```

Of course, this may also be extended and include multiple actions as keys like:
```
removed:
  - Removed unneeded dependencies [#124]
  - Removed development test file [#124]
fixed:
  - Changed to new layout structure [#487]
```

According to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) the following states/actions are usable:
* Added
* Changed
* Deprecated
* Removed
* Fixed
* Security

## Usage
### Parameters
The following options and parameters are currently supported:

| Option | Long Option | Description |
|------|:------:|------:|
| -f | --fragments-path | Path to changelog fragments where all release versions are present |
| -o | --output-path | Path (including name) where to write changelog file (default: ./CHANGELOG.md) |
| -c | --custom-fragments-extension | Add custom changelog fragment extensions (default: .yml, .yaml) |
| -s | --skip-tbd | Option to skip adding releases which are in draft but already have changelog fragments |

### Supported Systems
The goal is to support as many platforms and systems as possible which only needs a small Python environment without any further custom imports. Therefore, this is supported to run on:
* Linux
* BSD (FreeBSD, NETBSD, OpenBSD)
* macOS (OSX)
* Windows

### Dependencies
This changelog creator is written for minimal setups to be usable across almost all systems (platforms and distributions). Therefore, some dirty stunts were needed to avoid templating (jinja2), etc. to drop some imports that would require additional dependencies. It only requires a basic Python 3 installation on the system.

### How to Use
This tool is easy to use and just needs the path to the changelog fragments. By checking out, a valid structure is already given as an example and can be validated by simply running:
```
./changelog-creator -f example/changelog-fragments
```

## Motivation
This project has been created after a some frustrations in several projects where working with several developers on the same project with a higher count of pull requests lead into ongoing merge conflicts on the same file. On and on resolving these merge conflicts resulted in writing this small and handy tool which is included within the release pipeline and creates the needed changelog file.

## Misc
### Bugs
Bugs can be reported via the GitHub issue tracker at FIXME. You may also report bugs via email or deliver PRs to fix them on your own. Therefore, you might also see the contributing chapter.

### Contributing
Feel free to add further documentation, to adjust already existing one or to contribute with code. Please take care about the style guide and naming conventions.

### Author(s)
 * Florian Paul Azim Hoberg @gyptazy
