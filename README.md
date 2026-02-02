# workshop-k8s
workshop-k8s

# สิ่งที่ต้องเตรียม
1. ถ้าใช้ github codespace
```
# x86_64
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.31.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind


# Install kubectl
curl -LO "https://dl.k8s.io/release/v1.35.0/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client --short


# Install Trivy
curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sudo sh -s -- -b /usr/local/bin v0.69.0

# create cluster

cd kind
kind create cluster --config=config.yml


# Verify

kubectl cluster-info --context kind-kind
kubectl get nodes
```

2. เครื่องของตัวเอง Windows (LABTOP)
```
# ติดตั้ง WSL2 + Ubuntu
wsl --install -d Ubuntu-22.04

# x86_64
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.31.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind


# Install kubectl
curl -LO "https://dl.k8s.io/release/v1.35.0/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client --short

# Install Trivy
curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sudo sh -s -- -b /usr/local/bin v0.69.0


# create cluster
cd kind
kind create cluster --config=config.yml


# Verify
kubectl cluster-info --context kind-kind
kubectl get nodes
```

3. เครื่องของตัวเอง macOS (LABTOP)
```
# Install kind
brew install kind

# Install kubectl
brew install kubectl

# Install trivy
brew install trivy

# create cluster
cd kind
kind create cluster --config=config.yml

# Verify
kubectl cluster-info --context kind-kind
kubectl get nodes
```