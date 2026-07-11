# Blue Team Practices

Este repositorio centraliza el trabajo práctico realizado en el área de Blue Team, enfocado por el momento en la plataforma Let's Defend. Aquí se documentan las tareas de monitoreo, detección, análisis forense, respuesta a incidentes y gestión de alertas dentro de un entorno que simula un SOC (Security Operations Center) real.

El objetivo es registrar el proceso de aprendizaje, estructurar metodologías de investigación y construir una base de referencia técnica aplicable a la seguridad informática profesional.

## Plataforma Utilizada

* **Let's Defend:** Simulación de operaciones de SOC (L1/L2), análisis y triage de alertas, investigación de endpoints y contención de amenazas.

## Estructura de la Documentación

Cada ejercicio o alerta analizada en este repositorio está documentada bajo la siguiente estructura:

* **Descripción del Escenario:** Resumen del incidente original, nivel de criticidad y datos iniciales del host afectado (IP, hostname, usuario).
* **Metodología de Investigación:** Pasos cronológicos seguidos en el análisis (análisis de logs, monitoreo de procesos, conexiones de red).
* **Enriquecimiento de Amenazas (Threat Intelligence):** Análisis de reputación de artefactos (hashes, IPs, dominios) utilizando fuentes externas.
* **Acciones de Contención:** Medidas tomadas para mitigar el impacto, como el aislamiento de hosts o el bloqueo de indicadores de compromiso (IOCs).
* **Mapeo MITRE ATT&CK:** Identificación de las tácticas y técnicas utilizadas por el adversario.
* **Conclusión y Justificación:** Determinación final de la alerta (True Positive / False Positive) junto con la justificación del escalado.

## Áreas Temáticas Abordadas

* Análisis de logs y eventos de sistema (Windows Security Logs, Sysmon).
* Monitoreo de procesos y detección de técnicas de evasión de defensas.
* Análisis de red, peticiones DNS y tráfico HTTP/HTTPS hacia servidores C2.
* Aplicación de metodologías de contención inmediata en endpoints comprometidos.

## Reportes

- [EventID-153](/LetsDefend-Triaging/EventID-153.md)
- [EventID-263](/LetsDefend-Triaging/EventID-263.md)

