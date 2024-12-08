---
## **Configuración de Rotación de Logs de Docker**
---

### Problema de Almacenamiento

Los logs de Docker pueden llenar rápidamente el sistema de archivos si no se configuran correctamente.

### Configuración del Archivo de Logs

1. **Crear/Editar el archivo de configuración**:

   ```bash
   sudo nano /etc/docker/daemon.json
   ```

2. **Contenido del archivo de configuración**:

   ```json
   {
     "log-driver": "json-file",
     "log-opts": {
       "max-size": "10m",
       "max-file": "3"
     }
   }
   ```

### Explicación de la Configuración

- `max-size: "10m"`: Limita cada archivo de log a 10 megabytes.
- `max-file: "3"`: Mantiene un máximo de 3 archivos de log.
- Esto previene que los logs consuman todo el espacio en disco.
- Evita posibles problemas con imágenes y contenedores.

### Verificación

Después de configurar, puedes verificar la configuración ejecutando:

```bash
docker ps -a
```

>**Nota importante**: Recuerda reiniciar el servicio de Docker después de modificar la configuración:

```bash
sudo systemctl restart docker
```