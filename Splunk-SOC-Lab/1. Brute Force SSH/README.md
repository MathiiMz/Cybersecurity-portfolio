# Detección en Splunk — Caso 01: Fuerza Bruta SSH

## Búsqueda base

``index=main sourcetype=Ubuntu-Victima sshd``

### Objetivo
Visualizar eventos generales asociados al servicio SSH en el host monitoreado.

``Detección de autenticaciones fallidas
index=main sourcetype=Ubuntu-Victima "Failed password"``

### Objetivo
Identificar intentos fallidos de autenticación SSH potencialmente asociados a acceso no autorizado.

## Conteo por usuario e IP

``index=main sourcetype=Ubuntu-Victima "Failed password"
| stats count by user, src
| sort - count``

### Objetivo
Determinar usuarios objetivo y direcciones IP de origen con mayor volumen de intentos fallidos.

## Conteo temporal

``index=main sourcetype=Ubuntu-Victima "Failed password"
| timechart count``

### Objetivo
Visualizar la frecuencia de intentos fallidos en el tiempo para identificar comportamiento repetitivo o anómalo.

### Hallazgos
- Se observaron múltiples intentos fallidos de autenticación sobre SSH.
- Fue posible identificar usuarios objetivo e IP de origen asociadas a los intentos.
- La actividad observada es consistente con comportamiento de fuerza bruta o validación de credenciales.

### Clasificación
Detección válida / intento de acceso no autorizado

### Valor analítico
Este caso permitió practicar:
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
- Los logs de autenticación representan una fuente crítica para detectar intentos de acceso no autorizado.
- La frecuencia y repetición de eventos permiten diferenciar errores operativos normales de actividad potencialmente maliciosa.
- Una detección simple, bien planteada y correctamente interpretada puede aportar alto valor operativo.

# Evidencia — Caso 01: Fuerza Bruta SSH

## Actividad simulada
Se realizaron múltiples intentos fallidos de autenticación SSH con el objetivo de generar eventos asociados a acceso no autorizado en logs Linux.

## Evidencia observada
- Los eventos fueron visibles en `auth.log`.
- Splunk permitió identificar la repetición de intentos fallidos.
- La actividad presentó un patrón consistente con fuerza bruta sobre servicio SSH.

## Evidencia recomendada en capturas
- Eventos crudos con `Failed password`
- Conteo por usuario e IP
- Vista temporal de la actividad
- Dashboard o panel asociado, si aplica

## Conclusión
La telemetría recolectada permitió detectar de forma efectiva actividad compatible con intentos de acceso inicial mediante validación repetitiva de credenciales.
