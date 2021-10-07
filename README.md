# OCD Splunk Pub #3 - Splunk in Kubernetes
Notes and lab instructions for running Splunk in Kubernetes using [splunk-operator](https://github.com/splunk/splunk-operator).

Presented at OCD Splunk Pub #3 on 2021-10-08.

## Demo
- Deploy a `Standalone` instance and service
- Reconfigure the `Standalone` instance
- Deploy an `IndexerCluster`
- Reconfigure the `Standalone` to search the `IndexerCluster`

## Useful Links
- [splunk-operator](https://github.com/splunk/splunk-operator)
- [docker-splunk](https://github.com/splunk/docker-splunk)
- [splunk-ansible](https://github.com/splunk/splunk-ansible)
- [kubelabs](https://collabnix.github.io/kubelabs)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet)

## Lab instructions
### microk8s
1. Follow official [install instructions](https://microk8s.io) for microk8s
2. Enable features:
	`microk8s enable dns storage`
3. Create a namespace for this lab:
	`microk8s kubectl create namespace splunkpub`

### splunk-operator
1. Install splunk-operator in the splunkpub namespace:
	`microk8s kubectl --namespace splunkpub apply -f https://github.com/splunk/splunk-operator/releases/download/1.0.2/splunk-operator-install.yaml`

### Splunk resources
Run the commands like below, but not all at once!
Pause to view outputs of `kubectl get`, check `kubectl logs`, and monitor the status of Splunk before moving on to the next step. Also, check changes with `kubectl diff` before applying.

1. Alias `kubectl` in your shell to microk8s and the namespace:
    `alias kubectl="microk8s kubectl --namespace splunkpub"`

2. Deploy a `Standalone` instance and service:
	`kubectl apply -f kubernetes/standalone-v1.yml`
	`kubectl apply -f kubernetes/service.yml`

3. Get Splunk password from secret:
	`kubectl get secret splunk-s1-standalone-secret-v1 -o json | jq '.data | map_values(@base64d)'`

4. Reconfigure the `Standalone` instance and deploy an app to it:
	`kubectl apply -f kubernetes/standalone-v2.yml`

5. Deploy an `IndexerCluster` with two peers:
    `kubectl apply -f kubernetes/indexercluster.yml`

6. Reconfigure the `Standalone` instance to search the `IndexerCluster`:
	`kubectl apply -f kubernetes/standalone-v3.yml`
