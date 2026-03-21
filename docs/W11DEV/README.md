# HOST 1: Dev
En esta maquina vamos a configurar uno de nuestros Hosts. Este Host va a cumplir el roll de Desarrollador quien va a empujar a main los repos que trigerearán las automatizaciones que vamos a configurar para la ravision del codigo y auto-deploydeo.
Ademas del Wazuh agent a vincular para llevar control de posibles alarmas.

## Primeras configuraciones
Configuramos la maquina virtual para que esté dentro de la VLAN de DEV yendo a las configuraciones, y en la seccion de "Red", en el adaptador 1 asignamos conectar a Red interna y el nombre de la VLAN_20_DEV.

## Agregado al AD
Primero corroboramos que la pc encuentre el dominio haciendo: nslookup lab.local.

Sabemos que todo está en orden dado a que devuelve la IP del Windows Server (10.0.10.2)
<img width="497" height="414" alt="image" src="https://github.com/user-attachments/assets/06643bae-26c5-458e-8da7-038d3371755a" />

Si dijera "Non-existent domain", El DNS no estaría llegando y la unión va a fallar. Por lo que tendríamos que revisar el Scope del DHCP en el AD para confirmar que el DNS primario sea la 10.0.10.2.
Ahora:
1. Buscamos "Configuración avanzada del sistema" (o sysdm.cpl en el buscador y dale Enter).
2. En "Propiedades del sistema". Clickeamos la pestaña Nombre de equipo.
3. Abajo, donde dice "Para cambiar el nombre de este equipo o unirse a un dominio...", clikeamos en "Cambiar".
4. En "Miembro de", seleccionamos en Dominio: lab.local. y damos a "aceptar"
