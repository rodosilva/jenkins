# Jenkins
Jenkins y Pipelines BootCamp de Codigo Facilito

## Seteando el Entorno

1. Primero, corremos un `docker compose up` usando [docker-compose.yml](./docker/docker-compose.yml).

Con esto estaremos levantado un `Jenkins` usando el puerto `8080`

2. Para conectar `Jenkins` con `Github` la Key privada debemos ir `Panel de Control - Administrar Jenkins - Credentials - System - Global credentials (unrestricted)`
![New credentials](./images/jenkins_NewCredential.png)

3. La pública se colocará en [Deploy Keys](https://github.com/rodosilva/jenkins/settings/keys)

4. Para las configuraciones del `Pipeline` debemos colocar el repositorio de GitHub ![Pipeline](./images/jenkins_Pipeline.png)


