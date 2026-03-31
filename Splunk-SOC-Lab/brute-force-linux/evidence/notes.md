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
