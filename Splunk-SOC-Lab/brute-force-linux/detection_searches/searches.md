# Detección en Splunk - Caso 01: Fuerza Bruta

## Búsqueda base

``index=main sourcetype=Ubuntu-Victima sshd``

## Detección de autenticaciones fallidas

``index=main sourcetype=Ubuntu-Victima "Failed password"``

## Conteo por usuario e IP

``index=main sourcetype=Ubuntu-Victima "Failed password"
| stats count by user, src
| sort - count``

## Conteo temporal

``index=main sourcetype=Ubuntu-Victima "Failed password"
| timechart count``

### Hallazgos
- Se observaron múltiples intentos fallidos de autenticación sobre SSH.
- Fue posible identificar usuarios objetivo e IP de origen asociadas a los intentos.
- La actividad observada es consistente con comportamiento de fuerza bruta o validación de credenciales.

### Clasificación
- Detección válida / intento de acceso no autorizado

### Valor analítico
- Este caso permitió practicar:
  - monitoreo de autenticación
  - detección de acceso inicial
  - identificación de patrones repetitivos
  - análisis de eventos de seguridad en Linux
  - priorización de eventos en un escenario SOC

### Limitaciones
- Laboratorio controlado
- Sin integración con listas de reputación
- Sin correlación con firewall o IDS

### Lecciones aprendidas
- Los logs de autenticación son una fuente crítica para detectar intentos de acceso no autorizado.
- La frecuencia y repetición de eventos son claves para diferenciar error humano de actividad sospechosa.
- Una detección simple bien planteada puede entregar alto valor operativo.
