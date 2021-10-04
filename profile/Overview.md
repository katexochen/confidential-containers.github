
# Confidential Containers
We are interested in integrating existing [Trusted Execution Environments](https://en.wikipedia.org/wiki/Trusted_execution_environment) (TEE) 
infrastructure support and technologies with the cloud native world. Our focus is to place a kubernetes pod into a TEE. 

## Why?
Security has long been a significant concern with data encryption at rest and in flight assumed to be a key part of any offering.
Trusted Execution Environments look to address the data in use security concern.

Cloud Computing adoption continues to accelerate whether it be Public, Private or increasingly common a Hybrid approach
and with it the trust boundaries change. Consideration of Insider Threats needs to now consider the cloud provider,
infrastructure provider, managed service provider.

Certain Industries are heavily focused on compliance to standards, governments too are concerned both [collectively](https://www.un.org/counterterrorism/cybersecurity)
and [individually](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/).
The standards expected to protect software solutions continue to evolve towards a concept of Confidential Computing

Confidential Containers look to address the growing conern and needs of these three areas combining and growing in the future.

## How?
### Trusted Execution Environments
![TEE Protects an application](../images/ApplicationTEEProtection.png)

The TEE seeks to protect the Application and Data from outside threats, with the Application owner having complete control 
of all communication across the TEE boundary. The application is considered a Virtual Machine and once supplied with the
resources it requires, the TEE protects those resource (memory cpu) from the infrastructure and all communication across 
the TEE boundary is under the control of the Application Owner.

### Cloud Native Execution Environments
![TEE protects an orchestrated pod](../images/CloudNativeTEEProtection.png)

However moving to a more cloud native approach, the application is now considered a group of one or more containers, 
with shared storage and network resources (pod). This pod is also subject to an orchestration layer which needs to dynamically 
interact with the pods and containers with respect to provisioning, deployment, networking, scaling, availability, and
lifecycle management.

How does the application owner trust the orchestration actions required to deliver on the Cloud Native promise,
take advantage of the TEE capabilities and deliver on their compliance/ security requirements?

### Integration of Technologies
With many TEE technologies requiring a KVM boundary between the host and guest, [Kata Containers](https://katacontainers.io/)
are the basis for our initial work. The Kata Containers project already supports a KVM boundary between a Kubernetes Node and Kubernetes Pod
and focuses on reducing the concern of a Guest attacking the Host, in this case a breakout from containers within the pod attacking the Kubernetes Node.

Requests from TEE vendors to support their technology within Kata Containers project led to consideration of
[Confidential Computing Enablement](https://github.com/kata-containers/kata-containers/issues/1332). How to protect 
the guest from the host, in this case to protect the Containers and workload within a Pod from the Kubernetes Node.

Initial exploration led to the realisation that this was not a problem that it is possible to solve within the Kata 
Containers Project alone, it raises considerations that need discussed and resolved in other areas of a cloud native stack, from 
container runtime to CSI to orchestration(kubelet) and brings in new projects or concerns such as attestation, reconsidering trust 
domains and least privilege capabilities for kubernetes admin.

Our initial effort has focussed on several initial Areas
- Attestation - Giving Application Owner confidence their workload (containers) are really running in a TEE.
- OCI Container Image Pull - Ensuring the Container Images cannot be viewed or altered before they are started and available within the TEE.
- Restricting Orchestration Capabilities accepted today but which undermine Confidential Containers.

We will continue to enage more widely with CNCF projects around kubelet, container runtimes and seek to address further 
integration topics regarding confidential computing such as
- CSI plugins
- CNI 
- Align confidential Computing with Expected User Experience
- Tooling enhancements to facilitate Confidential Computing
- Alig confidential computing with broader Security considerations within CNCF
- Confidential Computing thinking from other projects
