# Docker en 20 minutos

---

# Demo

---

## ¿Qué es Docker?

- Herramienta de *devels*, más que de *sistema*

## ¿Qué NO es Docker?

- NO equivale a una VM

---

## ¿Cómo lo consigue?

- Trucos de kernel (LXC)
- + formato portable de imágenes
- + build automático
- + versionado
- + facilita el reuso (imagen padre)
- + facilita compartir

--- 

### Imágenes


```python
# ~/fabfile.py

from fabric.api import *

env.hosts = ['test.example.org']
env.user  = 'bob'

def remote_info():
    run('uname -a')

def local_info():
    local('uname -a')
```
