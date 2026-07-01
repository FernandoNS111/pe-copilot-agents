# PE Copilot Agents — Cargadores GEN2 Power Electronics

Colección de agentes GitHub Copilot (`.agent.md`) especializados en el soporte técnico, diagnóstico y gestión de cargadores GEN2 de Power Electronics.

## Agentes disponibles

| Agente | Descripción |
|--------|-------------|
| **AgenteSCO-pro** | Experto en documentos SCO (Software Change Order), versiones de SW, parametrizaciones y configuraciones de cargadores GEN2. |
| **AnalizadorOCPP** | Análisis de logs OCPP 1.6-J desde syslogs: transacciones, estados de conectores, conexiones WebSocket y anomalías. |
| **APIpoweronsupport** | Consultas a la API de Power On Support: tickets, plantas, equipos, KPIs de disponibilidad, MTTR y partes de trabajo. |
| **AsistenciaCargadores** | Asistencia técnica interactiva para diagnóstico y troubleshooting de cargadores GEN2 vía SSH, con procedimientos paso a paso. |
| **CRON_monitoriza** | Gestión de monitorización automática (crontab) en la RPi: scripts de descarga de logs, horarios y carpetas. |
| **dispersionparametros** | Análisis de dispersión de parametrización entre cargadores GEN2, informes HTML con gráficos Plotly por tipo de placa. |
| **enforce-auth-analyzer** | Diagnóstico remoto del plugin pe-plugin-enforce-auth en cargadores NB Gen-II: discovery, decisiones de enforcement, errores y anomalías. |
| **Extraeparametrizaciones** | Extracción masiva de parametrización Modbus de cargadores GEN2, exportación a Excel separado por placas (AC, DC, CB). |
| **MassiveJSON** | Generación de archivos JSON de operaciones masivas para la herramienta Massive (`pe_charger`): chequeos, Modbus, HMI, modem, etc. |
| **ModbusWriter** | Lectura/escritura de registros Modbus TCP, parametrización desde Excel y escritura masiva de parámetros en cargadores. |
| **monitoriza_v1** | Revisión remota completa de cargadores GEN2: versiones SW, logs DC/AC, cargas, clasificación de fallos, bugs 7.0.0.4 BETA y análisis OCPP. |
| **party-orchestrator** | Orquestador multi-agente: configuración wizard, generación de agentes, coordinación de ejecución y consolidación de resultados. |
| **PUSH_PULL_agentes** | Sincronización de agentes Copilot entre PC local y GitHub: push, pull, comparación local/remoto, gestión de ramas y actualización del README. |
| **ReparaHMI** | Diagnóstico y reparación de HMI (pantalla Android): binding ADB/SSH, private_key, brightness, timeout y problemas de conexión. |
| **ResumenticketingPONS** | Resumen diario de tickets Power On Support: pendientes N1/N2, pendiente SAT y pendiente versión SW, agrupados por división. |
| **secureboot-agent** | Despliegue y verificación de Secure Boot en flotas de Raspberry Pi CM4: firmware firmado, SIGNED_BOOT y resolución de problemas. |

## Estructura del repositorio

```
.github/
  agents/
    AgenteSCO-pro.agent.md
    AnalizadorOCPP.agent.md
    APIpoweronsupport.agent.md
    AsistenciaCargadores.agent.md
    CRON_monitoriza.agent.md
    dispersionparametros.agent.md
    enforce-auth-analyzer.agent.md
    Extraeparametrizaciones.agent.md
    MassiveJSON.agent.md
    ModbusWriter.agent.md
    monitoriza_v1.agent.md
    party-orchestrator.agent.md
    PUSH_PULL_agentes.agent.md
    ReparaHMI.agent.md
    ResumenticketingPONS.agent.md
    secureboot-agent.agent.md
0 - API/
    API_PowerOnSupport_v2.py
    API_PowerOnSupport_REFERENCE.md
    resumen_tickets_diario.py
```

## Uso

Los agentes se invocan automáticamente desde VS Code con GitHub Copilot Chat. Escribe `@` seguido del nombre del agente o describe la tarea y Copilot seleccionará el agente adecuado.

Ejemplos:
- `@monitoriza_v1` — Revisión completa de un cargador por IP
- `@AnalizadorOCPP` — Analizar un syslog OCPP
- `@MassiveJSON` — Generar un JSON de operaciones masivas
- `@ModbusWriter` — Leer/escribir registros Modbus en cargadores
- `@Extraeparametrizaciones` — Extraer parametrización masiva a Excel
- `@ReparaHMI` — Diagnosticar y reparar HMI de un cargador
- `@enforce-auth-analyzer` — Analizar el plugin enforce-auth en un cargador
- `@secureboot-agent` — Desplegar Secure Boot en CM4
- `@PUSH_PULL_agentes` — Sincronizar agentes con el repo GitHub
- `@ResumenticketingPONS` — Resumen diario de tickets pendientes

## Requisitos

- **VS Code** con extensión GitHub Copilot
- Acceso SSH a cargadores GEN2 (clave `developer_rsa`)
- Python 3.10+ con dependencias del proyecto (para scripts auxiliares)
