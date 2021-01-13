# niord-keycloak

In order to use Niord you will need to have a running Keycloak instance as Niord needs an instance for user management. 

The easiest way to setup a local Keycloak is by using Docker Compose as described in the next section.

## Keyclock via Docker Compose

To startup a local keycloak instance you simply stand in this directory and run

```bash
$ docker-compose up
```

This will create a Docker project called "niord-keycloak" with two containers running:

- niord-keycloak: The actual Keycloak instance
- niord-mysql-keycloak: A database instance that Keycloak needs in order to run.

This also creates a ~/.niord-keycloak directory on your computer where Keycloak maintains a MySql database.

You can now go to localhost:8090 and try and login to the master realm with (username/password) user/admin

Docker compose creates a niord keycloak realm which is the realm that the niord application uses.
A single user/password sysadmin/sysadmin is created. Use this when you login via the Niord application.

## Keycloak via Kubernetes+Helm

An alternative to using Docker Compose is to use Kubernetes and this Helm chart provided by Bitnami https://github.com/bitnami/charts/tree/master/bitnami/keycloak.

Assuming you have already installed Helm and access to a running K8s cluster (install minikube if you don't). You start by adding the bitnami chart registry:
```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
```

You can then install a Keycloak, for example, by using the provided example value file. You will mostly need to update the ingress hostname in the yaml file.

```bash
$ helm install keycloak --values helm-example-values.yaml bitnami/keycloak
```
