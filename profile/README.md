![logo](https://github.com/confidential-containers/.github/blob/main/coco_logo.png)

## Welcome to confidential-containers

Confidential Containers is an open source community working to enable cloud native confidential 
computing by leveraging 
[Trusted Execution Environments](https://en.wikipedia.org/wiki/Trusted_execution_environment) to 
protect containers and data.

Goals:
- Allow cloud native application owners to enforce application security requirements
- Transparent deployment of unmodified containers
- Support for multiple TEE and hardware platforms
- A trust model which separates Cloud Service Providers (CSPs) from guest applications
- Least privilege principles for the Kubernetes Cluster administration capabilities which impact 
delivering Confidential Computing for guest application or data inside the TEE.

### Find out more
- [**Documentation**](https://github.com/confidential-containers/documentation) Learn about our 
vision, goals, and progress.

### Get started
- [**Kubernetes Operator**](https://github.com/confidential-containers/confidential-containers-operator)
Deploy Confidential Containers on a Kubernetes cluster with an operator.

### Supporting Repositories
- [**attestation-agent**](https://github.com/confidential-containers/attestation-agent) A user space 
service for attestation procedure
- [**containerd**](https://github.com/confidential-containers/containerd) A temporary fork of 
containerd to explore runtime concepts and capabilities required for confidential containers
