### Introducing Kubernetes

Kube provides the shift from managing individual apps to just managing Kube (pg. 2) </br>

Multiple apps running on the same host can contain conflicting deps (pg 5.)

"By abstracting away the actual hardware and exposing it as a single platform for deployig and running apps, it allows developers to configure and deploy their applications without any help from the sysadmins and allows the sysadmins to focus on keeping the underlying infrastructure up and running, while not having to know anything about the actual applications running on top of it." (pg 7.)

"...the process in the container is still isolated from other processes.  To the process itself, it looks like it's the only one running on the machine and in its operating system. (pg. 8)

Containers are more lightweight than vms. (pg. 8)

"...each VM runs its own set of syste services, while containers don't, because they all run in the same OS...A process run in a container starts up immediately" (pg. 10)

LInux Namespaces - makes sure each process sees it's own personal view of the file system
Linux Control Groups (cgroups)  - limit the amount of resources a process can consume. (pg. 11)

mnt/pid/net/ipc/UTS/user (kinds of namespaces) (pg. 11)

"Each container uses its own Network namespace, and therefore each container sees its own set of network interfaces." (pg. 11)

Docker - Images (what you package your app into) registries (stores the image), and containers
 (container running on the host running Docker) (pg. 13)

Image Layers - Every Docker image is built on top of another image.  Each layer is only stored once. (pg. 15)

If a machine runs a different version of the Linux kernel or doesn't have the same kernel modules available, app can't run on it (pg. 15)

Kube exposes the whole datacenter as a single deployment platform (pg. 17)

You can think of Kube as an OS for the cluster

Nodes - Kube is consisted of master node (hosts the Kube ontrol Plane) and worker nodes (run the apps that are deployed. (pg. 18)

Control plane has: </br>

Kube API Server - Control plane components communicate/we communicate with this. 
Scheduler - Schedules your apps
Controller Manager - cluster level functions (replcating components, keeping track of workers, handling failures)
etcd - data store that distributes cluster config
(pg. 19)

Worker Nodes - Run the containerized app - monitor, run and provie services for docker, kubelet, and Kube Service proxy (kube-proxy) which load balances network traffic. (pg. 19)


