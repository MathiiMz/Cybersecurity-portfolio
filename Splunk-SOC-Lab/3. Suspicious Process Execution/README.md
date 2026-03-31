# Caso 03 — Suspicious Process Execution

## Resumen
Se implementó visibilidad de ejecución de procesos en Linux mediante `auditd`, permitiendo detectar actividad a nivel sistema que no era observable en logs tradicionales como `auth.log` o `syslog`.

## Objetivo
Simular y detectar ejecución de procesos potencialmente sospechosos en un endpoint Linux mediante auditoría de sistema e integración con Splunk.

## Escenario
En entornos Linux, muchas acciones relevantes para seguridad no quedan registradas en logs de autenticación.  
Para cubrir esta limitación, se habilitó auditoría de procesos con `auditd`, generando trazabilidad de comandos ejecutados en la máquina víctima.

## Fuente de datos
- `/var/log/audit/audit.log`
- `index=main`
- `sourcetype=linux_audit`

## Implementación
Se instaló y habilitó `auditd` en la máquina Ubuntu víctima.
Luego se configuró una regla de auditoría para registrar ejecución de procesos (`execve`) y se integró el archivo `audit.log` al Splunk Universal Forwarder.

## Detección principal
Se validó la llegada de eventos tipo `EXECVE` a Splunk, confirmando visibilidad sobre ejecución de procesos y argumentos utilizados.

## Hallazgos
- Fue posible observar procesos ejecutados a nivel sistema.
- Los eventos mostraron argumentos asociados a cada ejecución.
- Se logró ampliar la cobertura de monitoreo más allá de autenticación y privilegios.

## Impacto
Este caso mejora significativamente la capacidad de detección en Linux, permitiendo observar actividad relevante para:
- ejecución sospechosa
- herramientas de administración
- comportamiento post-explotación
- actividad fuera de flujos normales de usuario

## Clasificación
Detección válida / mejora de visibilidad

## Recomendaciones
- Mantener auditoría de procesos en endpoints críticos
- Correlacionar ejecución de procesos con autenticación y privilegios
- Priorizar comandos de alto riesgo o uso poco frecuente
