## Pods: running containers in Kubernetes

Pod is a co-located group of containers and represents the basic building blocks of Kube. (pg. 56)

When a pod has multiple containers, they are always on a single worker. (pg. 56)

Containers are designed to run only a single process per container (typically), hence pods! They do restart logic for you (pg. 56)

Pods allow us to run closely related processes together w/almost the same env while keeping them (somewhat) isolated (pg. 57)

Kube configures Docker to have all containers of a pod to share the same set of LInux namespaces instead of each container having it's own set of namespaces. (pg. 57)

Because pods have the same namespace, it's ipmortant that processes don't bind to the same port numbers or you'll hit port conflicts. (pg. 57)

Every pod can talk to every other pod through their unique ip address (diagram page 58)

Summary: Pods are logical hosts that behave like physical hosts or VMs in the non-container world.  Each process in a pod is encapsulated. (pg. 58)

Organize apps into multiple pods where each one contains only tightly related components or processes (pg. 58)

If front and backend are in the same pod, then both will always run on the same machine - separate things out as needed and let Kube utilize computational resources more efficiently (pg. 59)

Kube doesn't scale horizontally, it scales whole pods and backend and frontend will require different scaling (pg. 59)

Question guide and configuration example (pg. 60)

Defining all the kube objects from YAML makes it possible to store them in version control. (pg. 61)

Diagram showing YAML descriptor of an existing pod (pg. 61)

`kubectl get po <pod_name> -o yaml` to show yaml config (pg. 61)

Three important sections in all kube resources:

Metadata - name, namespace, labels, other info
Spec - description of the pod's contents, containers, volumes, and other
Status - current info about the running pod, condition it's in, description, internal ip, and other

Specifying container ports is purely informational, however it's good to be explicit to severyone using the cluster can see which ports the pod exposes.  It also allows name assignment. (pg. 63)

kubectl logs <app_name> is a great way to get logs without using docker logs, they rotate daily every time it hits 10MB (pg. 66)

port forwarding is a great way to debug an individual pod `kubectl port-forward <pod> 8888:8080` would allow you to curl `localhost:8888` and see a response from the app (pg. 67)

Labels are simple but powerful for all Kube resources.  It's a key value pair attached to a resource that shows everyone who can access the cluster the system's structure and where each pod fits (pg. 69)

Label selectors allow you to select a subset of pods tagged with certain levels and perform an ops on those specific pods.  (pg. 74)

the nodeSelector key value pair in the yaml files tells Kube to deploy this pod only to nodes containing that label (pg. 74)

Annotations are used to add descriptions for each pod or API object so that everyone using the cluster can quickly look up info about each individual object. (pg. 75)

Namespaces allow you to isolate objects into distinct groups, they don't provide any kind of isolation from running objects. (pg. 79)

k delete po <pod_name> sends a SIGTERM with timeout to SIGKILL (more on deleting commands pg. 80-81)
