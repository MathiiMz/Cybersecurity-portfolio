# Detección en Splunk — Caso 02: Escalamiento de privilegios con sudo

## Búsqueda base

``index=main sourcetype=Ubuntu-Victima "sudo:"``

### Objetivo
Visualizar eventos relacionados con uso de privilegios elevados mediante sudo.

Detección de comandos ejecutados con privilegios
``index=main sourcetype=Ubuntu-Victima "COMMAND="``

### Objetivo
Identificar comandos ejecutados con privilegios elevados dentro del sistema.

## Conteo por usuario

``index=main sourcetype=Ubuntu-Victima "sudo:"
| stats count by user
| sort - count``

### Objetivo
Determinar qué usuarios ejecutaron más acciones privilegiadas.

## Conteo temporal

``index=main sourcetype=Ubuntu-Victima "sudo:"
| timechart count``

### Objetivo
Visualizar actividad de escalamiento de privilegios en el tiempo.

### Hallazgos
Se observaron ejecuciones de comandos mediante sudo.
Fue posible identificar elevación de privilegios y sesiones asociadas.
La visibilidad permitió reconstruir actividad administrativa y potencialmente sospechosa.

### Clasificación
Detección válida / actividad privilegiada observable

### Valor analítico
Este caso permitió practicar:
  - monitoreo de privilegios
  - análisis de elevación de permisos
  - revisión de comandos administrativos
  - diferenciación entre actividad legítima y sospechosa
  - visibilidad de post-explotación

### Limitaciones
- Laboratorio controlado
- Sin integración con PAM avanzado o EDR
- Contexto limitado al host

### Lecciones aprendidas
- Los eventos de sudo son altamente relevantes para detectar abuso de privilegios.
- El contexto del comando ejecutado es clave para distinguir administración legítima de actividad maliciosa.

# Evidencia — Caso 02: Escalamiento de privilegios con sudo

## Actividad simulada
Se ejecutaron comandos privilegiados mediante sudo para generar trazabilidad asociada a elevación de permisos.

## Evidencia observada
- Los eventos fueron visibles en `auth.log`.
- Splunk permitió identificar apertura de sesiones privilegiadas.
- Fue posible observar comandos ejecutados bajo contexto root.

## Evidencia recomendada en capturas
- Eventos crudos de `sudo:`
- Comandos con `COMMAND=`
- Línea temporal de actividad
- Tabla por usuario

## Conclusión
La telemetría permitió identificar correctamente eventos de escalamiento de privilegios y analizar su contexto operativo.
