# Manual de Instalación de OmniLeads

Este es un manual de instalación paso a paso para configurar OmniLeads en un servidor Linux. Asegúrate de seguir cuidadosamente cada uno de los pasos a continuación.

## Requisitos Previos

- Sistema operativo Linux (CentOS 7 se utiliza en este ejemplo).
- Acceso de superusuario (root) o permisos sudo.
- Conexión a Internet.

## Paso 1: Actualizar el Sistema

```bash
yum update
yum upgrade

Paso 2: Instalar Dependencias

yum install nano net-tools wget epel-release

Paso 3: Desactivar SELinux y el Firewall

setenforce 0
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/sysconfig/selinux
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
systemctl disable firewalld


