# Despliegue de SD-WAN y Perfiles de Seguridad en FortiGate (CLI)

## Descripción del Proyecto
Configuración de una infraestructura de red segura y de alta disponibilidad utilizando un firewall FortiGate. Todo el despliegue se ha realizado mediante la interfaz de línea de comandos (CLI). 

El objetivo principal es garantizar la continuidad del servicio mediante SD-WAN y aplicar filtrado de seguridad al tráfico de salida.

## Tecnologías y Conceptos
- **Dispositivo:** FortiGate (FortiOS).
- **Gestión:** Acceso por consola (CLI).
- **Redes:** SD-WAN, LinkMonitor, enrutamiento dinámico/estático.
- **Seguridad:** Perfiles UTM (Antivirus, Web Filtering, IPS).

## Fases de la Configuración
1. **Configuración de Interfaces:** Asignación de direccionamiento IP y zonas de seguridad para las redes internas y externas.
2. **Alta Disponibilidad (SD-WAN):** Creación de una zona SD-WAN agrupando varias interfaces de salida. 
3. **Monitorización de Enlaces:** Configuración de *LinkMonitor* para detectar caídas de red y redirigir el tráfico automáticamente sin cortes de servicio.
4. **Políticas de Firewall:** Creación de reglas IPv4 desde la terminal, aplicando perfiles de seguridad para inspeccionar el tráfico permitido.

### Ejemplo de Configuración: LinkMonitor
A continuación, un extracto de los comandos utilizados para configurar el monitor de estado de los enlaces SD-WAN, asegurando el failover automático ante caídas:
```
config system link-monitor
    edit "Monitor_WAN"
        set srcintf "sdwan"
        set server "8.8.8.8" "1.1.1.1"
        set protocol ping
        set gateway-ip 192.168.1.1
        set update-cascade-interface enable
        set update-static-route enable
    next
end
````
## Valor Técnico
Este despliegue demuestra capacidad para:
- Administrar firewalls corporativos directamente desde la terminal.
- Diseñar arquitecturas de red con tolerancia a fallos.
- Implementar controles de seguridad perimetral.
