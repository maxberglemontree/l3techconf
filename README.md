# l3techconf
Repo for demonstrating basic Kubernetes usage

This repo: https://github.com/maxberglemontree/l3techconf/tree/main

### Requirements
You must be able to run `snap`.

Then, run `snap install microk8s`. You may be required to add a flag: `snap install microk8s --classic`

Once the installation is complete, test the installation by running a command such as `microk8s kubectl get ns`. You should see a list of namespaces created by microk8s.

### How to - simple

Go to the simple directory and run the following commands:

```
microk8s kubectl apply -f deployment.yaml
microk8s kubectl apply -f service.yaml
```

This will deploy the hello-world application.

To scale up the application, run `microk8s kubectl scale deployment hello-world --replicas 2`. To scale it back down, run the same command but with only 1 replica.

To "jump in" to a pod, first get the name of the pod with `microk8s kubectl get all`. This will display pods, services, deployments and some other stuff. Use the name of a pod and execute the following command: `microk8s kubectl exec -it <POD NAME> -- bash`. This will let you into the container in a bash-shell. The containers referenced here have curl installed. You can use curl within the pod to send a request to the hello-world service (it should be listed earlier, from when you executed `microk8s kubectl get all`). Use curl like in the following way to verify that pods can access services within the cluster:

```
curl (service name or service ip)/hello
```

If it works, you should get a message like "Hello, World!". That concludes the simple usage in this demonstration.

