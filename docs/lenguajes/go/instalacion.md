# Tutorial de Instalación de Go (Golang) en Ubuntu

## Requisitos Previos
- Sistema operativo Ubuntu o derivados
- Conexión a internet
- Permisos de administrador (sudo)

## Pasos de Instalación

### 1. Actualizar Paquetes del Sistema
Abre una terminal y ejecuta los siguientes comandos:

```bash
sudo apt update && sudo apt upgrade
```

### 2. Descargar Go
Visita [golang.org/dl/](https://golang.org/dl/) y descarga la última versión para Linux. En el momento de este tutorial, usaremos la versión 1.22.1:

o puedes descargar desde terminal

```bash
wget https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
```

### 3. Extraer el Archivo Descargado
```bash
sudo tar -C /usr/local -xzf go1.23.4.linux-amd64.tar.gz
```

### 4. Configurar Variables de Entorno
Abre tu archivo de configuración de shell:

```bash
nano ~/.bashrc
```

Agrega las siguientes líneas al final del archivo:

```bash
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

### 5. Aplicar los Cambios
```bash
source ~/.bashrc
```

### 6. Verificar la Instalación
```bash
go version
```

## Solución de Problemas Comunes

- **Problema:** No se encuentra el comando `wget`
  - **Solución:** Instalar wget
    ```bash
    sudo apt install wget
    ```

- **Problema:** Permisos denegados
  - **Solución:** Verificar que estás usando `sudo` cuando sea necesario
  - Asegurarse de tener permisos de administrador

- **Problema:** Espacio insuficiente
  - **Solución:** Verificar espacio disponible en /usr/local
    ```bash
    df -h /usr/local
    ```

## Desinstalación

Para desinstalar Go:
1. Eliminar el directorio de Go:
```bash
sudo rm -rf /usr/local/go
```

2. Eliminar las líneas añadidas en `~/.bashrc`:
```bash
# Eliminar estas líneas
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

## **PATH**:  Explicación de los comandos a continuación

```
export GOROOT=/usr/local/go
```

Define la ubicación de la instalación de **Go**,
Es el directorio donde se instalan los archivos binarios y herramientas de **Go**
Normalmente es **/usr/local/go** cuando instalas **Go** manualmente

```
export GOPATH=$HOME/go
```

Define el directorio de trabajo para proyectos Go, **$HOME** es tu directorio de usuario (generalmente /home/tu_usuario)
Contiene tres subdirectorios:

- **src/:** Código fuente de tus proyectos

- **pkg/:** Paquetes compilados

- **bin/:** Ejecutables binarios



```
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

Añade los directorios de binarios de Go a tu PATH
Permite ejecutar comandos de Go desde cualquier lugar
$GOROOT/bin: Herramientas del sistema Go
$GOPATH/bin: Ejecutables de tus proyectos Go

3. Aplicar cambios:
```bash
source ~/.bashrc
```

## Recursos Adicionales
- Documentación oficial de Go: [golang.org/doc/](https://golang.org/doc/)
- Repositorio de Go en GitHub: [github.com/golang/go](https://github.com/golang/go)

>**NOTA:** Asegúrate de tener la última versión de Go instalada. Verifica periódicamente actualizaciones en el sitio oficial.