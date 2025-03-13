# PYSAXSAY

Complemento de proyecto SAXSAY (.NET) para procesos que exploten las cualidades de `python` (ejm: automatización y análisis de datos).


---
### Errores Identificados (podman)

Si usa containerización con Docker probablemente no tenga los inconvenientes detallados a continuación. Esto problemas aparecen al usar Podman como gestor de containers.

#### CNI Config

[2025-03-12]
Hay un error que aparece en algunas versiones de **podman** relacionado al network de podman.

> WARN[0000] Error validating CNI config file /home/xxxxxx/.config/cni/net.d/container_default.conflist: [plugin firewall does not support config version "1.0.0"]

En mi caso, tuve que lidiar con este error que se presentó en una instalación de `podman 3.4.4` sobre la distribución `pop! OS 22.04 LST` que estaba usando en ese momento.<br>La solución fue actualizar el paquete `containernertworking-plugins` a una versión superior. La solución la encontré en los foros de reporte de errores de Ubuntu. Enlace al comentario con la solución [[🔗 Enlace](https://bugs.launchpad.net/ubuntu/+source/libpod/+bug/2024394/comments/16)].

```bash
# cambiar ruta de trabajo
cd ~/Downloads
# descargar plugin de repositorio
curl -O http://archive.ubuntu.com/ubuntu/pool/universe/g/golang-github-containernetworking-plugins/containernetworking-plugins_1.1.1+ds1-3build1_amd64.deb
# comando de instalación
dpkg -i containernetworking-plugins_1.1.1+ds1-3build1_amd64.deb
# al finaliza eliminar instalador
rm containernetworking-plugins_1.1.1+ds1-3build1_amd64.deb
```