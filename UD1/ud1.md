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

Para cumplir con los estándares militares y aeroespaciales de GMV, se requiere un sistema operativo base Linux sometido a procesos de bastionado (Hardening), eliminando cualquier servicio no esencial para reducir la superficie de ataque. Sobre este núcleo seguro se desplegará una arquitectura de Docker que orquestará los servicios de la aplicación de monitorización, garantizando que cada proceso (base de datos, panel web, alertas) corra en un contenedor aislado y efímero.

La gestión de los datos de telemetría y logs de seguridad se realizará mediante un clúster de bases de datos PostgreSQL de alta disponibilidad. Todo el tráfico de red será inspeccionado por un Firewall de Nueva Generación y Proxy Inverso, y se implementarán mecanismos de Seguridad avanzados como autenticación de doble factor (2FA) para los administradores y copias de seguridad inmutables frente a ransomware.

**4. Oportunidades y viabilidad del proyecto**

La oportunidad estratégica radica en demostrar la capacidad de desplegar infraestructuras que cumplan con el Esquema Nacional de Seguridad (ENS), un requisito obligatorio para cualquier empresa que trabaje con la administración pública española. La viabilidad técnica es total gracias al uso de virtualización, permitiendo simular en un entorno de laboratorio la topología de red compleja de un centro de operaciones de defensa sin incurrir en costes millonarios de hardware.

Económicamente, el proyecto es altamente sostenible al utilizar un stack tecnológico Open Source (Linux, Docker, PostgreSQL, Grafana). Esto permite a GMV reducir costes operativos en licencias de software propietario para sus herramientas internas, desviando la inversión hacia la mejora de los protocolos de seguridad y la formación del personal.

**5. Obligaciones legales y normativas**

Dada la naturaleza de los clientes de GMV (Gobiernos, Fuerzas Armadas), el proyecto se rige estrictamente por el Esquema Nacional de Seguridad (ENS) en su categoría ALTA, lo que implica auditorías de trazabilidad y planes de continuidad de negocio. Asimismo, se debe cumplir con la normativa ISO 27001 sobre gestión de seguridad de la información, estándar en la industria aeroespacial.

En cuanto a la protección de datos personales de los operadores del sistema, se aplica rigurosamente el RGPD, asegurando que los registros de actividad (logs) se tratan con confidencialidad. Todo el software desarrollado internamente está sujeto a cláusulas de confidencialidad y propiedad industrial, protegiendo el know-how estratégico de la compañía frente a espionaje industrial.

**6. Guion inicial del proyecto**

La ejecución técnica se divide en cinco fases secuenciales. La Fase 1 y 2 (Infraestructura) abordarán la instalación del servidor físico simulado con Linux (Ubuntu Server) aplicando cifrado de disco (LUKS) y redundancia RAID 1, seguido del bastionado del sistema operativo según guías CCN-CERT. A continuación, se desplegará el motor Docker y se segmentarán las redes virtuales para aislar el tráfico de gestión del tráfico de datos.

La Fase 3 y 4 (Despliegue y Seguridad) se centrará en levantar los contenedores de la aplicación (Base de Datos PostgreSQL y Panel de Control) tras un Proxy Inverso Nginx con reglas estrictas de filtrado. Finalmente, la Fase 5 (Operaciones) implementará el sistema de copias de seguridad automatizadas (política 3-2-1) y la monitorización activa con alertas en tiempo real, concluyendo con una auditoría de seguridad para validar el cumplimiento del ENS antes del cierre del proyecto.
B. Anexo Técnico: Desglose detallado, Costes y Mantenimiento

Esto es lo que necesitas para trabajar y para rellenar los apartados económicos de tu proyecto (ideal para IPE II).
1. Guion Paso a Paso (Roadmap)

    Fase 0: Diseño de Arquitectura

        Diseñar topología de red: DMZ, LAN Interna, Red de Gestión.

        Definir especificaciones del hardware virtual (vCPU, RAM, Disco).

    Fase 1: El "Hierro" y el SO

        Crear Máquina Virtual (simulando servidor HP ProLiant).

        Configurar 2 Discos Virtuales de 100GB.

        Instalar Ubuntu Server 24.04 LTS.

        Configurar RAID 1 (Software) durante la instalación (Espejo).

        Hardening: Configurar SSH con llaves (sin password), instalar fail2ban, configurar UFW (Firewall) cerrando todo menos puerto 22.

    Fase 2: El Motor de Contenedores

        Instalar Docker Engine y Docker Compose plugin.

        Crear redes docker internas (docker network create gmv-internal).

        Crear estructura de carpetas para volúmenes persistentes.

    Fase 3: Los Servicios

        Redactar docker-compose.yml.

        Servicio DB: PostgreSQL (optimizada para datos geoespaciales/telemetría).

        Servicio App: Panel de monitorización (simulado con Grafana).

        Servicio Web: Nginx como Proxy Inverso con certificados SSL (simulados o Let's Encrypt).

    Fase 4: Seguridad y Resiliencia

        Script de Backup: Un script en Bash que haga pg_dump de la base de datos a las 3:00 AM, lo comprima y lo mueva a una carpeta segura.

        Simulacro de fallo: Apagar un disco del RAID y ver si el servidor arranca. Borrar el contenedor de la base de datos y recuperarlo con el volumen.

2. Análisis de Costes (Estimación para Proyecto Real)

Al ser un proyecto "On-Premise" (servidor propio en GMV), no pagamos alquiler mensual a Amazon/Google, pero hay una inversión inicial fuerte (CAPEX).

A. Costes de Implantación (CAPEX - Inversión Inicial)

Concepto,Descripción,Coste Estimado (Real),Coste en tu Proyecto
Hardware Servidor,"Servidor Dell PowerEdge / HP ProLiant (32GB RAM, Xeon, 2xSSD)",1.800 €,0 € (Virtualizado)
Infraestructura Red,Firewall físico (Fortinet/Cisco) + SAI (Batería),800 €,0 € (Simulado)
Licencias Software,"Linux, Docker, PostgreSQL, Grafana (Open Source)",0 €,0 €
Mano de Obra (Tú),60 horas de Técnico Superior ASIR (a 25€/hora coste empresa),1.500 €,0 € (Es tu estudio)
TOTAL INVERSIÓN,,4.100 €,0 €

B. Costes de Operación y Mantenimiento (OPEX - Mensual)

Concepto,Descripción,Coste Mensual
Consumo Eléctrico,Servidor 24/7 + Refrigeración (aprox. 50-80€ mes),60 €
Mantenimiento HW,"Amortización de piezas (discos duros que fallan, etc.)",20 €
Horas SysAdmin,4 horas/mes para actualizaciones de seguridad y revisión logs,100 €
TOTAL MENSUAL,,180 €

3. Justificación Económica (El "gancho" del proyecto)

    "La elección de tecnologías Open Source (Docker, Linux, PostgreSQL) permite a GMV ahorrar aproximadamente 15.000 € anuales en licencias (comparado con usar Windows Server + SQL Server + VMware). Además, al ser infraestructura propia, se evita el coste variable de la nube, que suele dispararse con el tráfico de datos masivo, garantizando un coste predecible y controlado."

## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

  ## Bibliografía / Webgrafía 
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)

