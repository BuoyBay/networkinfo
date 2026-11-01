---
title: "networkinfo API contracts"
summary: "Platform support, result semantics, and operational constraints for networkinfo."
category: "Reference"
order: 20
keywords: ["networkinfo", "NetworkInfo", "native", "discovery"]
symbols: ["InterfaceAddressInfo", "InterfaceAddresses", "InterfaceAddressesSupported", "InterfaceAddressesAvailable"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# networkinfo API contracts

## Platform support

Linux uses `getifaddrs` and `inet_ntop`. Windows and macOS are unsupported. `InterfaceAddressesSupported()` tests the compile target without I/O. `InterfaceAddressesAvailable()` probes libc without enumerating interfaces or testing connectivity.

## Address records

Each `InterfaceAddressInfo` is a read-only owned snapshot of one address. Multiple records can belong to the same interface.

| Property | Meaning |
| --- | --- |
| InterfaceName | Native interface name |
| Family | ipv4 or ipv6 |
| NativeFamily | Native address-family number, 2 or 10 on this Linux backend |
| Address | Numeric address text |
| Netmask | Optional numeric netmask text |
| ScopeId | IPv6 scope; zero is the native no-scope value |
| NativeFlags | Native interface flags |
| IsUp, IsLoopback | Native flag-derived booleans |

Keep `ScopeId` with an IPv6 address when identifying a scoped address. A missing `Netmask` is `None`, distinct from a present empty string. Names and flags describe the current network namespace; they are not a permanent global network identity.

## Results and errors

An empty array means successful enumeration with no applicable addresses. Native errors throw; unsupported-target enumeration throws `UnsupportedOperationException`. Interface state and an assigned address do not prove internet connectivity. This package does not perform DNS lookup, inspect routes, or send network traffic.

[Full typed reference](typed-api.md) · [Getting started](getting-started.md)
