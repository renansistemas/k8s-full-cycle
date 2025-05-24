# k8s-full-cycle
Repositório criado para estudos e treinamento utilizando o Kubernetes

## Pré-requisitos
- Docker
- Kubectl

## Passos para Instalação e Configuração

### 1. Instalar o Docker

```bash
# Atualize o repositório e instale dependências
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Adicione o repositório oficial do Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Instale o Docker
sudo apt update
sudo apt install -y docker-ce

# Verifique a instalação
docker --version
```

### 2. Instalar o kubectl

```bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```

### 3. Instalar o kind

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/
kind --version
```

### 4. Iniciar um cluster Kubernetes com kind

```bash
kind create cluster
```

### 5. Verificar os nós ativos no cluster

```bash
kubectl get nodes
```

## Explicação dos Arquivos YAML

No diretório deste projeto, você encontrará três arquivos principais para orquestração no Kubernetes:

### pod.yaml
Define um **Pod**, que é a menor unidade executável no Kubernetes. O arquivo `pod.yaml` especifica um ou mais containers que serão executados juntos, compartilhando recursos como rede e armazenamento. Use este arquivo para criar um pod isolado, geralmente para testes ou aplicações simples.

### deployment.yaml
Define um **Deployment**, que gerencia a criação e atualização de múltiplas réplicas de pods. O `deployment.yaml` garante alta disponibilidade e atualização controlada dos pods. Ele permite escalar a aplicação facilmente e realizar rollouts/rollbacks automáticos em caso de falhas.

### service.yaml
Define um **Service**, responsável por expor os pods para acesso interno ou externo ao cluster. O `service.yaml` cria um endpoint estável para acessar os pods, mesmo que eles sejam recriados ou substituídos pelo deployment. Pode ser configurado como ClusterIP, NodePort ou LoadBalancer, dependendo da necessidade de exposição.

Esses arquivos juntos permitem que você defina, gerencie e exponha sua aplicação de forma padronizada e escalável no Kubernetes.