# kubernetes 

**Note:** To start with kubernetes install docker as we will use the docker driver 

To Download kubernetes on MacOS:

Install kubectl binary with curl

1. curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"
   
2.  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl.sha256"

3. echo "$(cat kubectl.sha256)  kubectl" | shasum -a 256 --check

4. chmod +x ./kubectl

5. sudo mv ./kubectl /usr/local/bin/kubectl

6. sudo chown root: /usr/local/bin/kubectl

7. kubectl version --client --output=yaml 

8. rm kubectl kubectl.sha256

To Download kubernetes on Windows:

1. curl.exe -LO "https://dl.k8s.io/release/v1.28.0/bin/windows/amd64/kubectl.exe"

2. curl.exe -LO "https://dl.k8s.io/v1.28.0/bin/windows/amd64/kubectl.exe.sha256"

3. CertUtil -hashfile kubectl.exe SHA256
4. type kubectl.exe.sha256

5. kubectl version --client --output=yaml

6. kubectl cluster-info

You will get the response:
The connection to the server <server-name:port> was refused - did you specify the right host or port?

7. kubectl cluster-info dump

Install minikube:

visit to download: https://minikube.sigs.k8s.io/docs/start/

Run minikube:

1. minikube start

2. kubectl get pot -A

3. minikube dashboard

Service:

4. kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
5. kubectl expose deployment hello-minikube --type=NodePort --port=8080

6. kubectl get services hello-minikube

7. kubectl port-forward service/hello-minikube 7080:8080

Tada! Your application is now available at http://localhost:7080/.

Some commands to manage cluster

1. minikube pause
2. minikube unpause
3. minikube stop
4. minikube config set memory 2048
5. minikube addons list
6. minikube delete --all
7. minikube start -p aged --kubernetes-version=v1.16.1
