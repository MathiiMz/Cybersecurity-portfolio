# Brute Force SSH – Linux + Splunk

## Objetivo

Detectar intentos repetidos de autenticación fallida sobre un servicio SSH en un sistema Linux, simulando un posible ataque de fuerza bruta orientado a acceso inicial.

## Escenario

Se generaron múltiples intentos fallidos de autenticación SSH contra un servidor Linux con el fin de validar la visibilidad de eventos de acceso y su detección desde Splunk.

El objetivo fue identificar:

- múltiples fallos de autenticación
- repetición de intentos sobre una misma cuenta
- posible actividad de acceso no autorizada

## Arquitectura

- Kali Linux (simulación ofensiva controlada)
- Ubuntu Server (víctima / fuente de logs)
- Splunk Enterprise (SIEM)
- Splunk Universal Forwarder

## Fuente de datos

- `/var/log/auth.log`
- `sourcetype=Ubuntu-Victima`
- `index=main`

## Implementación técnica

### 1. Recolección de logs

Se configuró Splunk Forwarder en el servidor Linux para enviar logs de autenticación hacia Splunk.

### 2. Validación de eventos

Se verificó la llegada de eventos asociados a autenticación SSH fallida.

## Simulación / generación de eventos

Se realizaron múltiples intentos fallidos de acceso SSH con credenciales incorrectas contra el servidor Linux.

Ejemplo de actividad generada:

```bash
ssh usuario@IP_DEL_SERVIDOR
