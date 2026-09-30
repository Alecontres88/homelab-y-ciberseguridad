# Auditoría de Seguridad y Explotación con Nmap y Metasploit

## Descripción del Proyecto
Simulación controlada de un test de intrusión (pentesting) sobre una máquina vulnerable en un entorno de laboratorio aislado. El objetivo es identificar vectores de ataque, explotar servicios desactualizados y obtener acceso al sistema para evaluar el impacto real de las vulnerabilidades.

## Tecnologías y Conceptos
- **Enumeración:** Nmap (Escaneo de puertos, detección de versiones y scripts NSE).
- **Explotación:** Metasploit Framework.
- **Fuerza Bruta:** Crunch (generación de diccionarios) e Hydra (ataques a servicios de red).
- **Fases:** Reconocimiento, Explotación, Escalada de Privilegios.

## Fases de la Auditoría
1. **Reconocimiento y Enumeración:** Escaneo exhaustivo de la red objetivo con Nmap para descubrir puertos abiertos, servicios en ejecución y sistemas operativos.
2. **Fuerza Bruta Controlada:** Creación de listas de palabras personalizadas con Crunch y ejecución de ataques de autenticación contra servicios expuestos utilizando Hydra.
3. **Explotación:** Selección, configuración y lanzamiento del exploit adecuado dentro de Metasploit para comprometer el servicio vulnerable.
4. **Post-Explotación:** Obtención de una sesión remota (Meterpreter) para interactuar con el sistema comprometido, demostrando el impacto sin alterar la disponibilidad del servicio.

### Ejemplo de Ejecución: Escaneo de Vulnerabilidades
Comando de Nmap utilizado en la fase inicial de reconocimiento para detectar versiones exactas de los servicios y ejecutar los scripts de auditoría predeterminados:

```bash
nmap -p- -sV -sC -O -T4 192.168.1.100 -oN escaneo_inicial.txt
```

## Valor Técnico
Esta auditoría demuestra capacidad técnica para:
- Ejecutar metodologías estructuradas de seguridad ofensiva.
- Identificar y validar vulnerabilidades en infraestructuras de red.
- Manejar frameworks de explotación profesional comprendiendo el punto de vista del atacante.
