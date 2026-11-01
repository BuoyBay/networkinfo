# Discover native network interface addresses and scope IDs

Import `networkinfo` (or `networkinfo.NetworkInfo`). This focused package owns `InterfaceAddressesSupported()`, `InterfaceAddressesAvailable()` and `InterfaceAddresses() As Array Of InterfaceAddressInfo`. It has no package, container, or external source dependency. Backend modules are implementation details and are non-public imports; their module-scope symbols are globally prefixed to avoid collisions.

Enumeration is read-only. Empty arrays mean successful enumeration with no results; missing services/libraries, denied access and native errors throw. Missing optional fields are None, present empty strings are Some(""). No absent numeric or powered state is fabricated as zero/False. Snapshot properties are read-only owned copies. Native IDs are observations in their backend namespace, not cross-platform stable identities or openable handles.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add networkinfo --git https://github.com/BuoyBay/networkinfo.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## API entrypoints

- `InterfaceAddressesSupported()`
- `InterfaceAddressesAvailable()`
- `InterfaceAddresses() As Array Of InterfaceAddressInfo`

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer networkinfo
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

The generated agent files and editor settings stay local and are ignored by Git.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
