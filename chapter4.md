## Replication and other controllers, deploying managed pods

As soon as a pod is scheduled to a node, the Kubelet on that node will run it's containers and then keep them running as long as the pod exists. (pg. 85)

"liveness probes" are used to check if a container is alive - restart is called if the probe fails (pg. 85)

Get request, TCP socket probe, or exec probe - conditions you can set for success/restart probes for automating restarting containers (pg. 86)

k logs mypod --previous (--previous allows u sto get the logs from the crashed container) (pg. 87)


