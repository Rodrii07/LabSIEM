# Laboratorio de Detección con SIEM

Laboratorio casero para construir y validar reglas de detección en un SIEM (Wazuh), usando eventos controlados para medir verdaderos y falsos positivos.

**Estado:** en progreso

## Objetivos
- Desplegar un SIEM Wazuh con endpoints Windows (Sysmon) y Linux
- Escribir reglas de detección mapeadas a MITRE ATT&CK
- Validar cada regla con eventos controlados, maliciosos y benignos
- Medir los falsos positivos y documentar el proceso de ajuste (tuning)

## Arquitectura
| VM | Rol | IP |
|---|---|---|
| wazuh-server | Manager, indexer y dashboard de Wazuh (Ubuntu Server 24.04, Wazuh 4.14) | 192.168.56.10 |
| win-endpoint-01 | Windows 11 + agente Wazuh + Sysmon | 192.168.56.20 |
| kali | Atacante (planificado) | 192.168.56.x |

Red: VirtualBox Host-only (laboratorio) + NAT (internet).

## Detecciones
| ID | Regla | MITRE | Estado | Precisión |
|---|---|---|---|---|
| 100100 | Fuerza bruta: 5+ inicios de sesión fallidos, misma cuenta, 120 s | T1110 | En pruebas | Por definir |

## Estructura del repositorio
- `setup/`: notas paso a paso de la construcción del laboratorio, con problemas y soluciones
- `rules/`: reglas de detección (XML de Wazuh; Sigma planificado)
- `tests/`: comandos usados para generar los eventos controlados
- `results/`: análisis de verdaderos/falsos positivos y ajustes
- `screenshots/`: evidencia

## Aprendizajes
(ver `setup/` y `results/`)
