[[_ intro Python Docker]]
[[4 - Docker containers Basics]]
[[4 How to access an App in a Container?]]
[[4 Application Design Patterns]]



---
# How Containers Store Data?

Each container has its own dedicated and isolated file system.

Docker create this file system automatically (no snapshot, backup).

## Bind Mount
![[docker_bind_mount.excalidraw|700]]
in development processes not in production

---

## Volume Mount
![[docker Volume Mount.excalidraw|700]]

==volume== 
- independent storage entity
- contains a filesystem
- can be mounted to a mountpoint to a container
- save all data, (nawet gdy) container stopped to exists

__Docker has no direct way to mount a volume to a host machine__
Google, AWS provide some entites as a volumes to a container



