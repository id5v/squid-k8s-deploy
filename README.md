
# Squid Proxy Deployment Project

This project contains two separate implementations for deploying a **Squid Proxy server**, designed to test and manage HTTP transport connections. The repository is organized into two directories: `docker` for the Docker-based setup and `kube` for the Kubernetes-based setup.

The Squid Proxy acts as an intermediary to route and analyze HTTP traffic, making it suitable for testing, debugging, or optimizing HTTP connections.

## Docker Setup

The Docker implementation is located in the `docker` directory. This approach provides a straightforward way to build and run the Squid Proxy server in a containerized environment. Follow these steps to set up Squid Proxy using Docker:

1. Navigate to the `docker` directory and build the Docker image:
   ```bash
   docker build -t squid-proxy .
   ```
2. Run the container, mapping port `3128` for external access:
   ```bash
   docker run -d -p 3128:3128 squid-proxy
   ```

Once the container is running, you can connect to the proxy server on `localhost:3128` to test HTTP transport behavior.

---

## Kubernetes Setup

The Kubernetes implementation is located in the `kube` directory. This setup leverages **Helm charts** for easy deployment and scaling in Kubernetes clusters. Follow these steps to deploy the Squid Proxy server in a Kubernetes environment:

1. Navigate to the `kube` directory and install the Helm chart:
   ```bash
   helm install --name squid .
   ```
2. Forward the Squid Proxy service to your local machine on port `3128`:
   ```bash
   kubectl port-forward -n default service/squid 3128:3128
   ```

Once the service is forwarded, you can connect to the proxy at `localhost:3128` to test HTTP transport scenarios.

---

## Use Cases

- **Testing HTTP Transport**: Squid Proxy enables detailed inspection and management of HTTP connections.
- **Development and Debugging**: Use the proxy to simulate and debug various HTTP scenarios in a controlled environment.
- **Performance Tuning**: Analyze and optimize HTTP traffic to improve performance and reliability.

Choose the implementation (`docker` or `kube`) based on your testing environment and scalability requirements. Both setups ensure a functional Squid Proxy server accessible via port `3128`.
