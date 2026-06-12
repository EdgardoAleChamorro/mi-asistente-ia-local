# Edgardo Ale AI V1.0 -Ecosistema Local y Soberano

¡Bienvenido! Este proyecto nació de la necesidad de tener un **Asistente de IA personal, potente y multifuncional**, pero con una condición innegociable: **privacidad absoluta**. 

En lugar de depender de servicios en la nube que comercializan o leen nuestros datos, diseñé e implementé un ecosistema completo de Inteligencia Artificial y almacenamiento privado que corre de forma **100% local y soberana**. Todo el procesamiento se realiza dentro de mi propia infraestructura, sin que un solo byte de información salga a internet.

---

## ¿Por qué este proyecto es diferente? 

Como profesionales de tecnología, a veces nos enfocamos solo en que el código funcione. Con **Edgardo Ale AI V1.0**, el objetivo fue ir más allá:
* **Privacidad por Diseño:** Mis documentos, notas y chats se procesan en mi propio hardware.
* **Modularidad:** Utilizo contenedores para que todo el sistema sea agnóstico; hoy corre en mi entorno virtualizado, pero mañana puede migrar a un servidor en producción o a un clúster doméstico sin cambiar una sola línea de configuración.
* **Aprender haciendo (RAG listo):** No es solo un chat idéntico a ChatGPT; está preparado para actuar como un "cerebro secundario" capaz de leer mis propios archivos locales y responder basándose en ellos.

---

##  Arquitectura del Sistema

La magia ocurre gracias a la combinación de cuatro herramientas líderes del mundo Open Source y DevOps:

1. **Ubuntu Desktop:** El sistema operativo base, elegido por su estabilidad y excelente manejo de recursos.
2. **Ollama:** El motor que le da vida a la IA, encargado de gestionar y ejecutar los modelos de lenguaje de forma ultraeficiente.
3. **Open WebUI:** Una interfaz de usuario hermosa, intuitiva y veloz (estilo ChatGPT) que personalicé con mi propia identidad de marca.
4. **Nextcloud + MariaDB:** Mi búnker de datos personal. El almacenamiento en la nube privada donde residen los documentos que alimentan el conocimiento del asistente.

---

##  El Cerebro: Qwen 2.5 

Para este despliegue elegí **Qwen 2.5 de 7 mil millones de parámetros**. Es un modelo de lenguaje de última generación optimizado para:
* Una comprensión y redacción impecable en español.
* Asistencia avanzada en escritura de código y debugging.
* Un consumo equilibrado de recursos, ideal para procesamiento por CPU en entornos virtuales.

---

##  Guía de Despliegue Rápido 

Si querés replicar este entorno en tu propia máquina virtual o servidor local, seguí estos pasos:

###  Requisitos Previos
* Tener instalado **Docker** y **Docker Compose V2**.
* Un mínimo de 8 GB de RAM asignados al sistema.

###  Instalación en 3 comandos

1. Cloná este repositorio en tu máquina local:
   ```bash
   git clone [https://github.com/EdgardoAleChamorro/mi-asistente-ia-local.git](https://github.com/EdgardoAleChamorro/mi-asistente-ia-local.git)
   cd mi-asistente-ia-local


**-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**



# Edgardo Ale IA - v1.1 (Local AI & DevOps Observability)

## Descripción del Proyecto
Este proyecto consiste en un entorno de laboratorio modular self-hosted sobre una máquina virtual Linux (Ubuntu). El ecosistema integra un asistente de inteligencia artificial privado junto con servicios de almacenamiento descentralizados, aplicando metodologías de cultura DevOps, infraestructura como código y observabilidad de sistemas.

---

## Actualizaciones en la Versión 1.1
La versión 1.1 expande la arquitectura inicial mediante la implementación de un stack de observabilidad completo utilizando Prometheus y Grafana. Esta actualización permite el scrap, centralización y visualización de la telemetría del hardware y del runtime de contenedores en tiempo real, transformando el laboratorio local en una infraestructura monitoreada bajo estándares profesionales.

---

## Arquitectura de la Infraestructura (Stack Docker Compose)

El entorno se encuentra completamente contenedorizado y orquestado mediante Docker Compose, dividiéndose en tres capas lógicas:

### 1. Capa de Aplicación e Inteligencia Artificial
* **Ollama:** Motor de ejecución local para modelos de lenguaje (LLMs) con optimización de recursos sobre hardware nativo.
* **Open-WebUI:** Interfaz web de usuario orientada a la interacción y parametrización de los modelos locales.
* **Nextcloud & MariaDB:** Suite de almacenamiento en la nube privada respaldada por un motor de base de datos relacional.

### 2. Capa de Recolección de Métricas (Aislamiento y Sistema Operativo)
* **Node Exporter:** Agente encargado de la recolección de métricas a nivel del sistema operativo huésped (uso de CPU, memoria RAM, operaciones de E/S de disco y tráfico de red).
* **cAdvisor (Container Advisor):** Utilidad de análisis a nivel de runtime de contenedores encargada de auditar el consumo de recursos, aislamiento y rendimiento de cada servicio de Docker de forma independiente.

### 3. Capa de Almacenamiento y Visualización
* **Prometheus:** Base de datos de series temporales (TSDB) configurada para centralizar y unificar las métricas recolectadas por los exportadores en intervalos de 10 segundos.
* **Grafana:** Plataforma de análisis y visualización conectada a Prometheus para el aprovisionamiento de dashboards dinámicos.

---

## Despliegue del Entorno

### Requisitos Previos
* Motor Docker y Docker Compose instalados en el sistema operativo huésped.
* Configuración previa del archivo `prometheus.yml` con los targets correspondientes a los agentes de recolección (`node-exporter` y `cadvisor`).

### Instrucciones de Ejecución
1. Clonar el repositorio localmente.
2. Navegar hacia el directorio raíz del proyecto.
3. Levantar el stack completo en segundo plano (detached mode) ejecutando:
```bash
   docker compose up -d


