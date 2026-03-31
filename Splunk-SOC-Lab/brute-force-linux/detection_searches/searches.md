# Detección en Splunk - Caso 01: Fuerza Bruta

## Búsqueda base

``index=main sourcetype=Ubuntu-Victima sshd``

### Objetivo
- Visualizar eventos generales asociados al servicio SSH en el host monitoreado.

## Detección de autenticaciones fallidas

``index=main sourcetype=Ubuntu-Victima "Failed password"``

### Objetivo
- Identificar intentos fallidos de autenticación SSH potencialmente asociados a acceso no autorizado.

## Conteo por usuario e IP

``index=main sourcetype=Ubuntu-Victima "Failed password"
| stats count by user, src
| sort - count``

### Objetivo
- Determinar usuarios objetivo y direcciones IP de origen con mayor volumen de intentos fallidos.

## Conteo temporal

``index=main sourcetype=Ubuntu-Victima "Failed password"
| timechart count``

### Objetivo
- Visualizar la frecuencia de intentos fallidos en el tiempo para identificar comportamiento repetitivo o anómalo.

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
