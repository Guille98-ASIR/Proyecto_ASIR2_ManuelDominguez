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

El proyecto se centra en Nexo Neural, una consultora tecnológica sevillana especializada en soluciones de Inteligencia Artificial y formación avanzada. Actualmente, la empresa requiere escalar sus operaciones para ofrecer entornos de entrenamiento de modelos seguros a sus clientes corporativos, sin depender exclusivamente de proveedores externos que comprometan la confidencialidad de los datos sensibles.

El objetivo del proyecto es el diseño y despliegue de una infraestructura On-Premise (Servidor Local) optimizada para Inteligencia Artificial. Esta plataforma permitirá al equipo de Data Scientists de Nexo Neural desplegar, entrenar y monitorizar modelos de IA en un entorno controlado, aislado y gestionado íntegramente por el departamento de sistemas, garantizando la soberanía del dato y la eficiencia operativa.

**3. Identificación de necesidades tecnológicas**

La infraestructura requiere un sistema operativo base Linux (ASO), preferiblemente Ubuntu Server, optimizado para gestionar drivers de GPU y contenedores. Sobre esta base se desplegará una arquitectura de microservicios con Docker (IAW) que alojará herramientas de gestión de modelos (como MLflow o JupyterHub) y dashboards internos, permitiendo a los desarrolladores trabajar sin tocar la configuración del servidor.

Para el manejo de grandes volúmenes de datos, se implementará un sistema gestor de bases de datos PostgreSQL o Vectorial (ASGBD) en alta disponibilidad. Todo el entorno estará protegido por una red privada con acceso vía VPN y Proxy Inverso (SRI), y blindado con medidas de Seguridad (SAD) como cortafuegos perimetrales y copias de seguridad inmutables para proteger la propiedad intelectual de los algoritmos.

**4. Oportunidades y viabilidad del proyecto**

La oportunidad para Nexo Neural es estratégica: ofrecer a sus clientes "IA Soberana", garantizando que sus datos nunca salen de servidores controlados en España, un valor diferencial frente a la competencia que usa APIs públicas. La viabilidad técnica se sustenta en el uso de virtualización para simular los nodos de cómputo, permitiendo replicar una arquitectura de centro de datos real sin el coste prohibitivo del hardware de IA.

Económicamente, el proyecto maximiza la rentabilidad al utilizar un stack tecnológico 100% Open Source (Linux, Docker, PostgreSQL, Python), eliminando costes de licencias. Esto permite a la empresa ofrecer precios competitivos en sus servicios de consultoría y formación, manteniendo márgenes de beneficio altos al no depender de terceros.

**5. Obligaciones legales y normativas**

El proyecto debe cumplir rigurosamente con el RGPD y la futura Ley de IA de la UE (AI Act), asegurando la trazabilidad y seguridad de los datos utilizados para entrenar los modelos. Se implementarán registros de actividad (logs), cifrado de datos en reposo y tránsito, y controles de acceso estrictos para garantizar que solo personal autorizado de Nexo Neural acceda a la información sensible.

Asimismo, la plataforma cumplirá con la LSSI-CE en sus interfaces web internas y externas, y se alineará con los estándares de seguridad de la información (ISO 27001) recomendados por el INCIBE para empresas tecnológicas. Esto asegura que la infraestructura no solo sea funcional, sino legalmente robusta ante auditorías.



## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

  ## Bibliografía / Webgrafía 
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)

