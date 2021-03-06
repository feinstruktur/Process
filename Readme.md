# Process

[![Build Status](https://travis-ci.org/oarrabi/Process.svg?branch=master)](https://travis-ci.org/oarrabi/Process)
[![codecov](https://codecov.io/gh/oarrabi/Process/branch/master/graph/badge.svg)](https://codecov.io/gh/oarrabi/Process)
[![Platform](https://img.shields.io/badge/platform-osx-lightgrey.svg)](https://travis-ci.org/oarrabi/Process)
[![Language: Swift](https://img.shields.io/badge/language-swift-orange.svg)](https://travis-ci.org/oarrabi/Process)
[![Carthage](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)


A posix-compliant library to run external applications and capture the standard out and standard error.

## Why?

If you are developing cross platform command line apps, you need an easy way to run external applications. `Process` provides just that.

You can use `Process` with [Guaka](https://github.com/oarrabi/Process) to create aweseome command line applications.

## Usage

To execute a simple command you would do:

```swift
let result = Process.exec("ls -a -l")
print(result.stdout)
```

`result` type is `RunResults`, it contains:

- `exitStatus`: The command exit status
- `stdout`: The standard output for the command executed
- `stderr`: The standard error for the command executed

To customize the run function, you can pass in a customization block:

```swift
let result = Process.exec("ls -all") { settings in
    settings.dryRun = true
    settings.echo = [.Stdout, .Stderr, .Command]
    settings.interactive = false
}
```

`settings` is an instance of RunSettings, which contains the following variables:

- `settings.dryRun`: defaults to false. If false, the command is actually run. If true, the command is logged to the stdout paramter of result
- `settings.echo`: Customize the message printed to stdout, `echo` can contain any of the following:
    - `EchoSettings.Stdout`: The stdout returned from running the command will be printed to the terminal
    - `EchoSettings.Stderr`: The stderr returned from running the command will be printed to the terminal
    - `EchoSettings.Command`: The command executed will be printed to the terminal

## Installation
You can install Process using Swift package manager (SPM) and carthage

### Swift Package Manager
Add Process as dependency in your `Package.swift`

```
  import PackageDescription

  let package = Package(name: "YourPackage",
    dependencies: [
      .Package(url: "https://github.com/oarrabi/Process.git", majorVersion: 0),
    ]
  )
```

### Carthage
    github 'oarrabi/Process'

## Tests
Tests can be found [here](https://github.com/oarrabi/Process/tree/master/Tests).

Run them with
```
swift test
```

## Contributing

Just send a PR! We don't bite ;)
