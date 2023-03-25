# Kubernetes
Serve para orquestração de containers em diferentes máquinas (nodes)

## Conceitos
Control Plane
: máquina que gerencia todas as outras máquinas

Node
: a máquina gerenciada pelo Control Plane

Deployment
: execução de uma imagem/projeto em um Pod

Pod
: um ou mais containers que ficam no Node

Services
: expõe os Pods

kubectl
: linha de comando do Kubernetes

## Minikube
Não serve para produção

minikube start --driver=<DRIVER\>
: Inicia o Minikube (DRIVER: virtualbox, hyperv, docker)

**minikube status**

**minikube stop**

minikube dashboard
: para apenas a url usar --url

## Criando Deployment
O deployment cria automaticamente o pod.

**kubectl create deployment <NOME\> --image=<IMAGEM_DOCKER_HUB\>**

**kubectl get deployments**

**kubectl describe deployments**

**kubectl delete deployment <NOME\>**

**kubectl get pods**

**kubectl describe pods**

**kubectl config view**

## Criando Services
O service expõe o pod para o mundo externo. Os dados do pod são efêmeros.
O tipo mais utilizado é o LoadBalancer.

**kubectl expose deployment <NOME\> --type=<TIPO\> --port=<PORTA\>**

minikube service <NOME\>
: O nome do service é o nome do deployment

**kubectl get services**

**kubectl delete service <NOME\>**

## Replicando a aplicação
kubectl scale deployment/<NOME\> --replicas=<NUMERO\>
: O número pode ser utilizado para fazer scale down passando um número menor do que as replicas existentes

**kubectl get rs**

## Atualização de imagem
Rebuildar a imagem do docker e enviar para o docker hub.

**kubectl set image deployment/<NOME_DEPLOYMENT\> <NOME_CONTAINER\>=<NOVA_IMAGEM\>**

## Desfazer alteração
**kubectl rollout status deployment/<NOME\>**

**kubectl rollout undo depoyment/<NOME\>**

## Modo declarativo
Utiliza um arquivo em YAML

- apiVersion
- kind
- metadata
- replicas
- containers

**kubectl apply -f <ARQUIVO\>**

**kubectl delete -f <ARQUIVO\>**