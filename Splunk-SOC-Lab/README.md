# SOC Lab – Splunk Detection Engineering

## Objetivo

Diseñar e implementar un laboratorio SOC para simular escenarios de seguridad ofensiva controlada y desarrollar capacidades de monitoreo, detección, correlación y triage en Splunk.

## Arquitectura del laboratorio

**Flujo de telemetría:**

Kali (ataque controlado) → Ubuntu Server (víctima / logs) → Splunk Universal Forwarder → Splunk Enterprise (SIEM)

## Componentes utilizados

- Kali Linux
- Ubuntu Server
- Splunk Enterprise
- Splunk Universal Forwarder
- Linux auth logs
- Linux auditd

## Capacidades implementadas

- Centralización de logs Linux
- Monitoreo de autenticación SSH
- Detección de patrones sospechosos de login
- Monitoreo de uso de privilegios
- Auditoría de ejecución de procesos
- Correlación de eventos de autenticación y post-explotación
- Dashboards operativos en Splunk
- Identificación de gaps de visibilidad en telemetría

## Casos desarrollados

### Caso 1 – Fuerza bruta SSH
Detección de múltiples intentos fallidos de autenticación desde una misma IP.

### Caso 2 – Patrón sospechoso de autenticación
Detección de secuencia repetitiva fail → success, consistente con validación de credenciales.

### Caso 3 – Escalamiento de privilegios
Análisis de eventos sudo y uso de privilegios elevados posterior a autenticación.

### Caso 4 – Actividad post-explotación
Correlación de eventos posteriores al login para identificar comportamiento anómalo.

### Caso 5 – Gap de visibilidad DNS
Análisis de limitaciones en trazabilidad DNS y documentación de brecha de monitoreo.

### Caso 6 – Ejecución sospechosa de herramientas de red
Monitoreo de ejecución de procesos mediante auditd para identificar actividad asociada a descarga remota o comunicación externa.

## Habilidades demostradas

- Análisis de logs
- Detección basada en eventos
- Triage
- Correlación
- Documentación técnica
- Enfoque SOC junior
- Validación de falsos positivos
- Identificación de brechas de monitoreo
