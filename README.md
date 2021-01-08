# niord-keycloak

In order to use Niord you will need to have a running Keycloak instance as Niord needs an instance for user management. 

The easiest way to setup a local Keycloak is by using Docker Compose. As we will describe in the next section.
If you want to set up a production grade instance we will briefly touch upon it in the Keycloak+Helm section.

## Keyclock via Docker Compose

To startup a local keycloak instance you simply stand in this directory and run

```bash
$ docker-compose up
```

This will create a Docker project called "niord-keycloak" with two containers running:

- niord-keycloak: The actual Keycloak instance
- niord-mysql-keycloak: A database instance that Keycloak needs in order to run.

It will also create a ~/.niord-keycloak on your computer. This is where MySql stores its data files.

You can go to localhost:8090 and try and login to the mast realm with username/password "user"/"admin"

Docker compose also create a niord realm which is the realm that the niord application uses.
A single user with password sysadmin/sysadmin is created.

## Keycloak via Kubernetes+Helm

Another alternative is to create a Keycloak instance using Kubernetes and a Helm chart provided by Bitnami https://github.com/bitnami/charts/tree/master/bitnami/keycloak.

Assuming you have already installed Helm and access to a running K8s cluster (install minikube if you don't). You start by adding the bitnami chart registry:
```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
```

And then install a Keycloak using the helm example values template we have provided. You will mostly need to update the ingress hostname in the yaml file.

```bash
$ helm install keycloak --values helm-example-values.yaml bitnami/keycloak
```
