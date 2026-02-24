[Volver al índice general](../README.md)
# UD2 – Diseño técnico de la infraestructura empresarial segura y automatizada

## Índice de apartados

- [ ] **1. Recopilación de información técnica**
- [ ] **2. Diseño lógico y físico de la infraestructura**
- [ ] **3. Definición de objetivos y fases del proyecto**
- [ ] **4. Recursos y presupuesto**
- [ ] **5. Documentación técnica**

1 Recopilación de información técnica

Para el despliegue del proyecto de preservación de videojuegos y reparación de hardware, se han establecido los siguientes requisitos técnicos basados en la filosofía Open Source, consolidando los servicios en cuatro equipos físicos principales para optimizar los recursos, el consumo eléctrico y permitir una administración ágil (DevOps).

1.1 Inventario de Hardware (Equipos Físicos)

Servidor Perimetral (Firewall y Enrutador):

Hardware: Equipo dedicado con al menos 3 tarjetas de red (NICs).

Rol: Enrutador principal y barrera de seguridad. Conecta y aísla la WAN (Internet), la LAN, la DMZ y los túneles VPN.

Servidor Principal (Zona LAN):

Hardware: Equipo de alto rendimiento con CPU/GPU potente.

Rol: Servidor Híbrido (Emulación Nativa + Orquestación Kubernetes). Centraliza el núcleo del negocio.

Servidor Web (Zona DMZ):

Hardware: Equipo de bajo consumo (ej. MiniPC) o Máquina Virtual.

Rol: Servidor público. Alojamiento del portfolio web aislado del resto de la empresa.

Servidor de Almacenamiento (Zona LAN):

Hardware: Servidor NAS con discos duros en configuración RAID.

Rol: Repositorio central de copias de seguridad, ROMs y Volúmenes Persistentes (PVs) para Kubernetes.

1.2 Requisitos de Software y Stack Tecnológico

Todo el software utilizado es libre (Open Source), alineándose con estándares de la industria Cloud Native:

Sistema Operativo Base: Linux (distribuciones Enterprise/Debian) y FreeBSD.

Seguridad Perimetral y Acceso Remoto: pfSense integrado con WireGuard VPN para teletrabajo seguro.

Almacenamiento: TrueNAS con sistema de archivos ZFS.

Orquestación de Contenedores: K3s (Lightweight Kubernetes). Sustituye el uso de contenedores aislados por un clúster de alta disponibilidad que garantiza la autorrecuperación de los servicios (self-healing).

Gestión de Identidad: OpenLDAP y phpLDAPadmin (autenticación única para todos los servicios internos).

Base de Datos: MariaDB / Redis, desplegadas como StatefulSets en Kubernetes.

2 Diseño lógico y físico de la infraestructura

El diseño se basa en una arquitectura segmentada gestionada íntegramente por el firewall, garantizando la protección de los datos sensibles frente a posibles ataques desde Internet y facilitando el acceso a los técnicos autorizados.

2.1 Topología de Red y Segmentación

El Servidor Firewall (pfSense) cuenta con interfaces dedicadas y virtuales para gestionar el tráfico de las siguientes zonas:

Zona WAN (Internet): Recibe la conexión del ISP. El firewall aplica reglas NAT y de inspección de paquetes.

Zona LAN (Red Privada - 192.168.10.0/24): Zona de alta seguridad, sin acceso desde el exterior. El firewall actúa como Gateway, DHCP y DNS.

Zona DMZ (Red Perimetral - 192.168.50.0/24): Zona de seguridad media, accesible públicamente. Regla estricta: El tráfico de la DMZ tiene bloqueado por firewall cualquier intento de conexión hacia la LAN.

Zona VPN (Red Virtual - 10.0.0.0/24): Túnel cifrado mediante WireGuard. Permite al administrador acceder a la red interna desde el exterior como si estuviera físicamente en el taller.

2.2 Mapa de Servicios por Servidor (Diseño Físico)

A. En la Red LAN (Segura):

Servidor Principal: Ejecuta cargas de trabajo híbridas para maximizar el rendimiento y la fiabilidad:

Capa Bare Metal (Nativa): Ejecuta RomM (Rom Manager) directamente sobre el SO para aprovechar el 100% de la aceleración de hardware (GPU) en la emulación de juegos.

