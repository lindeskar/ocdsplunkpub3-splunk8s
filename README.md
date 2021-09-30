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
1. Follow official [install instructions](https://microk8s.io)
2. Enable storage feature:
	`microk8s enable storage`
3. Create a namespace for this lab:
	`microk8s kubectl create namespace splunkpub`

### splunk-operator
1. Install splunk-operator in the splunkpub namespace:
	`microk8s kubectl --namespace splunkpub apply -f https://github.com/splunk/splunk-operator/releases/download/1.0.2/splunk-operator-install.yaml`
2. Deploy `Standalone` instance and service:
	`microk8s kubectl --namespace splunkpub apply -f kubernetes/standalone-v1.yml`
3. Change Splunk configuration:
	`microk8s kubectl --namespace splunkpub apply -f kubernetes/standalone-v2.yml`
