[Volver al índice general](../README.md)

# UD1 – Análisis del entorno y detección de necesidades tecnológicas

## Índice de apartados

- [ ] **1. Análisis del sector tecnológico**
- [ ] **2. Selección de la empresa o contexto de trabajo**
- [ ] **3. Identificación de necesidades tecnológicas**
- [ ] **4. Oportunidades y viabilidad del proyecto**
- [ ] **5. Obligaciones legales y normativas**
- [ ] **6. Guion inicial del proyecto**

**1. Análisis del sector tecnológico**

El ecosistema tecnológico de Sevilla, liderado por el PCT Cartuja, está virando agresivamente hacia la Inteligencia Artificial y el Big Data, siendo uno de los polos de atracción tecnológica más importantes del sur de Europa según la Corporación Tecnológica de Andalucía (CTA). Sin embargo, existe una carencia crítica de perfiles de infraestructura (SysAdmins/DevOps) especializados en soportar estas cargas de trabajo; las empresas encuentran desarrolladores de algoritmos, pero les cuesta encontrar técnicos capaces de desplegar los servidores de alto rendimiento necesarios para ejecutarlos de forma segura.

Informes del SEPE y la Cámara de Comercio de Sevilla destacan que la "Industria 4.0" y la digitalización avanzada son los mayores generadores de empleo estable en la región. Las empresas locales están repatriando sus servicios desde la nube pública a infraestructuras híbridas o privadas para proteger su propiedad intelectual y reducir costes de cómputo, generando una demanda inmediata de administradores de sistemas cualificados en virtualización y seguridad de datos.

**2. Selección de la empresa o contexto de trabajo**

El proyecto se contextualiza en la delegación de GMV en el PCT Cartuja (Sevilla), una multinacional tecnológica líder en sistemas de navegación por satélite, ciberseguridad y defensa. La necesidad detectada es la modernización de los sistemas internos de monitorización de incidencias críticas, que actualmente residen en servidores monolíticos (legacy) difíciles de escalar y mantener.

El objetivo es desplegar una nueva infraestructura On-Premise (Privada) basada en microservicios, aislada de internet y administrada por el departamento de sistemas. Esta plataforma permitirá a los operadores de GMV gestionar logs y alertas de seguridad en tiempo real, garantizando que la información sensible de sus clientes (gobiernos, agencias espaciales) permanezca bajo soberanía estricta y protegida mediante arquitectura de contenedores.

**3. Identificación de necesidades tecnológicas**

Para cumplir con los estándares de "Misión Crítica" de GMV, se requiere un sistema operativo Linux (ASO) endurecido (Hardened), donde se eliminarán servicios innecesarios para reducir la superficie de ataque. Sobre este núcleo se desplegará una arquitectura Docker (IAW) que orquestará los servicios de la aplicación, separando la lógica de negocio de los datos para facilitar actualizaciones sin paradas de servicio.

La gestión de datos recaerá sobre un clúster de bases de datos PostgreSQL o MariaDB (ASGBD) configurado para alta disponibilidad y tolerancia a fallos. Todo el tráfico de red será filtrado por un Firewall perimetral y un Proxy Inverso (SRI) con inspección de paquetes, y se implementarán protocolos de Seguridad (SAD) como copias de seguridad inmutables y autenticación de doble factor (2FA) para los administradores del sistema.

**4. Oportunidades y viabilidad del proyecto**

La oportunidad radica en simular un entorno "Enterprise" real, demostrando la capacidad de implementar el Esquema Nacional de Seguridad (ENS) en una infraestructura técnica, algo muy valorado por empresas contratistas del Estado como GMV. La viabilidad técnica es total, utilizando virtualización para recrear la topología de red de un centro de datos de defensa sin coste de hardware.

A nivel económico, el uso de herramientas Open Source (Linux, Docker, herramientas de monitorización como Prometheus/Grafana) garantiza la sostenibilidad del proyecto. Esto permite a GMV reducir la dependencia de licencias de software propietario en sus herramientas internas, alineándose con las estrategias de soberanía tecnológica europeas.

**5. Obligaciones legales y normativas**

Dada la naturaleza de GMV (Defensa/Espacio), el proyecto se rige por el Esquema Nacional de Seguridad (ENS), aplicando las medidas de nivel medio/alto en cuanto a control de accesos, trazabilidad y recuperación ante desastres. Además, se cumple estrictamente con el RGPD para la protección de los datos de los empleados que operan el sistema y la normativa ISO 27001 sobre seguridad de la información.

En cuanto a la propiedad intelectual, todo el software y scripts de automatización desarrollados en el proyecto se consideran activos confidenciales de la empresa. Se implementarán avisos legales internos y políticas de uso aceptable conforme a la LSSI-CE y los convenios de confidencialidad (NDA) habituales en el sector aeroespacial.

**6. Guion inicial del proyecto**



## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

  ## Bibliografía / Webgrafía 
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)

