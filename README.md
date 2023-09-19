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

## Paso 3: Configurar SSH

Abre el archivo de configuración de SSH para realizar modificaciones:

```bash
nano /etc/ssh/sshd_config
```

Dentro del archivo, busca las siguientes líneas y modifícalas según se indica a continuación:

```bash
PermitRootLogin yes
PasswordAuthentication yes
```

Guarda los cambios y luego continúa con el Paso 3. Esto permitirá la autenticación de contraseña para el usuario root y habilitará el inicio de sesión como root a través de SSH. Asegúrate de reiniciar el servicio SSH después de realizar estos cambios:

```bash
systemctl restart sshd
```

## Paso 4: Cambiar la contraseña de Root

Para cambiar la contraseña del usuario root, usa el siguiente comando y sigue las instrucciones:

```bash
passwd root
```

## Paso 5: Desactivar SELinux y el Firewall

Desactiva SELinux temporalmente y el firewall con los siguientes comandos:

```bash
setenforce 0
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/sysconfig/selinux
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
systemctl disable firewalld
```

## Paso 6: Actualizar el Kernel y Git

Asegúrate de que tu sistema tenga el kernel y Git actualizados para continuar con la instalación:

```bash
yum update -y && yum install kernel-devel git -y
```

## Paso 7: Instalar Python y pip

Instala Python 3 y pip3 en tu sistema:

```bash
yum install epel-release -y && yum install python3-pip python3 -y
pip3 install --upgrade pip
```

## Paso 8: Instalar Ansible

Instala Ansible en tu sistema con el siguiente comando:

```bash
pip3 install setuptools_rust
pip3 install 'ansible==2.9.2' --user
```

## Paso 9: Verificar el Kernel y las Dependencias

Antes de continuar, verifica la versión del kernel y la presencia de las dependencias necesarias con los siguientes comandos:

```bash
uname -r
rpm -qa | grep kernel-devel
```

## Paso 10: Instalar Completado Automático

Instala el completado automático de Bash con los siguientes comandos:

```bash
yum install bash-completion bash-completion-extras -y
```
