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

Según el informe económico de la Cámara de Comercio de Sevilla, la provincia lidera el crecimiento andaluz con un incremento del PIB impulsado por el sector TIC y la industria aeroespacial, especialmente tras la designación de Sevilla como sede de la Agencia Espacial Española. El PCT Cartuja, donde se ubican empresas tractoras como GMV, facturó más de 4.000 millones de euros el último año, consolidándose como el principal ecosistema tecnológico del sur de España. Sin embargo, este crecimiento ha revelado una carencia crítica: la falta de infraestructuras seguras capaces de soportar operaciones de misión crítica (Defensa/Espacio) frente a ciberamenazas crecientes.

El Observatorio de las Ocupaciones del SEPE destaca en su informe anual que los perfiles con mayor dificultad de cobertura en Sevilla no son programadores web, sino especialistas en Ciberseguridad, Cloud Computing y Administración de Sistemas. El mercado laboral local está saturado de desarrolladores junior, pero existe una demanda urgente de técnicos superiores (ASIR) cualificados para implementar el Esquema Nacional de Seguridad (ENS) y gestionar entornos de alta disponibilidad. Este proyecto se alinea directamente con esta necesidad del mercado, simulando un despliegue de infraestructura segura que las empresas del parque tecnológico demandan activamente.

**2. Selección de la empresa o contexto de trabajo**

El proyecto se desarrolla en la delegación de GMV en el PCT Cartuja (Sevilla), multinacional tecnológica líder en los sectores de Espacio, Defensa y Seguridad. GMV es contratista de referencia para organismos como la Agencia Espacial Europea (ESA) y el Ministerio de Defensa, gestionando sistemas críticos que requieren niveles de confidencialidad y disponibilidad extremos.

La necesidad detectada que justifica este proyecto es la modernización de los sistemas internos de monitorización de satélites y ciberseguridad ("Ground Segment"). Actualmente, se requiere migrar servicios monolíticos antiguos a una nueva infraestructura On-Premise (Privada) basada en microservicios aislados. El objetivo es que el departamento de sistemas recupere el control total de los datos sensibles, garantizando la soberanía de la información sin depender de nubes públicas externas.

**3. Identificación de necesidades tecnológicas**

Para cumplir con los estándares militares y aeroespaciales de GMV, se requiere un sistema operativo base Linux (ASO) sometido a procesos de bastionado (Hardening), eliminando cualquier servicio no esencial para reducir la superficie de ataque. Sobre este núcleo seguro se desplegará una arquitectura de Docker (IAW) que orquestará los servicios de la aplicación de monitorización, garantizando que cada proceso (base de datos, panel web, alertas) corra en un contenedor aislado y efímero.

La gestión de los datos de telemetría y logs de seguridad se realizará mediante un clúster de bases de datos PostgreSQL (ASGBD) de alta disponibilidad. Todo el tráfico de red será inspeccionado por un Firewall de Nueva Generación y Proxy Inverso (SRI), y se implementarán mecanismos de Seguridad (SAD) avanzados como autenticación de doble factor (2FA) para los administradores y copias de seguridad inmutables frente a ransomware.

**4. Oportunidades y viabilidad del proyecto**

La oportunidad estratégica radica en demostrar la capacidad de desplegar infraestructuras que cumplan con el Esquema Nacional de Seguridad (ENS), un requisito obligatorio para cualquier empresa que trabaje con la administración pública española. La viabilidad técnica es total gracias al uso de virtualización, permitiendo simular en un entorno de laboratorio la topología de red compleja de un centro de operaciones de defensa sin incurrir en costes millonarios de hardware.

Económicamente, el proyecto es altamente sostenible al utilizar un stack tecnológico Open Source (Linux, Docker, PostgreSQL, Grafana). Esto permite a GMV reducir costes operativos en licencias de software propietario para sus herramientas internas, desviando la inversión hacia la mejora de los protocolos de seguridad y la formación del personal.

**5. Obligaciones legales y normativas**

Dada la naturaleza de los clientes de GMV (Gobiernos, Fuerzas Armadas), el proyecto se rige estrictamente por el Esquema Nacional de Seguridad (ENS) en su categoría ALTA, lo que implica auditorías de trazabilidad y planes de continuidad de negocio. Asimismo, se debe cumplir con la normativa ISO 27001 sobre gestión de seguridad de la información, estándar en la industria aeroespacial.

En cuanto a la protección de datos personales de los operadores del sistema, se aplica rigurosamente el RGPD, asegurando que los registros de actividad (logs) se tratan con confidencialidad. Todo el software desarrollado internamente está sujeto a cláusulas de confidencialidad y propiedad industrial, protegiendo el know-how estratégico de la compañía frente a espionaje industrial.

**6. Guion inicial del proyecto**



## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

  ## Bibliografía / Webgrafía 
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)

