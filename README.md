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
```

## Paso 2: Instalar Dependencias

Instala las dependencias necesarias con el siguiente comando:

```bash
yum install nano net-tools wget epel-release
```

## Paso 3: Desactivar SELinux y el Firewall

Desactiva SELinux temporalmente y el firewall con los siguientes comandos:

```bash
setenforce 0
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/sysconfig/selinux
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
systemctl disable firewalld
```

## Paso 4: Actualizar el Kernel y Git

Asegúrate de que tu sistema tenga el kernel y Git actualizados para continuar con la instalación:

```bash
yum update -y && yum install kernel-devel git -y
```

## Paso 5: Instalar Python y pip

Instala Python 3 y pip3 en tu sistema:

```bash
yum install epel-release -y && yum install python3-pip python3 -y
pip3 install --upgrade pip
```

## Paso 6: Instalar Ansible

Instala Ansible en tu sistema con el siguiente comando:

```bash
pip3 install setuptools_rust
pip3 install 'ansible==2.9.2' --user
```

## Paso 7: Verificar el Kernel y las Dependencias

Antes de continuar, verifica la versión del kernel y la presencia de las dependencias necesarias con los siguientes comandos:

```bash
uname -r
rpm -qa | grep kernel-devel
```
