# Monitoreo de infraestructura con Nagios

## Instalación de Nagios
En este repositorio se encuentra un archivo de configuración Vagrantfile, el cual contiene una máquina tipo servidor la cual es la que contiene el software de Nagios y 3 máquinas más que contienen diferentes servicios para ser monitoreados.
La instalación de Nagios se hace automáticamente en el aprovisionamiento de la máquina por lo que no debe preocuparse por su instalación, de igual forma si desea hacerlo manualmente bastará con ejecutar solo el siguiente comandos:
```bash
curl https://assets.nagios.com/downloads/nagiosxi/install.sh | sh
```
La instalación será administrada completamente por Nagios, al final nos queda la url para ingresar a la plataforma. Ya con la aplicación abierta en un navegador web, procedemos a crear un usuario y contraseña para ingresar, con esto tendremos ya disponible Nagios para su utilización.

## Servicios
Los servicios que se utilizan para probar Nagios, también se instalan y configuran por medio del aprovisionamiento del Vagrantfile. En este caso usamos FTP, HTTP, Linux Server
Por temas de demostración una de las máquinas llamada Cliente, tendrá un servicio particular el cual es una herramienta de Nagios la cual permitirá monitorizar todo el servidor, esta herramienta está incluida en el aprovisionamiento. Lo único que debemos realizar adicional es colocar un token personalizado en esta máquina cliente para que Nagios se pueda conectar. El archivo que se debe modificar en el Cliente es:
```bash
vim /usr/local/ncpa/etc/ncpa.cfg
#modificar en:
#community_string =MiTokenSecreto

#Se debe reiniciar el servicio
systemctl restart ncpa_listener.service
```
Con lo anterior ya tenemos todo el entorno de Nagios configurado y las diferentes máquinas y servicios que serán monitoreados.
