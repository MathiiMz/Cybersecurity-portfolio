# Caso 01 — Brute Force SSH

## Resumen
Se documenta la detección de múltiples intentos fallidos de autenticación SSH sobre un servidor Linux, simulando un escenario de acceso inicial mediante fuerza bruta.

## Objetivo
Detectar patrones repetitivos de autenticación fallida y validar visibilidad operativa en Splunk a partir de logs de autenticación Linux.

## Escenario simulado
Desde una máquina atacante se generaron múltiples intentos fallidos de acceso SSH contra la máquina víctima, con el fin de evaluar la capacidad de detección en el SIEM.

## Fuente de datos
- `/var/log/auth.log`
- Sourcetype: `Ubuntu-Victima`
- Index: `main`

## Técnica observada
- Intentos repetidos de autenticación fallida
- Posible validación automatizada de credenciales
- Actividad consistente con acceso inicial

## Resultado
Se logró identificar:
- usuario objetivo
- dirección IP de origen
- repetición temporal del patrón
- volumen de intentos fallidos

## Impacto
Riesgo de acceso no autorizado mediante compromiso o descubrimiento de credenciales válidas.

## Clasificación
**True Positive**

## Recomendaciones
- Implementar controles contra fuerza bruta (ej. fail2ban)
- Restringir acceso SSH por IP o VPN
- Deshabilitar autenticación por contraseña cuando sea posible
- Monitorear volumen de fallos por usuario e IP
