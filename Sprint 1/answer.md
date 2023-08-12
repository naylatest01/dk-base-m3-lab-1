# Sprint 1
TODO: Student to complete code and comments in the sections below.

## Install Kubernetes node 1

- Customized kubeadm-config.yaml:

kind: InitConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
bootstrapTokens:
- token: ef2063.28rldur6uqvqfrp7
nodeRegistration:
  ignorePreflightErrors:
  - NumCPU
---
kind: JoinConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
discovery:
  bootstrapToken:
    apiServerEndpoint: install_lab1:6443
    token: ef2063.28rldur6uqvqfrp7
    unsafeSkipCAVerification: true
nodeRegistration:
  ignorePreflightErrors:
  - NumCPU
---
kind: KubeletConfiguration
apiVersion: kubelet.config.k8s.io/v1beta1
failSwapOn: false
---
kind: ClusterConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
apiServer:
  certSANs:
  - 34.221.111.82
