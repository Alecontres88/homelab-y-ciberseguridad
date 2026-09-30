# Forense de Sistemas de Archivos con Autopsy

## Descripción del Proyecto
Análisis forense de una imagen de disco para identificar artefactos de compromiso, reconstruir la línea temporal de un incidente y recuperar información eliminada. El proceso simula una investigación formal manteniendo las buenas prácticas de la cadena de custodia.

## Entorno y Tecnologías
- **Herramienta principal:** Autopsy (The Sleuth Kit).
- **Evidencia:** Imagen de disco en formato RAW (.dd) o EnCase (.E01).
- **Integridad:** Utilidades de validación de hashes criptográficos (MD5/SHA256).

## Fases de la Investigación
1. **Preservación de Evidencia:** Verificación de la integridad de la imagen de disco original mediante el cálculo de hashes antes de iniciar el análisis.
2. **Análisis de Línea Temporal:** Uso del módulo *Timeline* para correlacionar la creación de archivos sospechosos con eventos del sistema y ejecuciones de malware.
3. **Recuperación de Datos:** Extracción de archivos ocultos, ejecutables eliminados, historiales de navegación y correos electrónicos utilizando los módulos de ingestión.
4. **Reporte:** Exportación de marcadores y hallazgos clave a un informe técnico estructurado.

### Ejemplo: Verificación de Integridad Inicial
Antes de procesar e ingerir cualquier imagen forense en Autopsy, es crítico asegurar que la evidencia no ha sido alterada. Este comando genera el hash de verificación:

```bash
sha256sum evidencia_disco.dd > hash_original.txt
```

## Valor Técnico
Este proyecto demuestra capacidad analítica para:
- Mantener la integridad de los datos en investigaciones críticas.
- Navegar e interpretar artefactos a nivel de sistema de archivos y registros.
- Reconstruir los pasos de un atacante tras la vulneración de un endpoint.
