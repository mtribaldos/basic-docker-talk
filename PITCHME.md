# Docker en 20 minutos

---

## Demo

#### dockersamples/static-site

---

## ¿Qué es Docker?

- Herramienta orientada a *devels*

## ¿Qué NO es Docker?

- No es una máquina virtual
- No está orientada a *sysops*

---

## ¿Cómo lo consigue?

- Trucos de kernel (LXC)
- + formato portable de imágenes
- + build automático
- + versionado
- + facilita el reuso (imagen padre)
- + facilita compartir

--- 

### Ejemplo con migración Wedip

853117510175.dkr.ecr.eu-central-1.amazonaws.com/wedip

---

### Entornos de ejecución:

```
# ~/fabfile.py

from fabric.api import *

env.hosts = ['test.example.org']
env.user  = 'bob'

def remote_info():
    run('uname -a')

def local_info():
    local('uname -a')
```
