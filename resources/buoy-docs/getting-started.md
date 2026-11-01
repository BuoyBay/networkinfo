---
title: "Getting started with networkinfo"
summary: "Import networkinfo, check platform availability, and handle results and failures."
category: "Guide"
order: 10
keywords: ["networkinfo", "NetworkInfo", "native", "discovery"]
symbols: ["InterfaceAddressInfo", "InterfaceAddresses", "InterfaceAddressesSupported", "InterfaceAddressesAvailable"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Install `networkinfo` into your project’s packages directory with your package workflow, then import `networkinfo`. Use the NetworkInfo facade instead of importing platform backend modules.

Use `System.GetNetworkInterfaces()` for ordinary interface summaries. When you need multiple addresses or IPv6 scope, check `InterfaceAddressesSupported()` and `InterfaceAddressesAvailable()`, then call `InterfaceAddresses()` with exception handling. Group the `Array Of InterfaceAddressInfo` by `InterfaceName` when showing interfaces with multiple addresses.

The result is an address inventory, not a complete interface inventory. Interfaces with no address, or only address families other than IPv4 and IPv6, contribute no records. An interface missing from these results has not necessarily disappeared; use `System.GetNetworkInterfaces()` for ordinary interface summaries rather than treating an empty address list as proof that no interfaces exist.

## Handling availability

A Supported predicate describes the compile target. An Available predicate probes runtime prerequisites; it does not guarantee that the next operation will succeed. Preserve the distinction between successful empty results and an exception. Consult the [API contracts](api.md) for supported platforms, blocking behavior, and lifecycle requirements.

The [typed reference](typed-api.md) lists argument types, defaults, read-only properties, and return values. It also includes declarations from internal backend source modules; applications should use the facade entry points described here.
