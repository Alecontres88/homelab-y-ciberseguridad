# Arquitectura Defensiva y Contenerización (Homelab)

## Descripción del Proyecto
Diseño y despliegue de un entorno de laboratorio local (Homelab) sobre hardware de bajo consumo. El objetivo es alojar servicios de forma segura, aislar entornos de pruebas mediante contenedores y aplicar filtrado de red para bloquear dominios maliciosos a nivel de infraestructura.

## Entorno y Tecnologías
- **Hardware:** Raspberry Pi 3 Model B+.
- **Orquestación:** Docker y Docker Compose.
- **Seguridad de Red:** Pi-hole (Sinkhole DNS).
- **Sistema Operativo:** Linux (Raspberry Pi OS / Debian).

## Fases del Despliegue
1. **Hardening del Host:** Actualización del sistema base, cambio de puertos SSH por defecto y configuración de acceso exclusivo mediante claves criptográficas.
2. **Estructura de Contenedores:** Instalación del motor de Docker y creación de redes virtuales tipo *bridge* para aislar el tráfico de los distintos servicios desplegados.
3. **Filtrado DNS Perimetral:** Despliegue del contenedor de Pi-hole, configurándolo como el servidor DNS principal del router local para interceptar y bloquear peticiones a dominios de telemetría y malware.
4. **Monitorización:** Revisión periódica de los registros de consulta (Query Log) para identificar anomalías en el tráfico saliente de los dispositivos de la red.

### Ejemplo de Configuración: Despliegue de Pi-hole
Extracto del archivo `docker-compose.yml` utilizado para levantar el servicio de filtrado DNS de forma persistente y aislada:

```yaml
version: "3"
services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "80:80/tcp"
    environment:
      TZ: 'Europe/Madrid'
      WEBPASSWORD: 'tu_contraseña_segura'
    volumes:
      - './etc-pihole:/etc/pihole'
      - './etc-dnsmasq.d:/etc/dnsmasq.d'
    restart: unless-stopped
```

## Valor Técnico
Este despliegue demuestra capacidad para:
- Diseñar e implementar infraestructuras locales autohospedadas.
- Administrar contenedores y aplicar persistencia de datos con Docker.
- Mejorar la seguridad de una red mediante la inspección y filtrado de tráfico DNS.
