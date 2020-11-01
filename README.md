# Information

Setup of Postgres Exporter based on: https://github.com/bitnami/bitnami-docker-postgres-exporter/tree/0.8.0-debian-10-r259 which is also based on: https://github.com/wrouesnel/postgres_exporter

## Deployment

Bitnami provides custom Images with non-root privileges (USER 1001), which are needed sometimes regarding PROD Clusters. Normally you have best practices for Security like not allowing Images/Containers to be executable as root containers in your Kubernetes Clusters (DevSecOps). In the official Dockerfile you can see where the USER variable is set to make sure that the Image will only be runnable as non-root: https://github.com/bitnami/bitnami-docker-postgres-exporter/blob/0.8.0-debian-10-r259/0/debian-10/Dockerfile

There is also the official Helm Chart which you can use: https://github.com/bitnami/bitnami-docker-postgres-exporter/blob/0.8.0-debian-10-r259/0/debian-10/Dockerfile

Because of simplicity I decided to create my own Helm Chart which is nearly exactly the same. Sometimes less is more and easier to understand :) If you take a look into values.yaml you can find the variables which needs to be used or to adapted/extended.

```
dataSourceUri: "postgresql://postgres_exporter:password@localhost:5432/postgres?sslmode=disable"
``` 

For the URI you have to know the URL of the postgres database with its port, the user with the correct password and also the database which you want to connect. 
