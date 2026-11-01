---
title: "networkinfo typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["InterfaceAddressInfo", "NetworkInfoLinuxInterfaceAddress", "NetworkInfoLinuxNativeIfaddrs"]
dependencies: []
symbols: ["InterfaceAddressInfo", "NetworkInfoLinuxInterfaceAddress", "NetworkInfoLinuxNativeIfaddrs"]
related: ["api.md", "getting-started.md", "index.md"]
---

# networkinfo typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## InterfaceAddressInfo

`Public Class InterfaceAddressInfo`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `InterfaceName` | `String` | Yes | No | — | — |
| `Family` | `String` | Yes | No | — | — |
| `NativeFamily` | `Integer` | Yes | No | — | — |
| `Address` | `String` | Yes | No | — | — |
| `Netmask` | `Optional Of String` | Yes | No | — | — |
| `ScopeId` | `Integer` | Yes | No | — | — |
| `NativeFlags` | `Integer` | Yes | No | — | — |
| `IsUp` | `Boolean` | Yes | No | — | — |
| `IsLoopback` | `Boolean` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(vInterfaceName As String, vFamily As String, vNativeFamily As Integer, vAddress As String, vNetmask As Optional Of String, vScopeId As Integer, vNativeFlags As Integer, vIsUp As Boolean, vIsLoopback As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `vInterfaceName` | `String` | `ByVal` | Required |
| `vFamily` | `String` | `ByVal` | Required |
| `vNativeFamily` | `Integer` | `ByVal` | Required |
| `vAddress` | `String` | `ByVal` | Required |
| `vNetmask` | `Optional Of String` | `ByVal` | Required |
| `vScopeId` | `Integer` | `ByVal` | Required |
| `vNativeFlags` | `Integer` | `ByVal` | Required |
| `vIsUp` | `Boolean` | `ByVal` | Required |
| `vIsLoopback` | `Boolean` | `ByVal` | Required |

Returns: no value.

## NetworkInfo functions

### InterfaceAddressesSupported

`Public Function InterfaceAddressesSupported() As Boolean`

Read-only compile-target backend test; no runtime I/O.

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### InterfaceAddressesAvailable

`Public Function InterfaceAddressesAvailable() As Boolean`

Read-only libc library probe; no interface enumeration or connectivity test.

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### InterfaceAddresses

`Public Function InterfaceAddresses() As Array Of InterfaceAddressInfo`

Read-only; every IPv4/IPv6 address in this network namespace, with IPv6 scope. No DNS, route or connectivity claim.

No parameters.

#### Returns

| Type |
| --- |
| `Array Of InterfaceAddressInfo` |

## NetworkInfoLinuxInterfaceAddress

`Public Class NetworkInfoLinuxInterfaceAddress`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Name` | `String` | No | No | — | — |
| `Family` | `Integer` | No | No | — | — |
| `Address` | `String` | No | No | — | — |
| `Netmask` | `Optional Of String` | No | No | — | — |
| `ScopeId` | `Integer` | No | No | — | — |
| `Flags` | `UInt32` | No | No | — | — |
| `IsUp` | `Boolean` | No | No | — | — |
| `IsLoopback` | `Boolean` | No | No | — | — |

## NetworkInfoLinuxNativeIfaddrs

`Sequential Structure NetworkInfoLinuxNativeIfaddrs`

### Fields

| Name | Type | Value / Default | Description |
| --- | --- | --- | --- |
| `NextEntry` | `Ptr` | — | — |
| `Name` | `Ptr` | — | — |
| `Flags` | `UInt32` | — | — |
| `Address` | `Ptr` | — | — |
| `Netmask` | `Ptr` | — | — |
| `BroadcastOrDestination` | `Ptr` | — | — |
| `Data` | `Ptr` | — | — |

## NetworkInfoLinuxBackend functions

### NetworkInfoLinuxIsSupported

`Public Function NetworkInfoLinuxIsSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### NetworkInfoLinuxInterfaceAddresses

`Public Function NetworkInfoLinuxInterfaceAddresses() As Array Of NetworkInfoLinuxInterfaceAddress`

One record per IPv4/IPv6 address in this process's network namespace.

No parameters.

#### Returns

| Type |
| --- |
| `Array Of NetworkInfoLinuxInterfaceAddress` |
