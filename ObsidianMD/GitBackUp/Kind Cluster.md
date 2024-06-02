```bash
# Install Docker (if not already installed)
# Install Kind (assuming macOS with Homebrew)
brew install kind

# Create a Kind cluster
kind create cluster

# Configure kubectl to use the Kind cluster
export KUBECONFIG="$(kind get kubeconfig-path --name="kind")"

# Verify cluster is running
kubectl cluster-info
```