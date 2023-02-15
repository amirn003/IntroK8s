# Create a Pod

1. Export your namespace as an environment variable so that it can be used in subsequent commands.

    export MY_NAMESPACE=sn-labs-$USERNAME

2. Build and push the image

    docker build -t us.icr.io/$MY_NAMESPACE/hello-world:1 . && docker push us.icr.io/$MY_NAMESPACE/hello-world:1

3. Run the hello-world image as a container in Kubernetes

    kubectl run hello-world --image us.icr.io/$MY_NAMESPACE/hello-world:1 --overrides='{"spec":{"template":{"spec":{"imagePullSecrets":[{"name":"icr"}]}}}}'

4. List the pods

    kubectl get pods

5. Get more details about the resource

    kubectl get pods -o wide

6. Describe the Pod

    kubectl describe pod hello-world

7. Delete the Pod

    kubectl delete pod hello-world

8. Imperatively create a Pod

    kubectl create -f hello-world-create.yaml

9. Create a Pod with a declarative command

    kubectl apply -f hello-world-apply.yaml

10. Get the deployments

    kubectl get deployments

11. Load balancing the application

    kubectl expose deployment/hello-world

12. List Services

    kubectl get services

13. Create a proxy

    kubectl proxy

14. Ping the app to get a response

    curl -L localhost:8001/api/v1/namespaces/sn-labs-$USERNAME/services/hello-world/proxy

15. Delete the Deployment and Service.

    kubectl delete deployment/hello-world service/hello-world
    