Capa Orquestación (Clúster K3s): Ejecuta la infraestructura de gestión corporativa mediante Deployments y Services:

Gestión Taller (GLPI / Leantime): Sistema de tickets y facturación.

OpenLDAP: Directorio central de usuarios.

Base de Datos (MariaDB): Almacena los registros de GLPI y LDAP, utilizando Persistent Volume Claims (PVC) conectados al NAS.

Ingress Controller (Traefik): Enruta el tráfico interno hacia los contenedores correctos.

Servidor TrueNAS: Proporciona almacenamiento de red. Sirve volúmenes NFS para Kubernetes y RomM, y volúmenes SMB seguros para guardar volcados de NAND/BIOS de clientes.

Equipos Cliente: PC del Trabajador (acceso total de administración) y PC de Pruebas (testeo de consolas reparadas vía RomM).

B. En la Red DMZ (Pública):

Servidor Web: Ejecuta contenedores de forma aislada (Podman/Docker). Contiene un servidor Nginx que despliega el portfolio de trabajos de modding y servicios.

3 Definición de objetivos y fases del proyecto

3.1 Objetivos del Proyecto (SMART)

Preservación y Rendimiento: Lograr una emulación sin latencia instalando RomM en formato Bare Metal.

Alta Disponibilidad (DevOps): Implementar Kubernetes (K3s) para la gestión empresarial. Si el contenedor de GLPI o la Base de Datos falla, el orquestador detectará el error y levantará un nuevo Pod automáticamente en segundos.

Teletrabajo y Seguridad: Desplegar una VPN corporativa con WireGuard para administrar remotamente el clúster y el firewall.

Aislamiento Comercial: Mantener la web pública en una DMZ estrictamente separada de los datos de los clientes.

3.2 Fases de Implementación (Cronograma)

Fase 1: Enrutamiento y VPN: Instalación de pfSense, configuración de interfaces (LAN, DMZ) y despliegue del túnel WireGuard.

Fase 2: Almacenamiento Central: Despliegue de TrueNAS y exportación de volúmenes persistentes.

Fase 3: Orquestación K3s: Instalación del plano de control de Kubernetes en el Servidor Principal.

Fase 4: Servicios Core y Web: Despliegue vía manifiestos YAML de MariaDB, OpenLDAP, GLPI en K3s; y despliegue del Nginx en la DMZ.

Fase 5: Emulación Bare Metal: Instalación nativa de RomM en el Servidor Principal y pruebas de estrés.

4 Recursos y presupuesto

Al priorizar soluciones Cloud Native de código abierto, se elimina por completo el coste de licenciamiento empresarial tradicional.

4.1 Presupuesto Estimado (Simulación de Ahorro)

Componente Lógico

Solución Elegida

Coste

Solución Propietaria

Ahorro

Firewall y VPN

pfSense + WireGuard

0 €

Fortinet + AnyConnect

> 800 € / año

Orquestación

Kubernetes (K3s)

0 €

VMware Tanzu / OpenShift

> 1.500 €

Sistema de Identidad

OpenLDAP

0 €

Win Server + AD CALS

> 800 €

Gestión Taller (ERP)

GLPI / Leantime

0 €

ServiceNow / Jira

Suscripción

Base de Datos

MariaDB

0 €

MS SQL Server

> 1.000 €

TOTAL SOFTWARE



0 €



> 4.100 €

5 Documentación técnica

Para asegurar el mantenimiento futuro y la escalabilidad de la infraestructura, se generarán los siguientes documentos técnicos (Anexos):

Esquema de Red y VPN: Configuración de reglas NAT en pfSense y generación de pares de claves para clientes WireGuard.

Manifiestos de Kubernetes: Repositorio con los archivos .yaml (Deployments, Services, Ingress, PVCs) para recrear toda la infraestructura de gestión en minutos.

Guía de Integración LDAP: Parámetros de conexión para enlazar GLPI y RomM contra el directorio activo OpenLDAP.

Manual de Operador de Taller: Procedimiento estándar para la creación de tickets y volcados de seguridad en el NAS.

## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

## Bibliografía / Webgrafía
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)
