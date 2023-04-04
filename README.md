# SDL_docker

Task: https://hackmd.io/@0x41/SDL_Docker

How to use:
1. `git clone https://github.com/UnTea/SDL_Docker`
2. `docker-compose build`
3. `docker-compose up -d`
4. Go to the cloned directory: `cd SDL_Docker`
5. In the address bar at the top, enter your search: `localhost:80`

# Docker scan before fix

``` sh
[INFO] 5 - Container Runtime
[WARN] 5.1  - Ensure AppArmor Profile is Enabled
[WARN]      * No AppArmorProfile Found: trash-web-1
[WARN]      * No AppArmorProfile Found: trash-db-1
[WARN] 5.2  - Ensure SELinux security options are set, if applicable
[WARN]      * No SecurityOptions Found: trash-web-1
[WARN]      * No SecurityOptions Found: trash-db-1
[PASS] 5.3  - Ensure Linux Kernel Capabilities are restricted within containers
[PASS] 5.4  - Ensure privileged containers are not used
[PASS] 5.5  - Ensure sensitive host system directories are not mounted on containers
[PASS] 5.6  - Ensure ssh is not run within containers
[WARN] 5.7  - Ensure privileged ports are not mapped within containers
[WARN]      * Privileged Port in use: 80 in trash-web-1
[NOTE] 5.8  - Ensure only needed ports are open on the container
[PASS] 5.9  - Ensure the host's network namespace is not shared
[WARN] 5.10  - Ensure memory usage for container is limited
[WARN]      * Container running without memory restrictions: trash-web-1
[WARN]      * Container running without memory restrictions: trash-db-1
[WARN] 5.11  - Ensure CPU priority is set appropriately on the container
[WARN]      * Container running without CPU restrictions: trash-web-1
[WARN]      * Container running without CPU restrictions: trash-db-1
[WARN] 5.12  - Ensure the container's root filesystem is mounted as read only
[WARN]      * Container running with root FS mounted R/W: trash-web-1
[WARN]      * Container running with root FS mounted R/W: trash-db-1
[WARN] 5.13  - Ensure incoming container traffic is binded to a specific host interface
[WARN]      * Port being bound to wildcard IP: 0.0.0.0 in trash-web-1
[WARN] 5.14  - Ensure 'on-failure' container restart policy is set to '5'
[WARN]      * MaximumRetryCount is not set to 5: trash-web-1
[WARN]      * MaximumRetryCount is not set to 5: trash-db-1
[PASS] 5.15  - Ensure the host's process namespace is not shared
[PASS] 5.16  - Ensure the host's IPC namespace is not shared
[PASS] 5.17  - Ensure host devices are not directly exposed to containers
[INFO] 5.18  - Ensure the default ulimit is overwritten at runtime, only if needed
[INFO]      * Container no default ulimit override: trash-web-1
[INFO]      * Container no default ulimit override: trash-db-1
[PASS] 5.19  - Ensure mount propagation mode is not set to shared
[PASS] 5.20  - Ensure the host's UTS namespace is not shared
[PASS] 5.21  - Ensure the default seccomp profile is not Disabled
[NOTE] 5.22  - Ensure docker exec commands are not used with privileged option
[NOTE] 5.23  - Ensure docker exec commands are not used with user option
[PASS] 5.24  - Ensure cgroup usage is confirmed
[WARN] 5.25  - Ensure the container is restricted from acquiring additional privileges
[WARN]      * Privileges not restricted: trash-web-1
[WARN]      * Privileges not restricted: trash-db-1
[WARN] 5.26  - Ensure container health is checked at runtime
[WARN]      * Health check not set: trash-web-1
[WARN]      * Health check not set: trash-db-1
[INFO] 5.27  - Ensure docker commands always get the latest version of the image
[WARN] 5.28  - Ensure PIDs cgroup limit is used
[WARN]      * PIDs limit not set: trash-web-1
[WARN]      * PIDs limit not set: trash-db-1
[PASS] 5.29  - Ensure Docker's default bridge docker0 is not used
[PASS] 5.30  - Ensure the host's user namespaces is not shared
[PASS] 5.31  - Ensure the Docker socket is not mounted inside any containers
```

# Docker scan after fix

``` sh
[INFO] 5 - Container Runtime
[WARN] 5.1  - Ensure AppArmor Profile is Enabled
[WARN]      * No AppArmorProfile Found: web
[WARN]      * No AppArmorProfile Found: db
[PASS] 5.2  - Ensure SELinux security options are set, if applicable
[PASS] 5.3  - Ensure Linux Kernel Capabilities are restricted within containers
[PASS] 5.4  - Ensure privileged containers are not used
[PASS] 5.5  - Ensure sensitive host system directories are not mounted on containers
[PASS] 5.6  - Ensure ssh is not run within containers
[PASS] 5.7  - Ensure privileged ports are not mapped within containers
[NOTE] 5.8  - Ensure only needed ports are open on the container
[PASS] 5.9  - Ensure the host's network namespace is not shared
[PASS] 5.10  - Ensure memory usage for container is limited
[PASS] 5.11  - Ensure CPU priority is set appropriately on the container
[WARN] 5.12  - Ensure the container's root filesystem is mounted as read only
[WARN]      * Container running with root FS mounted R/W: web
[WARN]      * Container running with root FS mounted R/W: db
[WARN] 5.13  - Ensure incoming container traffic is binded to a specific host interface
[WARN]      * Port being bound to wildcard IP: 0.0.0.0 in web
[WARN]      * Port being bound to wildcard IP: 0.0.0.0 in db
[PASS] 5.14  - Ensure 'on-failure' container restart policy is set to '5'
[WARN] 5.15  - Ensure the host's process namespace is not shared
[WARN]      * Host PID namespace being shared with: web
[WARN]      * Host PID namespace being shared with: db
[PASS] 5.16  - Ensure the host's IPC namespace is not shared
[PASS] 5.17  - Ensure host devices are not directly exposed to containers
[INFO] 5.18  - Ensure the default ulimit is overwritten at runtime, only if needed
[INFO]      * Container no default ulimit override: web
[INFO]      * Container no default ulimit override: db
[PASS] 5.19  - Ensure mount propagation mode is not set to shared
[PASS] 5.20  - Ensure the host's UTS namespace is not shared
[PASS] 5.21  - Ensure the default seccomp profile is not Disabled
[NOTE] 5.22  - Ensure docker exec commands are not used with privileged option
[NOTE] 5.23  - Ensure docker exec commands are not used with user option
[PASS] 5.24  - Ensure cgroup usage is confirmed
[WARN] 5.25  - Ensure the container is restricted from acquiring additional privileges
[WARN]      * Privileges not restricted: db
[PASS] 5.26  - Ensure container health is checked at runtime
[INFO] 5.27  - Ensure docker commands always get the latest version of the image
[WARN] 5.28  - Ensure PIDs cgroup limit is used
[WARN]      * PIDs limit not set: web
[WARN]      * PIDs limit not set: db
[PASS] 5.29  - Ensure Docker's default bridge docker0 is not used
[PASS] 5.30  - Ensure the host's user namespaces is not shared
[PASS] 5.31  - Ensure the Docker socket is not mounted inside any containers
```
