# niord-keycloak

In order to use Niord you will need to have a running Keycloak instance as Niord requires it for user management. 

If you do not have a running Keycloak instance you can use. The easiest way to setup a local Keycloak is by using Docker Compose.

## Running using Docker Compose

docker-compose up

You will now have a Docker project called "niord-keycloak" with two containers running

niord-keycloak The actual Keycloak instance
niord-mysql-keycloak A database instance that Keycloak needs in order to run.

You can go to localhost:8090 and try and login with "user" "admin"

Will also install a Niord keycloak-theme and add the default niord domain
The default niord user is sysadmin

Running will create ~/.niord-keycloak on your local computer. This is where mysql stores its datafiles

## Running using Helm

Another alternative is to create a Keycloak instance using Kubernetes "package manager" Helm.
This is typically what you want to do in production.



## Update Niord theme
Install Niord theme

// Backup
https://cwienczek.com/2020/06/simple-backup-of-postgres-database-in-kubernetes/