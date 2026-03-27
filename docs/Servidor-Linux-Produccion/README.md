# Servidor Linux de Produccion
Este servidor cumple la función de servidor de produccion. En el mismo vamos a correr programas vulnerables a drede para poder testear alertas.
El manejo del codigo va a ser a través de un contenedor con Gitea. Esto podría ser manejado en un servidor a parte, pero por limite de hardware, va a correr como un servicio en docker. También podría ser manejado con Github directamente, pero Gitea nos va a permitir practicar usando webhooks con Jenkins.
Ademas de los repos, Gitea y wazuh agent, este servidor va a correr las automatizaciónes CI/CD y controles de seguridad usando Jenkins.
El enrutamiento entre los contenedores van a ser manejados con Docker y traefik como reverse proxy.

## Tabla de Contenidos
* [Wazuh Agent](#Wazuh-Agent)
* [Docker](#Docker)
* [Traefik](#Traefik)
* [Gitea](Gitea)
* [Jenkins](#Jenkins)


## Wazuh Agent
Ingresamos via ssh desde alguna de las terminales y una vez adentro ingresamos al browser accediendo a wazuh y launcheando un nuevo agente como las veces anteriores


En mi caso esto no fue suficiente, la variable se creo sin la ip del servidor de seguridad, lo solucione entrando al archivo y configurandolo yo mismo:
(`sudo nano /var/ossec/etc/ossec.conf`)
y cambiando "<address>MANAGER_IP</address>" con la ip del servidor de seguridad.


## Docker
 (`sudo apt install docker.io docker-compose-v2 -y
sudo usermod -aG docker prodadmin`)

## Traefik

## Gitea

## Jenkins
