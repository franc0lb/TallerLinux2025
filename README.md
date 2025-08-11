# TallerLinux2025

# **Como usar los playbooks:**

Primero debemos instalar los complementos necesarios para que los playbooks funcionen.

## **Instalar complementos:**

*ansible-galaxy collection install -r  collections/requeriments.yaml*

## **Playbook para NFS:**

**Para ejecutar playbook nfs_setup.yml:**

*ansible-playbook playbooks/nfs_setup.yml -K*

**Este playbook se aplica para el grupo centos y se encarga de:**
- El servidor NFS esté instalado
- Se asegura que el servicio NFS esté iniciado y funcionando 
- Se asegura que el firewall permita conexiones al puerto 2049
- Se asegura que exista el directorio /var/nfs_shared, que pertenece al usuario/grupo nobody/nobody y tiene permisos 777.
- Que el directorio está compartido por NFS. 
- Se crea un handler que reinicia el servicio de nfs y ejecuta el exportfs -r si /etc/exports cambia.

## **Playbook para Hardening:**

**Para ejecutar playbook hardering.yaml:**

*ansible-playbook playbooks/hardering.yaml -K*

**Este playbook se aplica para el grupo ubuntu y se encarga de:**
- Actualizar todos los paquetes 
- Que esté habilitado ufw, bloqueando todo el tráfico entrante y permitiendo solo ssh. 
- Que solo se pueda hacer login con clave pública, y que root no pueda hacer login. 
- Que esté instalado fail2ban y bloquee intentos fallidos de conexión SSH. El servicio debe quedar habilitado y activado. 
- Ejecuta un handler que reinicia el sistema si se actualizan paquetes. 
- Ejecuta un handler que reinicia ssh si cambia la configuración.

