# ARFICARS Platform

ARFICARS Platform es el monorepo inicial de la plataforma digital de ARFICARS.

El proyecto nace alrededor de un taller real y busca cubrir dos necesidades principales:

1. ayudar a gestionar la actividad interna del taller
2. ayudar a publicar y gestionar coches en venta de forma profesional

La idea no es crear solo una web de catálogo. La idea es construir una base digital del negocio: una plataforma con backoffice para el taller, una web pública para mostrar coches y, más adelante, una app móvil para que el equipo pueda operar también desde iOS y Android.

Este repositorio contiene la primera base técnica del proyecto:
- un backend principal con Spring Boot
- una aplicación pública con Nuxt
- una aplicación de administración con Nuxt
- infraestructura local para desarrollo
- documentación de arquitectura y decisiones técnicas

## Propósito

El objetivo de este repositorio es dejar una base limpia, entendible y ejecutable para ARFICARS.

Está pensado para cumplir dos cosas a la vez:
1. servir como base real para un producto de negocio
2. dejar una base técnica seria que pueda crecer sin rehacer todo desde cero

En esta etapa, la prioridad no es meter muchas funcionalidades, sino arrancar con orden, con una arquitectura clara y con una base que se pueda explicar y mantener.

## Qué quiere ser ARFICARS

ARFICARS quiere ser una plataforma que ayude al negocio en dos frentes.

### 1. Parte operativa del taller
El backoffice deberá permitir, de forma progresiva:
- gestionar clientes
- gestionar reservas o citas
- llevar seguimiento interno de la actividad del taller
- consultar balances o información de negocio
- centralizar operaciones internas del equipo

### 2. Parte comercial
La plataforma también deberá permitir:
- gestionar coches en venta
- crear y editar fichas de vehículos
- subir fotos y vídeos
- publicar o despublicar coches
- mostrar el catálogo en la web pública
- captar interesados o leads

Además, en una fase futura, habrá una app móvil en React Native para iOS y Android que usará la misma API y permitirá hacer tareas internas como sacar fotos, grabar vídeos o actualizar información desde el móvil.

## Base de arquitectura inicial

Estas decisiones de arquitectura ya están cerradas y este repositorio las refleja:

- **Frontend público:** Nuxt
- **Frontend admin:** Nuxt en una aplicación separada
- **Backend:** Spring Boot con Java
- **Estilo del backend:** monolito modular
- **Estructura interna del backend:** arquitectura hexagonal por módulos
- **Base de datos principal:** PostgreSQL
- **Identidad y autenticación:** Keycloak
- **Almacenamiento de ficheros binarios:** object storage compatible con S3
- **Infraestructura local:** Docker Compose
- **Ejecución en desarrollo:** backend y frontends desde IDE/editor; infraestructura en contenedores

Este repositorio evita meter complejidad antes de tiempo. Por tanto, en este bootstrap inicial quedan fuera:
- microservicios de negocio
- Redis
- Kafka o RabbitMQ
- motor de búsqueda dedicado
- Kubernetes
- observabilidad pesada
- autenticación de compradores
- e-commerce
- despliegues complejos más allá de un CI básico

## Estructura del repositorio

```text
.
├─ .github/
│  └─ workflows/
├─ backend/
│  └─ arfi-core-api/
├─ docs/
│  └─ adr/
├─ frontend/
│  ├─ apps/
│  │  ├─ arfi-public-web/
│  │  └─ arfi-admin-web/
│  └─ pnpm-workspace.yaml
├─ infra/
│  └─ compose/
├─ .editorconfig
├─ .env.example
├─ .gitattributes
├─ .gitignore
└─ README.md
````

## Componentes principales

### `backend/arfi-core-api`

Backend principal del sistema.

Aquí vivirá la API central de ARFICARS como aplicación Spring Boot, siguiendo un enfoque de monolito modular, con módulos claros y arquitectura hexagonal dentro de cada uno.

Esta API deberá servir tanto al backoffice web como a futuros clientes, incluida la app móvil administrativa.

### `frontend/apps/arfi-public-web`

Aplicación web pública.

Servirá el catálogo público, las fichas de vehículos, la presentación de la marca y los puntos de entrada para contacto o interés, con foco fuerte en SEO.

### `frontend/apps/arfi-admin-web`

Aplicación web de administración.

Servirá los flujos internos del negocio, incluyendo la gestión de vehículos, media, publicación y, más adelante, otras funciones del taller como clientes, reservas o seguimiento operativo.

### `infra/compose`

Base de infraestructura local.

Aquí irá la configuración de Docker Compose para levantar:

* PostgreSQL
* Keycloak
* object storage

La idea de esta carpeta es tener una infraestructura local repetible sin obligar a ejecutar también las aplicaciones dentro de contenedores durante el desarrollo normal.

### `docs`

Documentación de arquitectura e ingeniería.

Aquí se irá guardando:

* la base de arquitectura
* la estrategia del repositorio
* la guía de desarrollo local
* los ADR
* otros documentos técnicos del proyecto

## Modelo de desarrollo

El modelo inicial de desarrollo es simple:

* la infraestructura corre con Docker Compose
* el backend se ejecuta localmente desde IntelliJ
* los frontends se ejecutan localmente desde VS Code o terminal
* la documentación vive en el mismo repositorio
* el CI valida la base técnica de forma continua

Esto permite iterar rápido sin perder dependencias realistas.

## Estado actual

Este repositorio está en fase de **bootstrap**.

El objetivo de esta fase es dejar lista la base inicial del desarrollo, incluyendo:

* estructura del monorepo
* documentación base
* scaffolding del backend
* scaffolding de los frontends
* infraestructura local mínima
* pipeline básico de CI

Todavía no toca implementar la lógica completa del negocio. En esta fase importa más el orden, la claridad y la coherencia técnica que aparentar avance con complejidad vacía.

## Alcance inicial del bootstrap

Aunque la visión del producto es amplia, este primer hito tiene un alcance controlado.

El bootstrap inicial se centrará en dejar preparada la base técnica para:

* backend principal
* web pública
* web admin
* infraestructura local
* documentación
* CI básico

Las funciones completas de gestión del taller, reporting y app móvil quedan contempladas como evolución del sistema, pero no forman parte de este primer arranque técnico.

## Entregables previstos del bootstrap

El primer hito solo se considerará cerrado cuando existan, como mínimo, estos elementos:

* estructura base del repositorio
* `README.md`
* `docs/architecture.md`
* `docs/adr/ADR-001.md` a `ADR-005.md`
* `backend/arfi-core-api`
* `frontend/apps/arfi-public-web`
* `frontend/apps/arfi-admin-web`
* `infra/compose/compose.yaml`
* workflow básico de GitHub Actions
* evidencia de que la base construye y arranca correctamente

## Documentación

La documentación del repositorio irá definiendo poco a poco:

* la arquitectura base
* la estrategia del repositorio
* las normas de desarrollo local
* los registros de decisiones de arquitectura
* los límites de implementación de esta fase de bootstrap

## Principios de trabajo

Este repositorio sigue algunos principios que no se negocian:

* primero, utilidad real para el negocio
* modularidad antes que distribución
* límites claros entre partes del sistema
* nada de módulos compartidos convertidos en vertedero
* nada de complejidad “enterprise” por apariencia
* documentación que explique decisiones reales, no intenciones vacías

## Licencia

Licencia pendiente de definir.
