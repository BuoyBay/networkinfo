# networkinfo

Import `networkinfo` (or `networkinfo.NetworkInfo`). This focused package owns `InterfaceAddressesSupported()`, `InterfaceAddressesAvailable()` and `InterfaceAddresses() As Array Of InterfaceAddressInfo`. It has no package, container, or external source dependency. Backend modules are implementation details and are non-public imports; their module-scope symbols are globally prefixed to avoid collisions.

Linux getifaddrs and inet_ntop only. Windows and macOS are explicitly unsupported. Supported is a compile-target statement, not a runtime verification claim. Availability is a probe, not a promise that enumeration will succeed: Linux libc library probe; no enumeration or connectivity checks.

Enumeration is read-only. Empty arrays mean successful enumeration with no results; missing services/libraries, denied access and native errors throw. Missing optional fields are None, present empty strings are Some(""). No absent numeric or powered state is fabricated as zero/False. Snapshot properties are read-only owned copies. Native IDs are observations in their backend namespace, not cross-platform stable identities or openable handles.

Adapter mapping: linuxnetwork.InterfaceAddresses → InterfaceAddresses; InterfaceAddress → InterfaceAddressInfo. Name → InterfaceName; native family 2/10 → ipv4/ipv6 plus NativeFamily; Flags → NativeFlags; address/netmask/scope/up/loopback preserved. Legacy entry modules are unchanged; no forwarding adapter is installed by this change.

Builder registration: name `networkinfo`, source `libraries/networkinfo`, version `0.1.0`, output `networkinfo-0.1.0.buipkg`. All six desktop triples are in the manifest so unsupported-target predicates can be imported; this does not claim an implemented backend on each target. Build with the native package builder described in
[CONTRIBUTING](https://github.com/BuoyBay/networkinfo/blob/main/CONTRIBUTING.md).

Supported operations can fail when hardware, services or access are absent; callers must handle those errors. Cross-target compiler checks do not establish native backend behavior.

This fills only the multiple-address/IPv6-scope gap in System.GetNetworkInterfaces(). Use that built-in for ordinary interface summaries. There is no DNS, route, connectivity, or global network identity API here. ScopeId zero is the native no-scope value, not an absent-field sentinel.
