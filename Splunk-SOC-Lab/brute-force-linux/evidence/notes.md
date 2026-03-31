# Notas de evidencia

## Actividad simulada

Se realizaron múltiples intentos fallidos de autenticación SSH para generar eventos de acceso no autorizado en logs Linux.

## Observaciones

- Los eventos fueron visibles en auth.log
- Splunk permitió detectar la repetición de intentos
- La actividad fue consistente con un patrón de brute force
