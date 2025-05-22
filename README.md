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