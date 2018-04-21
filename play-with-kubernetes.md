## Play with Kubernetes

https://www.udemy.com/learn-docker-advanced/learn/v4/t/lecture/8568858?start=0

https://labs.play-with-k8s.com/


    - Free and great for practice


    - click `add instance ` + follow instructions

    - initialize cluster:

    ` kubeadm init --apiserver-advertise-address $(hostname -i)  `

    - Initialize cluster networking:

      `  kubectl apply -n kube-system -f \
    "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 |tr -d '\n')" `

    -  (Optional) Create an nginx deployment:

    `  kubectl apply -f https://k8s.io/docs/user-guide//nginx-app.yaml `

    - install Git on GUI

    ` yum install git `

    - Clone example voting app:

    ` git clone https://github.com/mmumshad/kubernetes-example-voting-app.git `

    ` cd kubernetes-example-voting-app `

    - view all pods and services:

      ` ls `

      ` kubectl create -f voting-app-pod.yml `

      ` kubectl get pods `//check status

      ` kubectl describe pods `//get more info

      ` kubectl get nodes `

      NOTE: master node (we have only one node in this case) cannot host any services by default

      * workaround:


      ` kubectl taint nodes <nodeName> node-role.kubernetes.io/master:NoSchedule- `

      ie.,....

      ` kubectl taint nodes node1 node-role.kubernetes.io/master:NoSchedule- `

      ` kubectl get pods `//should now see that node is running....may take a minute

      - create service so can access application:

        ` ls `

        ` kubectl create -f voting-app-service.yml `

        ` kubectl get services `

        * click on IP/url link in GUI to view application in browser

        * create other services

        ` kubectl create -f redis-pod.yml `

        ` kubectl create -f redis-service.yml `

        ` kubectl create -f postgres-pod.yml `

        ` kubectl create -f postgres-service.yml `

        ` kubectl create -f worker-app-pod.yml `

        ` kubectl create -f result-app-pod.yml `

        ` kubectl create -f result-app-service.yml `

        ` kubectl get pods `//check status of pods

        ` kubectl get services `//check status of services


          - click on new link in GUI for `result app `


      * To instead create all pods and services at once:


      ` kubectl create -f . `//will read all files at once


      ` kubectl get pods `//check status of pods

      ` kubectl get services `//check status of services



      * Delete all at once


        ` kubectl delete -f . `//select all files in directory


        ` kubectl get pods `//check status of pods

        ` kubectl get services `//check status of services
