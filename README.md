# Docker Demo Application

This is a Go demo application with a PostgreSQL database used for demonstrating Docker, Swarm mode, and Kubernetes

## Local Development

Using `docker-compose` you can start a local development environment. This environment will bind mount the application's
`static` and `templates` directories into the container so basic changes can be made live.

### Linux

#### Start

Start the local development enviornment

```
docker-compose up
```

#### Stop

Use `ctrl+c` to stop the local development environment


## Production

This application can be deployed on Kubernetes or Swarm (soon) using the YAML files in thier respective directories
(`kubernetes/cluster/` or `swarm/`). The repository is currently setup to use the Mirantis Docker Enterprise
Demo environments. This includes a Jenkins server and all of the automation to deploy the application onto
the selected cluster.


### How to Deploy

```
git clone https://github.com/mirantis-field/docker-demo.git
git checkout -b <mirantis.local username>
git push --set-upstream origin <mirantis.local username>
```

The new branch will automatically be detected by Jenkins and deployed onto the default cluster using the defaul
orchestrator, specified in the `Jenkinsfile`.

### Changing the Deployment Cluster

To switch the deployment cluster, you can set the value of `TARGET_CLUSTER_DOMAIN` in the `Jenkinsfile`.
For available options check the Presales Docker Enterprise Environment wiki.

### Changing the Orchestrator

To switch between Kubernetes and Swarm, you can set the value of `ORCHESTRATOR` in the `Jenkinsfile`.
Available options are `"kubernetes"` or `"swarm"`

### Changing the Kubernetes Ingress

To switch between Kubernetes and Swarm, you can set the value of `KUBERNETES_INGRESS` in the `Jenkinsfile`.
Available options are `"ingress"` or `"istio_gateway"`
