# Análisis de IDS: Snort y Suricata

🛡 **Implementación y configuración de sistemas de detección de intrusos (IDS) con Snort y Suricata**  

Este repositorio contiene el informe del **Laboratorio de IDS**, donde se han desplegado y configurado **Snort 3** y **Suricata** para detectar actividades maliciosas en la red mediante reglas personalizadas.

## 🔍 Descripción

El objetivo de este laboratorio es aprender a configurar y optimizar **Snort y Suricata** como sistemas de detección de intrusos (IDS), creando reglas específicas para detectar ataques y analizar su funcionamiento en un entorno de red controlado.

Las principales tareas realizadas incluyen:
- **Configuración y ajuste de Snort 3**: Definición de reglas para detectar tráfico sospechoso.
- **Creación y validación de reglas personalizadas** en Snort y Suricata.
- **Comparación entre Snort y Suricata** en términos de sintaxis, rendimiento y manejo de logs.
- **Generación de alertas en tiempo real** ante distintos tipos de ataques.

## 📁 Contenido del Repositorio

- `IDS Ejercicio Enrique García Cuadrado.pdf` → Informe detallado con configuración, pruebas y análisis de detección.
- **Archivos de configuración y reglas personalizadas** (próximamente).

## 🛠 Herramientas Utilizadas

### 🔹 **Configuración y Reglas en Snort 3**
- **Edición del archivo `snort.lua`** para definir variables de red y cargar reglas personalizadas.
- **Descarga e integración de reglas de la comunidad** para ampliar la detección.
- **Creación de reglas locales en `local.rules`**, como:
  1. **Detección de escaneo de puertos** (`nmap -sS`).
  2. **Detección de tráfico ICMP (ping)**.
  3. **Detección de conexiones HTTP al puerto 80**.
  4. **Detección de contenido no permitido** en tráfico web (`porn` en la URI).
  5. **Detección de conexiones SSH al puerto 22**.

### 🔹 **Configuración y Reglas en Suricata**
- **Archivo `suricata.yaml`** estructurado en YAML para mayor organización.
- **Reglas personalizadas**, incluyendo:
  - **Detección de tráfico ICMP** (ping a la red).
  - **Detección de conexiones SSH** (`alert tcp any any -> $HOME_NET 22`).

### 🔹 **Comparación entre Snort y Suricata**
- **Sintaxis de reglas**: Suricata requiere variables como `$HOME_NET`, mientras que Snort es más flexible.
- **Manejo de logs**: Suricata genera logs en JSON, integrables con herramientas como **Elasticsearch**, mientras que Snort necesita herramientas externas para exportar datos estructurados.
- **Rendimiento**: Suricata está optimizado para múltiples núcleos, lo que lo hace más eficiente en redes con alto tráfico.

## 🚀 Resultados y Hallazgos

| Prueba Realizada  | Herramienta | Resultado |
|------------------|------------|-----------|
| **Escaneo de puertos (`nmap -sS`)** | Snort | Alerta de tráfico SYN sospechoso |
| **Ping ICMP (`ping 192.168.1.33`)** | Snort y Suricata | Detectado correctamente |
| **Conexión HTTP al puerto 80 (`nmap -p 80`)** | Snort | Alerta generada |
| **Petición web con palabra `porn` (`curl http://example.com?q=porn`)** | Snort | Detectado y registrado |
| **Intento de conexión SSH (`ssh usuario@192.168.1.33`)** | Snort y Suricata | Alerta de intento de acceso |
| **Comparación de rendimiento** | Snort vs. Suricata | Suricata mejor en procesamiento paralelo |

📊 **Conclusión:** Suricata ofrece un rendimiento superior en entornos de alto tráfico y mejor integración con herramientas modernas de análisis. Sin embargo, Snort sigue siendo una opción robusta con una comunidad activa y gran cantidad de reglas disponibles.

## 📌 Posibles Mejoras

- **Automatización del despliegue de IDS** con scripts en Bash o Ansible.
- **Integración con SIEM** para mejorar la correlación de eventos de seguridad.
- **Uso de Snort y Suricata en modo IPS** (Intrusion Prevention System) en lugar de solo detección.
- **Visualización de alertas en tiempo real** con **Kibana + Elasticsearch**.

## 🤝 Contribuciones

Si deseas mejorar este análisis, agregar más reglas o integrar nuevas herramientas, haz un **fork**, añade tus cambios y envía un **Pull Request**.

## 📜 Licencia

Este proyecto se distribuye bajo la licencia **MIT**. Consulta el archivo `LICENSE` para más detalles.
