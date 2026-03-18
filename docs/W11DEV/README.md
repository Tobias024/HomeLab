# HOST 1: Dev
En esta maquina vamos a configurar uno de nuestros Hosts. Este Host va a cumplir el roll de Desarrollador quien va a empujar a main los repos que trigerearán las automatizaciones que vamos a configurar para la ravision del codigo y auto-deploydeo.
Ademas del Wazuh agent a vincular para llevar control de posibles alarmas.

## Primeras configuraciones
Configuramos la maquina virtual para que esté dentro de la VLAN de DEV yendo a las configuraciones, y en la seccion de "Red", en el adaptador 1 asignamos conectar a Red interna y el nombre de la VLAN_20_DEV.

## Agregado al AD
