# Docker 
## en solo 20 minutos

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
  + formato portable de imágenes
  + build automático
  + versionado
  + facilita el reuso (imagen padre)
  + facilita compartir

--- 

### Ejemplo con migración Wedip

853117510175.dkr.ecr.eu-central-1.amazonaws.com/wedip

---

### Entorno de staging:

```yaml
wedip:
  volumes:
    - ./wedip_config:/var/www/Main/config
    - ./ssl:/etc/apache2/ssl
  ports:
    - 8081:80
  image: 853117510175.dkr.ecr.eu-central-1.amazonaws.com/wedip
```
---

### Entorno de producción: 

```yaml
wedip:
  volumes:
    - /etc/localtime:/etc/localtime:ro
    - /home/ubuntu/docker/ssl:/etc/apache2/ssl
    - ./wedip_config:/var/www/Main/config
    - /home/ubuntu/medip-cloud-data/wedip/reports:/var/www/Wedip_Report/php/pdf
  environment:
    - VIRTUAL_HOST=wedip.mediphealth.com
    - VIRTUAL_PROTO=https
    - VIRTUAL_PORT=443
  image: 853117510175.dkr.ecr.eu-central-1.amazonaws.com/wedip

vpn:
  volumes:
    - ./vpn_config:/etc/openvpn
  net: container:wedip
  devices:
    - /dev/net/tun:/dev/net/tun
  cap_add:
    - NET_ADMIN
  command: gateway-hospitales.ovpn
  image: 853117510175.dkr.ecr.eu-central-1.amazonaws.com/openvpn
```
