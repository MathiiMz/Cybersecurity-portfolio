# Splunk SOC Labs

Este repositorio documenta ejercicios prácticos de análisis de eventos de seguridad realizados en un laboratorio SOC con Splunk, enfocados en detección, monitoreo y validación de actividad sospechosa en entornos Linux.

## Objetivo

Desarrollar experiencia práctica en:

- ingestión y análisis de logs
- detección de eventos de seguridad
- correlación de actividad
- triage y validación de alertas
- documentación técnica de hallazgos

## Entorno de laboratorio

- SIEM: Splunk Enterprise
- Forwarding: Splunk Universal Forwarder
- Sistemas monitoreados: Linux (Ubuntu Server)
- Escenarios simulados: autenticación, privilegios, ejecución de procesos, actividad sospechosa y validación de fuentes de datos

## Casos documentados

### 1. Brute Force SSH
Detección de intentos repetidos de autenticación fallida sobre servicio SSH.

### 2. Privilege Escalation
Monitoreo de uso de privilegios elevados y cambios de contexto a root.

### 3. Suspicious Process Execution
Visibilidad sobre ejecución de procesos en Linux mediante auditoría.

### 4. Suspicious Download Activity
Detección de herramientas asociadas a descarga remota y comunicación externa.

### 5. DNS Visibility Gap
Documentación de limitaciones de visibilidad para monitoreo de actividad DNS.

### 6. Log Source Validation & False Positive Analysis
Validación de eventos inicialmente sospechosos y clasificación analítica de falsos positivos.

## Habilidades aplicadas

- Splunk SPL
- Linux logging
- análisis de autenticación
- triage de eventos
- correlación de actividad
- documentación técnica
- validación de fuentes de datos

## Nota

Todos los ejercicios fueron realizados en entorno de laboratorio controlado con fines de aprendizaje, práctica técnica y fortalecimiento de capacidades orientadas a roles SOC / Blue Team.
