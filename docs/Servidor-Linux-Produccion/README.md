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
Usamos el siguiente codigo de wazuh:
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --dearmor | sudo tee /usr/share/keyrings/wazuh.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
sudo apt-get update
WAZUH_MANAGER='10.0.10.100' sudo apt-get install wazuh-agent -y
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent

## Docker

## Traefik

## Gitea

## Jenkins
