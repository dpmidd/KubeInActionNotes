## First steps with Docker and Kubernetes

If the latest image isn't local, it will pull it from Docker Hub registry. (pg. 27) <br/>

Docker assumes you want the latest tag unless specified otherwise in your commands (pg. 28) <br/>

Because the node image is made specifically for running Node.js apps, it includes everything we need to run the app (pg. 29) <br/>

The contents of the whole dir are uploaded to the daemon and the image is built there when executing `docker build kubia .` <br/>

When building an image a new layer is created for each individual command in the Dockerfile. <br/>

`docker exec -it container_name /bin/bash` -i stands for make sure STDIN is kept open and -t allocates a pseudo terminal (TTY) (pg. 33) <br/>

--generator=run-pod/v1 created the "kubia" replication controller - the output is different in terminal than in the book but if you navigate to "workload" in the UI for gcloud it will show (pg. 42) <br/>

A pod is a group of one or more tightly related containers that will always run together on the same worker node in the same Linux namespace(s) (pg. 43) <br/>

Each pod has it's own IP and contains one or more containers, each running an app process and are spread across diff worker nodes (pg. 43) <br/>

kubectl describe pod -> great source of information (pg. 44) <br/>

`kubectl expose rc kubia --type=LoadBalancer --name kubia-http` creates a service object which will grant an external IP for us to access our application (we can get this data with kubectl get services) (pg. 46) <br/>

ReplicationController, Pod, and Service fit together - RC creates the actual pod object, then we told kube to expose all the pods managed by that RC as a service (diagram pg. 47) <br/>

RC makes sure there is exactly one instance of my pod running (pg. 48)

Services - Needed because pods are ephemeral, they solve the ever changing pod IPs and expose pods at a single constant ip and port pair. The service forwards requests to the pods (pg. 48) <br/>
