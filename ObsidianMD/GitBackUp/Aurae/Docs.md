
Fosdem slides :
https://docs.google.com/presentation/d/1GxKN5tyv4lV2aZdEOUqy3R9tVCat-vrFJyelgFX7b1A/edit#slide=id.g1eec0a22ec6_0_4 

Group :
https://chat.fosdem.org/#/home

Crates.io :: https://crates.io/crates/aurae/versions
![[aurae CRATES.IO 20240125194416.png]]
## aer :: CLI
type command and it runs against the server

  

// An **Aurae cell** is a name given to Linux control groups (**cgroups**) that also
// includes a name, and special pre-exec functionality that is executed from
// within the same context as any executables scheduled.
// A cell must be allocated for every executable scheduled. A cell defines the resource constraints of the system to allocate for an arbitrary use case.

## api/cells/cells.proto
Isolation :
174 // Default: false
bool isolate_process = 10;
*the value `10` is associated with the field, not the strength of isolation*
// Will isolate the process (and proc filesystem) from the host.
// Will unshare the pid, ipc, uts, and mount namespaces.
// The cgroup namespace is always unshared with the host.
//

