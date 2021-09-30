# OCD Splunk Pub #3 - Splunk in Kubernetes
Notes and lab instructions for running Splunk in Kubernetes using [splunk-operator](https://github.com/splunk/splunk-operator).

Presented at OCD Splunk Pub #3 on 2021-10-08.

## Demo
- [ ] Deploy `Standalone` instance and service
- [ ] Deploy `IndexerCluster`
- [ ] Configure `Standalone` to search `IndexerCluster`
- [ ] Push app to `IndexerCluster`

## External Links
- [splunk-operator](https://github.com/splunk/splunk-operator)
- [docker-splunk](https://github.com/splunk/docker-splunk)
- [splunk-ansible](https://github.com/splunk/splunk-ansible)
- [kubelabs](https://collabnix.github.io/kubelabs)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet)

## Lab instructions
### microk8s
Install microk8s
Enable features
Create namespace

### splunk-operator
Install splunk-operator in namespace
Deploy `Standalone` instance and service
Change Splunk configuration
