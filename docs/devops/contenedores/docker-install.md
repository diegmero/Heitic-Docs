# Guía de Instalación de Docker en Linux (Ubuntu y Derivadas)

Docker es una herramienta popular para crear, implementar y ejecutar aplicaciones en contenedores. Sigue estos pasos para instalar Docker en sistemas Ubuntu y distribuciones basadas en Debian.

---

## **Paso 1: Actualizar el sistema**
Antes de comenzar, asegúrate de que el sistema esté actualizado:

```bash
sudo apt update
sudo apt upgrade -y
```

---

## **Paso 2: Instalar usando el apt repositorio**

Antes de instalar Docker Engine por primera vez en una nueva máquina host, debe configurar el aptrepositorio de Docker. Luego, puede instalar y actualizar Docker desde el repositorio.

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
>**Nota:** Si utiliza una distribución derivada de Ubuntu, como Linux Mint, es posible que necesite utilizar UBUNTU_CODENAMEen lugar de VERSION_CODENAME.

---

## **Paso 3: Instalar los paquetes de Docker**
1. Para instalar la última versión, ejecute:


   ```bash
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

 
## **Paso 4: Verificar la instalación**
Comprueba que Docker se instaló correctamente ejecutando:

```bash
docker --version
```

## **Paso 5: Ejecutar Docker sin permisos de sudo (opcional)**
Si deseas usar Docker sin anteponer `sudo`, añade tu usuario al grupo `docker`:

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
```

---

## **Paso 6: Probar Docker**
Ejecuta un contenedor de prueba para verificar que Docker funciona correctamente:

```bash
docker run hello-world
```

Si todo está configurado correctamente, verás un mensaje indicando que Docker se instaló y funciona.

---

**¡Listo!** Ahora tienes Docker instalado y listo para usar en tu sistema Linux.
> **Nota**: Después de seguir estos pasos, podrás ejecutar comandos de Docker sin necesidad de utilizar `sudo`, lo que simplifica significativamente tu trabajo con contenedores.
