# Kubernetes local development tools comparison

| Feature \ Option                     | Minikube                                                                                                            | Kind (Kubernetes IN Docker)                                                                                     | k3d                                                                     | Podman                                                             |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|--------------------------------------------------------------------|
| **Description**                          | Minikube is a tool that makes it easy to run Kubernetes locally by creating a single-node Kubernetes cluster.       | Kind is a tool for running local Kubernetes clusters using Docker container "nodes".                              | k3d is a lightweight wrapper to run Kubernetes clusters in Docker.     | Podman is a daemonless container engine for developing, managing, and running OCI Containers and Pods.                         |
| **Supported OS**                   | Linux, macOS, Windows                                                                                                | Linux, macOS, Windows                                                                                         | Linux, macOS, Windows                                                   | Linux                                                              |
| **Supported Architectures**        | x86_64, ARM64                                                                                                       | x86_64, ARM64                                                                                                | x86_64, ARM64                                                            | x86_64, ARM64                                                      |
| **Automation Options**             | Supports automation through scripts and integration with tools like Ansible.                                        | Provides automation options through scripting and configuration management tools.                                | Supports automation through scripts and integration with CI/CD pipelines. | Offers automation through scripting and integration with configuration management tools.                                           |
| **Additional Options**             | Provides addons for monitoring, logging, and storage.                                                               | Relies on external tools for monitoring and management.                                                         | Supports integration with monitoring tools and offers cluster management features. | Limited additional options, focuses primarily on container management. |
| **Pros**                           | - Easy to use and setup <br> - Good documentation and community support <br> - Supports various addons for extended functionality | - Lightweight and fast <br> - Easy to integrate with Docker ecosystem <br> - Supports custom node configurations             | - Lightweight and fast <br> - Good integration with Docker ecosystem <br> - CI/CD friendly | - Daemonless, making it lightweight and secure <br> - Good for container management <br> - Compatible with Docker images  |
| **Cons**                           | - Single-machine cluster only <br> - Can be resource-intensive on some systems                                             | - Single-machine cluster only <br> - Requires external tools for monitoring and management                            | - Single-machine cluster only | - Limited to container management and lacks some Kubernetes features |

[Minikube demo](https://asciinema.org/a/tzdf7F9vMXpsz67dZehd10wLH):
![Image](.data/minikube_demo.gif)

[Kind demo](https://asciinema.org/a/XGCvfdxaske1JqBxtddp3HTdx):
![Image](.data/kind_demo.gif)

[k3d demo](https://asciinema.org/a/fMCiyqFl3NcpNdynvzjVUWHLV):
![Image](.data/k3d_demo.gif)

Conclusions: It's better to use k3d for POC deployment, because in the future it would simplify transition to production-grade Kubernetes distribution.