# Capítulo IV: Product Implementation & Validation

## 4.1. Software Configuration Management

En esta sección el equipo establece las decisiones y convenciones que permiten mantener la consistencia de los productos de Qlic durante su ciclo de vida: el Landing Page, el RESTful API y las aplicaciones móviles nativa y multiplataforma. La gestión de configuración del software (Software Configuration Management, SCM) identifica los elementos que se versionan, controla sus cambios y registra su estado para que todo integrante pueda reproducir cualquier versión publicada (Institute of Electrical and Electronics Engineers [IEEE], 2012; Sommerville, 2016). Las decisiones se agrupan en cuatro frentes: el entorno de desarrollo, la gestión del código fuente, las guías de estilo y la configuración del despliegue.

### 4.1.1. Software Development Environment Configuration

El equipo definió un conjunto común de herramientas para cada actividad del proyecto, de modo que los artefactos producidos por un integrante puedan ser abiertos, revisados y modificados por cualquier otro sin conversiones adicionales. La selección respeta las restricciones tecnológicas establecidas para el proyecto: UXPressia para los artefactos de needfinding, Figma para wireframes, mock-ups y prototipos, LucidChart para wireflows y user flows, Structurizr y PlantUML como *diagram-as-code*, Spring Boot para los Web Services documentados con OpenAPI vía Swagger, Kotlin para la aplicación Android nativa, Flutter con Dart para la aplicación multiplataforma, y Trello y GitHub para la gestión del proyecto y del código fuente.

**Project Management**

| Herramienta | Propósito | Ruta de acceso |
|---|---|---|
| Trello | Tablero del Product Backlog y del Sprint Backlog, con estados por historia y responsables asignados. | https://trello.com |
| WhatsApp | Comunicación diaria del equipo y coordinación de revisiones. | https://web.whatsapp.com |
| GitHub | Alojamiento de repositorios, revisión de cambios e Insights de colaboración. | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov |

**Requirements Management y Product UX/UI Design**

| Herramienta | Propósito | Ruta de acceso |
|---|---|---|
| UXPressia | Elaboración de User Personas, Journey Maps e Impact Map. | https://uxpressia.com |
| Miro | Sesiones colaborativas de EventStorming y Context Mapping. | https://miro.com |
| Figma | Wireframes, mock-ups y prototipos de la aplicación móvil y del Landing Page, sobre la base de Material Design 3. | https://www.figma.com |
| LucidChart | Wireflow diagrams y user flow diagrams de la aplicación móvil. | https://www.lucidchart.com |

**Software Construction**

| Producto | Tecnología | Herramienta de desarrollo | Ruta de acceso |
|---|---|---|---|
| Landing Page | HTML5, CSS3 y JavaScript | Visual Studio Code | https://code.visualstudio.com |
| RESTful API | Kotlin 2.3 sobre Spring Boot 4.1 (Web MVC, Data JPA, Validation y Security OAuth2 Resource Server), con JVM 24 y Gradle Wrapper 9.7 (Kotlin DSL) | IntelliJ IDEA | https://www.jetbrains.com/idea |
| Mobile App (nativa) | Kotlin sobre Android | Android Studio | https://developer.android.com/studio |
| Mobile App (multiplataforma) | Flutter con Dart | Visual Studio Code o Android Studio con el plugin de Flutter | https://docs.flutter.dev/get-started |
| Base de datos | H2 en memoria para desarrollo local y PostgreSQL para producción | Consola H2 y cliente del proveedor de nube | https://www.postgresql.org |
| Modelado | PlantUML para diagramas UML y Structurizr DSL para C4 Model | Editor de texto y Structurizr | https://plantuml.com · https://structurizr.com |

El RESTful API se construye con el Gradle Wrapper incluido en el repositorio (`./gradlew bootRun`), por lo que cada integrante utiliza la misma versión de Gradle sin instalarla de forma manual. La versión de la JVM se fija mediante el toolchain de Gradle, lo que evita diferencias de compilación entre equipos (Gradle, s. f.).

**Software Testing**

| Herramienta | Propósito |
|---|---|
| JUnit 5 y kotlin-test | Pruebas unitarias de las reglas de dominio y de los manejadores de comandos del RESTful API. |
| Spring Test (MockMvc) y Spring Security Test | Pruebas de integración de los endpoints con el contexto completo de Spring, la base de datos en memoria y la seguridad por token. |
| Gherkin | Especificación de los criterios de aceptación de las User Stories en formato Dado/Cuando/Entonces, base de las pruebas de aceptación (Cucumber, s. f.). |
| Swagger UI | Ejecución manual de los endpoints documentados y verificación de los códigos de respuesta. |

**Software Deployment y Software Documentation**

| Herramienta | Propósito | Ruta de acceso |
|---|---|---|
| Docker | Empaquetado reproducible del RESTful API en una imagen de contenedor. | https://docs.docker.com |
| Render | Plataforma en la nube que ejecuta el contenedor del RESTful API y provee la base de datos PostgreSQL. | https://render.com |
| GitHub Pages | Publicación del Landing Page como sitio estático. | https://pages.github.com |
| Firebase App Distribution | Distribución de las aplicaciones móviles a usuarios de prueba durante la etapa de validación. | https://firebase.google.com/products/app-distribution |
| springdoc-openapi y Swagger UI | Generación de la especificación OpenAPI 3 del RESTful API y de su documentación interactiva. | https://springdoc.org |
| Markdown en GitHub | Redacción y versionado del Project Report. | https://docs.github.com |

### 4.1.2. Source Code Management

El código fuente de cada producto se gestiona en un repositorio independiente dentro de la organización de GitHub del equipo, con Git como sistema de control de versiones. Separar los repositorios por producto permite versionar y desplegar cada uno de forma autónoma, en coherencia con los containers definidos en la sección 2.5.3.2. El repositorio de los Web Services incluye, junto con el proyecto, las pruebas unitarias y de integración en `src/test/kotlin`.

**Organización de GitHub:** https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov

| Producto | Repositorio | Rama principal |
|---|---|---|
| Project Report | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/upc-pre-202620-1acc0238-13984-Qlic-report | `master` |
| RESTful API | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/qlic-backend-api | `main` |
| Landing Page | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/qlic-landing-page | `main` |
| Frontend Web | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/qlic-frontend-web | `main` |

**Modelo de ramas: GitFlow**

El equipo adopta el modelo GitFlow propuesto por Driessen (2010), que separa el código listo para producción del código en integración mediante dos ramas permanentes y tres tipos de ramas de soporte:

| Rama | Origen | Destino | Uso en Qlic |
|---|---|---|---|
| `master` / `main` | — | — | Contiene únicamente versiones publicadas; cada merge corresponde a un release etiquetado. El Project Report utiliza `master` y los repositorios de código, `main`. |
| `develop` | `master` / `main` | `release/*` | Integra las funcionalidades terminadas del Sprint en curso. |
| `feature/*` | `develop` | `develop` | Una rama por historia o grupo de historias, con nombre en *kebab-case* (por ejemplo, `feature/iam-authentication`, `feature/support-incidents` o `feature/chapter-4`). |
| `release/*` | `develop` | `master` / `main` y `develop` | Prepara una entrega: se ajustan versión, documentación y correcciones menores (por ejemplo, `release/v1.1.0`). |
| `hotfix/*` | `master` / `main` | `master` / `main` y `develop` | Corrige un error detectado en una versión publicada (por ejemplo, `hotfix/v1.1.1`). |

Los merges hacia `develop`, `release/*` y `master` / `main` se realizan con la opción `--no-ff`, de modo que cada integración conserva un commit de merge propio y el historial refleja qué cambios formaron parte de cada funcionalidad (Driessen, 2010).

**Versionado semántico**

Los releases se etiquetan siguiendo Semantic Versioning 2.0.0 con el formato `vMAJOR.MINOR.PATCH` (Preston-Werner, s. f.). Se incrementa MAJOR ante cambios incompatibles en el contrato del RESTful API, MINOR al incorporar funcionalidades compatibles —como los endpoints de un nuevo Sprint— y PATCH ante correcciones. En el Project Report, el número de versión de cada entrega se registra además en la sección Registro de Versiones del Informe.

**Mensajes de commit: Conventional Commits**

Los mensajes de commit siguen la especificación Conventional Commits 1.0.0, con la estructura `<tipo>(<alcance opcional>): <descripción>` (Conventional Commits, s. f.). Los tipos utilizados por el equipo son:

| Tipo | Uso | Ejemplo |
|---|---|---|
| `feat` | Nueva funcionalidad | `feat(iam): expose sign-up and sign-in endpoints (US05, US06)` |
| `fix` | Corrección de un error | `fix(alerting): return 404 when alert does not exist` |
| `docs` | Cambios en documentación o en el Project Report | `docs(chapter-4): add software configuration management` |
| `test` | Pruebas nuevas o corregidas | `test(iam): add unit tests for registration and authentication` |
| `refactor` | Cambio interno sin alterar el comportamiento | `refactor(monitoring): extract device resource assembler` |
| `chore` | Configuración, dependencias o tareas de mantenimiento | `chore(deploy): add Render Blueprint with managed PostgreSQL` |

La descripción se redacta en inglés, en modo imperativo y sin punto final, de modo que el historial pueda leerse como una secuencia de acciones sobre el producto.

### 4.1.3. Source Code Style Guide & Conventions

El equipo adopta guías de estilo publicadas por los responsables de cada lenguaje o plataforma, en lugar de definir reglas propias, para que el código resulte familiar a cualquier desarrollador que se incorpore al proyecto. Como regla general, todo identificador —clases, funciones, variables, endpoints y tablas— se escribe en inglés, mientras que la documentación dirigida al usuario y el Project Report se redactan en español.

**Kotlin (RESTful API y Mobile App nativa)**

Se aplican las Kotlin Coding Conventions (JetBrains, s. f.), la Android Kotlin Style Guide (Google, s. f.-c) en la aplicación Android y las convenciones de estructura de Spring Boot Features (Spring, s. f.-c) en el RESTful API:

- Clases, interfaces y objetos en *UpperCamelCase* (`AuthenticationController`); funciones y propiedades en *lowerCamelCase* (`handleRegister`); constantes en *SCREAMING_SNAKE_CASE* (`BEARER_SCHEME`).
- Paquetes en minúsculas y sin guiones bajos, bajo el paquete raíz `com.wasd.qlic`, con la clase principal `QlicBackendApiApplication` en ese paquete raíz, como recomienda Spring Boot.
- Sangría de cuatro espacios y longitud de línea no mayor a 120 caracteres.
- Uso de `val` por defecto y de `var` solo cuando el estado del objeto debe cambiar; inyección de dependencias por constructor.
- Uso de `data class` para comandos, consultas y recursos de entrada y salida.
- Configuración externa en `application.properties` y perfiles de Spring (`dev`, `prod`), sin valores sensibles en el código.
- En la aplicación Android, los textos visibles para el usuario se ubican en `res/values/strings.xml` (inglés, por defecto) y `res/values-b+es+419/strings.xml` (español latinoamericano).

**Organización del RESTful API**

El código se organiza por bounded context y, dentro de cada uno, por las cuatro capas definidas en la sección 2.6 (`domain`, `application`, `interfaces`, `infrastructure`), respetando los sufijos `Command`, `CommandHandler`, `Query`, `Controller`, `Resource`, `RepositoryImpl` y `Adapter`. Adicionalmente:

- Los endpoints se versionan y nombran con sustantivos en plural y en *kebab-case* bajo el prefijo `/api/v1` (por ejemplo, `/api/v1/devices/{id}/water-point`).
- Los verbos HTTP y los códigos de estado se utilizan según su semántica estándar (Fielding et al., 2022): `201 Created` al crear un recurso, `400 Bad Request` ante datos inválidos, `401 Unauthorized` ante credenciales ausentes o inválidas, `403 Forbidden` cuando el usuario autenticado no cuenta con el permiso requerido, `404 Not Found` cuando el recurso no existe o no pertenece a la cuenta, y `409 Conflict` ante un recurso duplicado o un cambio de estado no permitido.
- Los errores se devuelven con el formato *Problem Details for HTTP APIs* (`application/problem+json`), definido en el RFC 9457 (Nottingham et al., 2023).
- Las tablas y columnas de la base de datos se nombran en *snake_case* y en plural (`subscribers`, `password_hash`).
- La cuenta y el permiso del solicitante se obtienen del token de acceso y no de un parámetro enviado por el cliente; los endpoints de IAM, Consumption Analytics y Support incorporados en el Sprint 2 siguen esta regla, de modo que un usuario solo opera sobre la cuenta de su sesión.
- La integración entre bounded contexts se realiza mediante interfaces del dominio (por ejemplo, `PlanEntitlementProvider` o `AlertDataProvider`) implementadas por adaptadores de la capa de infraestructura (*anti-corruption layer*), sin que un contexto acceda a las clases de dominio de otro desde sus capas de dominio o aplicación.
- Los mensajes del API se escriben en inglés por defecto y se traducen al español latinoamericano en archivos de recursos (`messages.properties` y `messages_es_419.properties`), seleccionados según el encabezado `Accept-Language`.

**Dart (Mobile App multiplataforma)**

Se aplica la guía Effective Dart: Style (Dart, s. f.): tipos en *UpperCamelCase*, archivos y paquetes en *lowercase_with_underscores*, y variables y funciones en *lowerCamelCase*. El formato del código se normaliza con la herramienta `dart format` antes de cada commit.

**HTML, CSS y JavaScript (Landing Page)**

Se aplican la Google HTML/CSS Style Guide (Google, s. f.-b) y la HTML Style Guide and Coding Conventions de W3Schools (W3Schools, s. f.): etiquetas y atributos en minúsculas, sangría de dos espacios, uso de elementos semánticos (`header`, `nav`, `main`, `section`, `footer`) y clases CSS en *kebab-case*. Los elementos interactivos incorporan atributos ARIA, conforme a la Technical Story TS08.

**Gherkin (especificación de comportamiento)**

Los archivos `.feature` de las pruebas de aceptación se escriben en inglés con las palabras clave *Feature*, *Scenario*, *Given*, *When* y *Then* (Cucumber, s. f.), siguiendo las Gherkin Conventions for Readable Specifications (SpecFlow, s. f.): un único comportamiento por escenario, pasos redactados desde la perspectiva del usuario y en tiempo presente, y nombres de escenario que describen el resultado esperado. En el informe, los criterios de aceptación de las User Stories conservan su redacción en español (*Dado*, *Cuando*, *Entonces*). Las pruebas del RESTful API incluyen el identificador de la historia y del escenario en su `@DisplayName` (por ejemplo, `US05 - Scenario 2: an already registered email does not create a new account`), lo que permite trazar cada prueba con su criterio de aceptación.

### 4.1.4. Software Deployment Configuration

La configuración de despliegue define cómo cada producto pasa del repositorio a un entorno accesible por los usuarios. El equipo separa la configuración del código siguiendo el principio de *Config* de The Twelve-Factor App: los valores que cambian entre entornos —credenciales de base de datos, claves de firma o puertos— se leen de variables de entorno y no se versionan en el repositorio (Wiggins, s. f.).

La Figura 4.1 presenta el Deployment Diagram de C4 Model elaborado en la sección 2.5.3.3, que sirve de referencia para la configuración descrita a continuación: el Landing Page se publica en un proveedor de hosting estático, el RESTful API y la base de datos PostgreSQL se ejecutan en el proveedor de nube, y las aplicaciones móviles se instalan en los dispositivos de los suscriptores.

<img src="../images/c4/03_deployment_diagram.png" alt="Deployment Diagram de C4 Model de Qlic" width="800">

*Figura 4.1.* Deployment Diagram de C4 Model de la solución Qlic.

**Landing Page — GitHub Pages**

1. En el repositorio del Landing Page, la rama `main` contiene la versión publicada del sitio con el archivo `index.html` en la raíz.
2. En *Settings › Pages* se selecciona como fuente *Deploy from a branch*, con la rama `main` y la carpeta raíz (`/`).
3. GitHub publica el sitio en `https://1acc0238-2620-13984-aplicaciones-mov.github.io/qlic-landing-page/` y lo actualiza automáticamente con cada merge a `main` (GitHub, s. f.-a).

**RESTful API — Docker y Render**

El RESTful API se empaqueta como una imagen de Docker mediante un `Dockerfile` de dos etapas: la primera compila el proyecto con el Gradle Wrapper sobre una imagen JDK 24 (Alpine) y genera el ejecutable con `bootJar`; la segunda copia únicamente ese archivo sobre una imagen JRE 24 (Alpine) y lo inicia con el puerto asignado por la plataforma, lo que reduce el tamaño de la imagen final (Docker, s. f.).

La aplicación define dos perfiles de Spring Boot (Spring, s. f.-b):

| Perfil | Archivo | Base de datos | Uso |
|---|---|---|---|
| `dev` (por defecto) | `application-dev.properties` | H2 en memoria, con consola en `/h2-console` | Desarrollo y pruebas locales |
| `prod` | `application-prod.properties` | PostgreSQL administrado por el proveedor de nube | Entorno desplegado |

Desde el Sprint 2, la infraestructura del RESTful API en Render se declara como código en el archivo `render.yaml` (*Blueprint*) de la raíz del repositorio, que define el *Web Service* Docker y la base de datos PostgreSQL administrada y los enlaza mediante variables de entorno, sin versionar credenciales (Render, s. f.-a). Pasos de despliegue:

1. En Render, seleccionar *New › Blueprint* y elegir el repositorio `qlic-backend-api`; Render lee el `render.yaml` y muestra los recursos que creará: la base de datos `qlic-postgres` y el servicio `qlic-backend-api`.
2. Confirmar la creación. Render aprovisiona PostgreSQL e inyecta en el servicio su *host*, puerto, nombre de base, usuario y contraseña (`fromDatabase`), y genera un valor aleatorio para `JWT_SECRET` (`generateValue`).
3. Render construye la imagen a partir del `Dockerfile`, la ejecuta con el perfil `prod` y expone el servicio en `https://qlic-backend-api.onrender.com`; cada merge a `main` dispara un nuevo despliegue automático. El `Dockerfile` inicia la aplicación con el puerto de la variable `PORT` asignada por la plataforma (`-Dserver.port=${PORT:-8080}`).
4. Al iniciar contra una base vacía, Hibernate crea las tablas (`ddl-auto=update`) y el *seeder* de Support registra los técnicos y la versión vigente de los términos y condiciones.
5. Verificar el despliegue en `https://qlic-backend-api.onrender.com/swagger-ui.html`; Render utiliza `/v3/api-docs` como *health check* del servicio.

**Configuración del entorno `prod`**

| Variable | Origen | Valor |
|---|---|---|
| `SPRING_PROFILES_ACTIVE` | `render.yaml` | `prod` |
| `DB_HOST`, `DB_PORT`, `DB_NAME` | Base de datos de Render (`fromDatabase`) | Datos de conexión de PostgreSQL; el perfil `prod` construye con ellos la URL `jdbc:postgresql://<host>:<puerto>/<base>` |
| `SPRING_DATASOURCE_USERNAME` | Base de datos de Render | Usuario de la base de datos |
| `SPRING_DATASOURCE_PASSWORD` | Base de datos de Render | Contraseña de la base de datos |
| `SPRING_DATASOURCE_URL` | Opcional | Reemplaza la URL construida, por ejemplo, para usar una base externa |
| `JWT_SECRET` | Generado por Render | Clave de firma HS256 de al menos 32 caracteres |
| `JWT_EXPIRATION_MINUTES` | Opcional | Vigencia del token de acceso; por defecto, 1440 |
| `PASSWORD_RESET_EXPOSE_TOKEN` | `render.yaml` | `true` mientras no se integre un proveedor de correo: el token de restablecimiento (US07) se devuelve en la respuesta para la validación |

Dado que el plan gratuito de Render suspende el servicio tras un periodo de inactividad y limita la vigencia de la base de datos gratuita (Render, s. f.-b), la primera solicitud después de un periodo sin uso puede demorar algunos segundos; esta restricción es aceptable para la etapa de validación académica del producto.

**Mobile Apps — Firebase App Distribution**

1. Crear el proyecto de Qlic en Firebase Console y registrar la aplicación Android con su *package name*.
2. Generar el artefacto de la aplicación nativa desde Android Studio (*Build › Generate Signed App Bundle / APK*) y el de la aplicación multiplataforma con `flutter build apk --release`.
3. Configurar en ambas aplicaciones la URL base del RESTful API desplegado (`https://qlic-backend-api.onrender.com/api/v1`).
4. Cargar cada artefacto en *App Distribution*, asociar el grupo de testers del equipo y añadir notas de versión con el número de release (Firebase, s. f.).

## 4.2. Landing Page & Mobile Application Implementation

### 4.2.1. Sprint 1

#### 4.2.1.1. Sprint Planning 1

La planificación del Sprint 1 se organiza alrededor de las historias US01–US04 del Product Backlog. De acuerdo con la rúbrica, el registro incluye el contexto de la reunión, la fecha, los participantes, la revisión y retrospectiva del sprint anterior, el objetivo orientado al resultado, la velocidad y la suma de puntos. La reunión se realizó el **2026-09-29 a las 5:00 PM**, de forma virtual mediante Discord. Al tratarse de la primera presentación del proyecto, no hubo un Sprint 0 previo para revisar o retroalimentar.

| Campo de planificación | Registro del Sprint 1 |
|---|---|
| Sprint | Sprint 1 |
| Sprint Planning Background | Reunión de planificación para acordar el alcance inicial del Landing Page de Qlic y organizar las historias US01–US04. |
| Date | **2026-09-29** |
| Time | **5:00 PM** |
| Location / modalidad | **Virtual, mediante Discord** |
| Prepared by | **Avila Palacios, Aaron Alexander** |
| Attendees | Avila Palacios, Aaron Alexander; Briceño Llanos, Ayrton Omar; Conde Huashuayo, Sebasthian Alex; Condori Lozano, Alessandro Ramiro |
| Sprint 0 Review Summary | **No aplica:** esta es la primera presentación del proyecto y no hubo un Sprint 0 previo para revisar. |
| Sprint 0 Retrospective Summary | **No aplica:** esta es la primera presentación del proyecto y no hubo un Sprint 0 previo para realizar una retrospectiva. |
| Sprint Goal & User Stories | Ofrecer a visitantes de hogares y negocios una primera experiencia navegable de Qlic mediante US01 (propuesta de valor), US02 (planes), US03 (contacto) y US04 (idioma). |
| Sprint 1 Goal | Una persona visitante podrá comprender el beneficio principal de Qlic, comparar sus planes, solicitar contacto y cambiar el idioma sin depender de una explicación del equipo. El cumplimiento se verifica cuando las cuatro historias US01–US04 recorren sus flujos de aceptación en la Landing Page desplegada. |
| Sprint 1 Velocity | **9 puntos**, correspondientes a la capacidad comprometida para US01–US04 en este primer Sprint. Al no existir un Sprint 0, no se reporta una velocidad histórica anterior. |
| Sum of Story Points | **9** |

| User Story | Resultado esperado | Story Points |
|---|---|---:|
| US01 | Presentar la propuesta de valor, el problema y los beneficios principales de Qlic | 3 |
| US02 | Mostrar una comparación comprensible de los planes disponibles | 2 |
| US03 | Permitir el contacto del visitante con el equipo | 2 |
| US04 | Permitir consultar la página en inglés o español latinoamericano | 2 |
| **Total** |  | **9** |

La validación del Sprint requiere comprobar que una persona puede recorrer la página, identificar el beneficio principal, consultar las diferencias entre planes, enviar una consulta y seleccionar el idioma sin depender de una explicación del equipo.

#### 4.2.1.2. Aspect Leaders and Collaborators

La rúbrica solicita un artefacto **Leadership-and-Collaboration Matrix (LACX)** que indique el líder y los colaboradores de cada aspecto del Sprint. La matriz se construyó a partir de la distribución de tareas proporcionada por el equipo en las capturas adjuntas. `L` significa líder responsable del aspecto y `C` significa colaborador; `C` representa coordinación o apoyo esperado, no evidencia de que la tarea ya esté terminada.

| Team Member (Last Name, First Name) | GitHub Username | Planning & Backlog | SEO & Meta Tags | Landing Page US01–US04 | UX/UI & Design Artifacts | Development Evidence | Testing Evidence | Execution Evidence | Landing Deployment Evidence |
|---|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Avila Palacios, Aaron Alexander | `AaronAvilap` | **L** | **L** | **L** | C | C | C | C | **L** |
| Briceño Llanos, Ayrton Omar | `AyrtonBriceno` | C | C | C | C | **L** | **L** | C | C |
| Conde Huashuayo, Sebasthian Alex | `SebasthianCH` | C | C | C | **L** | C | C | **L** | C |
| Condori Lozano, Alessandro Ramiro | `AlessandroRCL` | C | C | C | C | C | C | C | C |

| Team Member (Last Name, First Name) | GitHub Username | Backend Device Monitoring & Alerting | Services Documentation / IAM / REST API & Swagger | Environment & API Deployment Configuration | Team Collaboration Insights | Versioning, PDF & Release |
|---|---|:---:|:---:|:---:|:---:|:---:|
| Avila Palacios, Aaron Alexander | `AaronAvilap` | C | C | C | C | C |
| Briceño Llanos, Ayrton Omar | `AyrtonBriceno` | **L** | C | C | C | C |
| Conde Huashuayo, Sebasthian Alex | `SebasthianCH` | C | C | C | C | C |
| Condori Lozano, Alessandro Ramiro | `AlessandroRCL` | C | **L** | **L** | **L** | **L** |

**Distribución detallada de tareas informada por el equipo**

- **Avila Palacios, Aaron Alexander:** 3.1.2.3 SEO Tags and Meta Tags; 4.2.1.1 Sprint Planning 1; 4.2.1.2 Aspect Leaders and Collaborators; 4.2.1.3 Sprint Backlog 1 con Engineering Tasks de 4 a 8 horas; 4.2.1.8 Software Deployment Evidence; 4.2.1.9 Team Collaboration Insights during Sprint; Landing Page desplegado (US01, US02, US03 y US04).
- **Briceño Llanos, Ayrton Omar:** 4.2.1.4 Development Evidence; 4.2.1.5 Testing Suite Evidence; Backend Device Monitoring (US10, US11 y US12); Backend Alerting (US15 y US16); corrección y mejora de los Capítulos I y II; 5.1 Conclusiones; 5.2 Bibliografía.
- **Conde Huashuayo, Sebasthian Alex:** 3.1.1 Style Guidelines; 3.1.2.1 Organization Systems; 3.1.2.2 Labelling Systems; 3.1.2.4 Searching Systems; 3.1.2.5 Navigation Systems; 3.1.3.1 Landing Page Wireframe; 3.1.3.2 Landing Page Mock-up; 3.1.4.1 Mobile Applications Wireframes; 3.1.4.2 Mobile Applications Wireflow Diagrams; 3.1.4.3 Mobile Applications Mock-ups; 3.1.4.4 Mobile Applications User Flow Diagrams; 3.1.4.5 Mobile Applications Prototyping; aplicación nativa Kotlin (pantallas de autenticación y home); 4.2.1.6 Execution Evidence.
- **Condori Lozano, Alessandro Ramiro:** 4.1.1 Software Development Environment Configuration; 4.1.2 Source Code Management; 4.1.3 Source Code Style Guide & Conventions; 4.1.4 Software Deployment Configuration; 4.2.1.7 Services Documentation Evidence; Backend IAM (US05 y US06) y despliegue del RESTful API con Swagger; registro de versiones; Project Report Collaboration Insights; consolidación del informe, PDF y release.

Los nombres de usuario de GitHub se registran según la captura proporcionada por el equipo. La evidencia de cada liderazgo debe vincularse posteriormente con la tarea, su estado y el commit, captura o artefacto correspondiente.

#### 4.2.1.3. Sprint Backlog 1

El Sprint Backlog 1 descompone US01–US04 en tareas estimadas entre cuatro y ocho horas. El tablero de Trello de Qlic contiene las listas `To Do`, `In Progress`, `Review` y `Done`, y registra las siete tareas del Sprint (T01–T07) con su responsable, descripción, criterios de aceptación y estado. El tablero está disponible en [Qlic — Sprint Backlog 1](https://trello.com/b/5qkBYnOQ/qlic-sprint-backlog-1). Las estimaciones son de planificación; el estado debe actualizarse con la evidencia de ejecución del Sprint.

| Sprint # | User Story Id | User Story Title | Task Id | Task Title | Task Description | Estimation (Hours) | Assigned To | Status |
|---:|---|---|---|---|---|---:|---|---|
| 1 | US01 | Conocer la propuesta de valor de Qlic | T01 | Hero de propuesta de valor | Construir la sección Hero con el problema, la propuesta de valor y el llamado a la acción | 6 | Condori Lozano, Alessandro Ramiro | To-do |
| 1 | US02 | Comparar los planes de suscripción disponibles | T02 | Comparador de planes | Implementar la comparación de Plan Básico y Plan Gestión Pro con información legible | 6 | Briceño Llanos, Ayrton Omar | To-do |
| 1 | US03 | Contactar al equipo desde el Landing Page | T03 | Formulario de contacto | Implementar el formulario y los canales de contacto del equipo | 4 | Conde Huashuayo, Sebasthian Alex | To-do |
| 1 | US04 | Consultar el Landing Page en el idioma de preferencia | T04 | Selector de idioma | Incorporar el selector para español latinoamericano e inglés | 6 | Avila Palacios, Aaron Alexander | To-do |
| 1 | US01–US04 | Historias del Landing Page | T05 | Responsive y accesibilidad | Aplicar diseño responsive, jerarquía visual, etiquetas accesibles y revisión en móvil | 6 | Condori Lozano, Alessandro Ramiro | To-do |
| 1 | US01–US04 | Historias del Landing Page | T06 | SEO y metadatos | Añadir título, descripción, viewport, URL canónica y metadatos sociales; el detalle SEO se documenta en el capítulo correspondiente | 4 | Avila Palacios, Aaron Alexander | To-do |
| 1 | US01–US04 | Historias del Landing Page | T07 | Verificación del despliegue | Preparar la configuración de hosting estático y verificar la URL de producción | 4 | Briceño Llanos, Ayrton Omar | To-do |

La captura del tablero debe incorporarse como evidencia visual de la revisión junto con el enlace registrado. La vista actual muestra las siete tareas en `To Do`; conforme avance el Sprint, cada tarjeta debe moverse a `In Progress`, `Review` o `Done` según la evidencia correspondiente.

### 4.2.1.4 Development Evidence

En esta sección se documenta la implementación del Web Service backend para la plataforma **Qlic**, desarrollado bajo el estilo arquitectural **RESTful API** utilizando el framework oficial **Spring Boot** sobre el ecosistema Java (JVM / OpenJDK 24) con Kotlin, aplicando principios de **Clean Architecture** y **Domain-Driven Design (Tactical DDD)**.

La solución desacopla la lógica de negocio en dos Bounded Contexts principales: **Device Monitoring** y **Alerting**, integrados con persistencia relacional en **PostgreSQL** y documentados interactivamente mediante **OpenAPI / Swagger**.

---

#### Bounded Context: Device Monitoring

* **US10: Device registration via QR scan**
    * **Descripción:** Permite el enrolamiento de un dispositivo IoT de medición hídrica en el sistema mediante la lectura de su carga útil (payload QR), número de serie, modelo y cuenta de usuario asociada.
    * **Endpoint:** `POST /api/v1/devices`
    * **Código de respuesta:** `201 Created`
    * **Evidencia de ejecución (Postman / Swagger):**

![devices_POST.png](../images/postman_evidence/devices_POST.png)

---

* **US11: Water point assignment**
    * **Descripción:** Vincula lógicamente un dispositivo sensor previamente registrado con un punto de infraestructura hidráulica específico dentro del predio monitoreado.
    * **Endpoint:** `PATCH /api/v1/devices/{id}/water-point`
    * **Código de respuesta:** `200 OK`
    * **Evidencia de ejecución (Postman):**

![devices_PATCH.png](../images/postman_evidence/devices_PATCH.png)

---

* **US12: Device status monitoring**
    * **Descripción:** Consulta el inventario, estado operativo (`ONLINE`, `OFFLINE`, `LOW_BATTERY`), nivel de batería remanente y última marca de sincronización de los dispositivos vinculados a una cuenta.
    * **Endpoint:** `GET /api/v1/devices?accountId={accountId}`
    * **Código de respuesta:** `200 OK`
    * **Evidencia de ejecución (Postman):**

![devices_GET.png](../images/postman_evidence/devices_GET.png)

---

#### Bounded Context: Alerting

* **US15 & US16: Evaluación de lecturas anómalas, listado y consulta de detalle de alerta**
  * **Descripción:** Ingesta lecturas de caudal para detectar fugas sostenidas integrando ahora la resolución dinámica de umbrales por Water Point, el filtro de preferencias de notificación push, el despacho automático a destinatarios autorizados y la consulta individual del detalle de cada alerta (`Alert Detail`).
  * **Endpoints:**
    * `POST /api/v1/alerts/evaluations` (`201 Created` / `204 No Content`)
    * `GET /api/v1/alerts?accountId={accountId}` (`200 OK`)
    * `GET /api/v1/alerts/{alertId}?accountId={accountId}` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger1.png](../images/postman_evidence/swagger1.png)

---

* **US17: Configurar el umbral de consumo**
  * **Descripción:** Permite al suscriptor definir un umbral personalizado (`USER_DEFINED`) para un Water Point y periodo específico. En caso de no definir un valor manual (`customLimitLitersPerHour = null`), el dominio calcula automáticamente un umbral de protección (`SYSTEM_CALCULATED`) equivalente al +25% sobre la línea base histórica del punto de agua.
  * **Endpoints:**
    * `PUT /api/v1/alerts/thresholds` (`200 OK`)
    * `GET /api/v1/alerts/thresholds?accountId={accountId}` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger2.png](../images/postman_evidence/swagger2.png)

---

* **US18: Limitar la frecuencia de notificaciones**
  * **Descripción:** Permite configurar la ventana temporal de agrupación de anomalías (`groupingWindowMinutes`) y el nivel mínimo de urgencia (`INFORMATIONAL`, `MODERATE`, `CRITICAL`) requerido para emitir notificaciones push, evitando la saturación de alertas ante variaciones menores.
  * **Endpoints:**
    * `PUT /api/v1/alerts/preferences` (`200 OK`)
    * `GET /api/v1/alerts/preferences?accountId={accountId}` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger3.png](../images/postman_evidence/swagger3.png)

---

* **US19: Notificar a usuarios autorizados**
  * **Descripción:** Permite al titular de la cuenta registrar usuarios adicionales (familiares o encargados de local), habilitar o deshabilitar su recepción de alertas y despachar notificaciones push a cada destinatario activo cuando se detecta una fuga.
  * **Endpoints:**
    * `POST /api/v1/alerts/recipients` (`201 Created`)
    * `GET /api/v1/alerts/recipients?accountId={accountId}` (`200 OK`)
    * `PATCH /api/v1/alerts/recipients/{recipientId}/toggle` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger4.png](../images/postman_evidence/swagger4.png)

---

* **US20: Confirmar la atención de una alerta**
  * **Descripción:** Permite marcar una alerta activa como atendida (`ACKNOWLEDGED`), registrando en el historial la acción correctiva ejecutada por el suscriptor y preservando la trazabilidad en caso de reaparición de la anomalía.
  * **Endpoint:**
    * `PATCH /api/v1/alerts/{alertId}/acknowledge` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger5.png](../images/postman_evidence/swagger5.png)

---

#### Bounded Context: Subscriptions

* **US31: Contratar un plan de suscripción**
  * **Descripción:** Procesa la contratación de planes para los segmentos Hogares (`HOME_BASIC`, `HOME_PRO`) y PYMES (`PYME_BUSINESS`, `PYME_ENTERPRISE`). Si el pago es confirmado, activa la suscripción por 30 días y habilita el límite correspondiente de Water Points (`201 Created`); si el medio de pago es rechazado, registra el intento fallido y mantiene restringidas las funciones sin activar el plan (`402 Payment Required`).
  * **Endpoint:** `POST /api/v1/subscriptions`
  * **Evidencia de ejecución:**

![swagger6.png](../images/postman_evidence/swagger6.png)

---

* **US32: Acceder a un periodo de prueba**
  * **Descripción:** Otorga por única vez un periodo de prueba gratuito (`TRIAL_ACTIVE`) de 14 días para suscriptores nuevos, indicando su fecha de término. Si el suscriptor intenta solicitar un segundo periodo de prueba, el dominio rechaza la operación (`409 Conflict`). Al concluir el periodo sin contratar un plan, el estado pasa a `TRIAL_EXPIRED` y restringe las funcionalidades pagadas.
  * **Endpoints:**
    * `POST /api/v1/subscriptions/trial` (`201 Created` / `409 Conflict`)
    * `GET /api/v1/subscriptions/current?accountId={accountId}` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger7y.png](../images/postman_evidence/swagger7y.png)

---

* **US33: Cambiar o cancelar el plan contratado**
  * **Descripción:** Permite programar el cambio hacia un nuevo plan aplicable a partir del siguiente ciclo de facturación (`nextBillingPlan`), o solicitar la cancelación de la suscripción (`CANCELLED_PENDING_EXPIRATION`), desactivando cobros futuros (`autoRenew = false`) pero manteniendo el acceso activo hasta la fecha de término del periodo pagado.
  * **Endpoints:**
    * `PATCH /api/v1/subscriptions/{subscriptionId}/plan` (`200 OK`)
    * `POST /api/v1/subscriptions/{subscriptionId}/cancel` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger8.1.png](../images/postman_evidence/swagger8.1.png)

![swagger8.png](../images/postman_evidence/swagger8.png)

---

* **US34: Consultar el historial de pagos**
  * **Descripción:** Recupera el listado cronológico de transacciones del suscriptor, detallando fecha de operación, monto en soles (PEN), plan asociado, medio de pago y estado (`CONFIRMED` o `REJECTED`).
  * **Endpoint:** `GET /api/v1/subscriptions/payments?accountId={accountId}` (`200 OK`)
  * **Evidencia de ejecución:**

![swagger9.png](../images/postman_evidence/swagger9.png)

---

#### Evidencia de Despliegue en la Nube (Cloud Deployment & API Docs)

El servicio backend fue contenerizado mediante un Dockerfile multi-stage con OpenJDK 24 y desplegado en la nube a través de **Render**, enlazado a una base de datos relacional administrada **PostgreSQL**.

* **Base de Datos:** PostgreSQL en Render (Gestión de esquemas automática con Hibernate JPA).
* **URL Base de Producción:** `https://qlic-backend-api.onrender.com`
* **Swagger UI:** `https://qlic-backend-api.onrender.com/swagger-ui/index.html`

![render_dashboard_evidence.png](../images/postman_evidence/render_dashboard_evidence.png)

![swagger_evidence.png](../images/postman_evidence/swagger_evidence.png)

---

### 4.2.1.5 Testing Suite Evidence

Para garantizar la estabilidad del software y el cumplimiento estricto de las reglas de negocio bajo un enfoque BDD (Given-When-Then), se construyó una suite automatizada de pruebas unitarias implementada con **JUnit 5**, desacoplada de la base de datos física mediante repositorios en memoria (In-Memory Test Doubles).

#### Matriz de Casos de Prueba Automatizados

| Bounded Context   | Clase de Prueba                     | User Story | Escenario BDD Validado                                                                         | Resultado  |
|:------------------|:------------------------------------|:-----------|:-----------------------------------------------------------------------------------------------|:-----------|
| **Alerting**      | `AnomalyDetectionServiceTest`       | US15       | Flujo sostenido superior al umbral genera alerta `CRITICAL` con volumen y costo estimado.      | **Passed** |
| **Alerting**      | `AnomalyDetectionServiceTest`       | US15       | Lectura aislada no sostenida es descartada (`null`) previniendo falsos positivos.              | **Passed** |
| **Alerting**      | `AlertManagementCommandHandlerTest` | US17       | Definición de umbral propio aplica valor personalizado (`USER_DEFINED`).                       | **Passed** |
| **Alerting**      | `AlertManagementCommandHandlerTest` | US17       | Ausencia de umbral propio calcula automáticamente +25% sobre línea base (`SYSTEM_CALCULATED`). | **Passed** |
| **Alerting**      | `AlertManagementCommandHandlerTest` | US18       | Supresión de notificación push cuando la urgencia es inferior al mínimo configurado.           | **Passed** |
| **Alerting**      | `AlertManagementCommandHandlerTest` | US19       | Despacho de notificaciones únicamente a los usuarios autorizados habilitados en la cuenta.     | **Passed** |
| **Alerting**      | `AlertManagementCommandHandlerTest` | US20       | Confirmación de atención cambia estado a `ACKNOWLEDGED` y registra la acción realizada.        | **Passed** |
| **Monitoring**    | `DeviceCommandHandlerTest`          | US10       | Registro de sensor mediante QR persiste dispositivo con estado `ONLINE` y batería al 100%.     | **Passed** |
| **Monitoring**    | `DeviceCommandHandlerTest`          | US11       | Asignación de Water Point vincula correctamente el identificador de punto hidráulico.          | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US31       | Pago confirmado activa la suscripción (`ACTIVE`), habilita funciones y registra el cobro.      | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US31       | Pago rechazado impide la activación de la suscripción y registra el motivo de rechazo.         | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US32       | Activación única del periodo de prueba (`TRIAL_ACTIVE`) y bloqueo de segunda solicitud.        | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US32       | Expiración del periodo de prueba (`TRIAL_EXPIRED`) restringe el acceso a funciones pagadas.    | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US33       | Cambio de plan se programa para el siguiente ciclo y cancelación conserva acceso vigente.      | **Passed** |
| **Subscriptions** | `SubscriptionCommandHandlerTest`    | US34       | Consulta de historial devuelve pagos ordenados con fecha, monto, plan asociado y estado.       | **Passed** |

#### Evidencia de Ejecución de Pruebas

Se ejecutó la suite completa de pruebas unitarias desde el entorno de desarrollo, logrando un **100% de éxito (pass rate)** sin fallos ni omisiones en la lógica de dominio.

![6_6.png](../images/postman_evidence/6_6.png)

#### 4.2.1.6. Execution Evidence for Sprint Review

Durante el Sprint 1 el equipo implementó y desplegó dos de los productos de la solución. El Landing Page presenta la propuesta de valor, los planes, el formulario de contacto y el selector de idioma (US01 a US04), y se publica en GitHub Pages. El RESTful API expone los endpoints de registro e inicio de sesión (US05, US06), de registro y consulta de dispositivos (US10 a US12) y de alertas de posible fuga (US15, US16); su ejecución se evidencia mediante la documentación interactiva de la sección 4.2.1.7. Las pantallas core de la aplicación móvil para este Sprint (Sign in, Create account, Dashboard, Alerts, Alert detail, Devices, Add device y Assign Water Point) se presentan mediante los mock-ups de la sección 3.1.4.3 y el prototipo navegable de la sección 3.1.4.5.

*Tabla 4.1. Vistas implementadas en el Sprint 1.*

| Producto | Vista implementada | User Stories | Evidencia |
|---|---|---|---|
| Landing Page | Hero, propuesta de valor y planes (escritorio) | US01, US02 | Figura 4.2 |
| Landing Page | Contacto y selector de idioma (navegador móvil) | US03, US04 | Figura 4.3 |
| RESTful API | Endpoints de Authentication, device-controller y leak-alert-controller | US05, US06, US10 a US12, US15, US16 | Documentación de endpoints en la sección 4.2.1.7 |

![Landing Page desplegado en navegador de escritorio](../images/execution/landing-desktop.png)

*Figura 4.2.* Landing Page de Qlic en navegador de escritorio: sección Hero y planes de suscripción.

![Landing Page desplegado en navegador móvil](../images/execution/landing-mobile.png)

*Figura 4.3.* Landing Page de Qlic en navegador móvil: formulario de contacto y selector de idioma.

#### 4.2.1.7. Services Documentation Evidence for Sprint Review

En esta sección se presenta la documentación de los servicios RESTful implementados durante el Sprint 1. La documentación se genera de forma automática a partir del código fuente en Kotlin con springdoc-openapi, que produce una especificación conforme a OpenAPI Specification 3 y la publica mediante Swagger UI (OpenAPI Initiative, 2021; springdoc, s. f.). De esta manera, la documentación se mantiene sincronizada con la implementación: cada cambio en un controller, en sus recursos de entrada o salida, o en sus anotaciones `@Operation`, `@ApiResponses` y `@Schema`, se refleja en la siguiente ejecución del servicio.

En este Sprint se documentaron siete endpoints agrupados en tres secciones de Swagger UI, una por controller: **Authentication** (bounded context IAM; US05, US06 y TS01), **device-controller** (Device Monitoring; US10, US11 y US12) y **leak-alert-controller** (Alerting; US15 y US16). Las operaciones de Authentication incluyen un resumen, una descripción, los códigos de respuesta posibles y valores de ejemplo para sus campos, de modo que el botón *Try it out* se presenta con datos de muestra precargados; las de Device Monitoring y Alerting se documentan a partir de las firmas de sus controllers y de sus recursos de entrada y salida. La interfaz de la documentación está en inglés, idioma por defecto del producto; los mensajes de error de IAM se devuelven en inglés y, al enviar el encabezado `Accept-Language: es-419`, en español latinoamericano.

La autenticación se implementa con tokens JWT firmados con HS256 (Jones et al., 2015): los endpoints de Authentication son públicos y los demás exigen el encabezado `Authorization: Bearer <token>`, según el esquema de uso de tokens Bearer (Jones & Hardt, 2012). La emisión y validación del token se configuran con el soporte de OAuth 2.0 Resource Server de Spring Security (Spring, s. f.-a), y las contraseñas se almacenan cifradas con BCrypt. El esquema se declara en la especificación como `bearerAuth`, por lo que Swagger UI ofrece el botón *Authorize* para probar los recursos protegidos. Los errores se devuelven con el formato *Problem Details for HTTP APIs* (Nottingham et al., 2023), que incluye el código HTTP, un título, un detalle legible y un código de error estable (`code`) para que las aplicaciones móviles puedan tratar cada caso.

**Acceso a la documentación**

| Recurso | URL |
|---|---|
| Swagger UI (entorno desplegado) | https://qlic-backend-api.onrender.com/swagger-ui.html |
| Especificación OpenAPI en JSON | https://qlic-backend-api.onrender.com/v3/api-docs |
| Swagger UI (entorno local) | http://localhost:8080/swagger-ui.html |
| Repositorio del RESTful API | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/qlic-backend-api |

**Endpoints documentados**

| Sección | Acción implementada | Verbo HTTP | Sintaxis de llamada | Parámetros | Respuestas | Historia |
|---|---|---|---|---|---|---|
| Authentication | Registrar una cuenta de suscriptor | POST | `/api/v1/authentication/sign-up` | Body: `fullName`, `email`, `password` (8 a 72 caracteres), `phone` (opcional), `acceptTerms` | `201` cuenta creada · `400` datos inválidos o términos no aceptados · `409` correo ya registrado | US05 |
| Authentication | Iniciar sesión y obtener el token de acceso | POST | `/api/v1/authentication/sign-in` | Body: `email`, `password` | `200` token emitido · `400` solicitud incompleta · `401` credenciales inválidas | US06, TS01 |
| device-controller | Registrar un dispositivo IoT mediante código QR | POST | `/api/v1/devices` | Body: `qrCodePayload`, `serialNumber`, `model`, `accountId` | `201` dispositivo registrado (si el número de serie ya existe, devuelve el dispositivo registrado) · `400` cuerpo inválido · `401` sin token | US10 |
| device-controller | Asignar un dispositivo a un Water Point | PATCH | `/api/v1/devices/{id}/water-point` | Path: `id` (UUID) · Body: `waterPointId` | `200` dispositivo actualizado · `401` sin token · `404` dispositivo inexistente | US11 |
| device-controller | Consultar el estado de los dispositivos registrados | GET | `/api/v1/devices?accountId={accountId}` | Query: `accountId` (UUID) | `200` relación de dispositivos (vacía si no hay registros) · `401` sin token | US12 |
| leak-alert-controller | Evaluar una lectura de consumo y generar una alerta de posible fuga | POST | `/api/v1/alerts/evaluations` | Body: `accountId`, `waterPointId`, `currentFlowLitersPerHour`, `thresholdLimit`, `isSustained` | `201` alerta generada o escalada · `204` lectura sin anomalía · `400` cuerpo inválido · `401` sin token | US15 |
| leak-alert-controller | Consultar las alertas de una cuenta | GET | `/api/v1/alerts?accountId={accountId}` | Query: `accountId` (UUID) | `200` relación de alertas (vacía si no hay registros) · `401` sin token | US16 |

**Ejemplos de llamada y respuesta — Authentication**

*Registro de cuenta (US05 - Escenario 1).* La respuesta `201 Created` devuelve los identificadores del suscriptor y de su cuenta; la contraseña nunca se incluye en la respuesta.

```http
POST /api/v1/authentication/sign-up
Content-Type: application/json

{
  "fullName": "Claudia Morales",
  "email": "claudia.morales@example.com",
  "password": "Qlic2026!",
  "phone": "+51987654321",
  "acceptTerms": true
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "subscriberId": "8f2c6a1e-4b7d-4c1a-9e3f-2d5b7a9c1e40",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "email": "claudia.morales@example.com",
  "fullName": "Claudia Morales",
  "phone": "+51987654321",
  "accountName": "Claudia Morales's account",
  "createdAt": "2026-10-05T15:04:12.381Z"
}
```

*Correo ya registrado (US05 - Escenario 2).* El API no crea una nueva cuenta y responde `409 Conflict`.

```http
HTTP/1.1 409 Conflict
Content-Type: application/problem+json

{
  "type": "about:blank",
  "title": "Conflict",
  "status": 409,
  "detail": "The email claudia.morales@example.com is already registered.",
  "instance": "/api/v1/authentication/sign-up",
  "code": "iam.email.already-registered"
}
```

*Inicio de sesión (US06 - Escenario 1).* La respuesta `200 OK` incluye el token de acceso, su tipo y su fecha de expiración; la aplicación móvil lo envía en las siguientes solicitudes.

```http
POST /api/v1/authentication/sign-in
Content-Type: application/json

{
  "email": "claudia.morales@example.com",
  "password": "Qlic2026!"
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "subscriberId": "8f2c6a1e-4b7d-4c1a-9e3f-2d5b7a9c1e40",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "email": "claudia.morales@example.com",
  "fullName": "Claudia Morales",
  "token": "eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJxbGljLWJhY2tlbmQtYXBpIiwic3ViIjoi...",
  "tokenType": "Bearer",
  "expiresAt": "2026-10-06T15:05:40.112Z"
}
```

*Credenciales inválidas (US06 - Escenario 2), solicitado en español latinoamericano.* El mensaje es el mismo cuando el correo no existe y cuando la contraseña es incorrecta, de modo que la respuesta no revela qué correos se encuentran registrados.

```http
POST /api/v1/authentication/sign-in
Accept-Language: es-419
Content-Type: application/json

{ "email": "claudia.morales@example.com", "password": "incorrecta" }
```

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/problem+json

{
  "type": "about:blank",
  "title": "Unauthorized",
  "status": 401,
  "detail": "Las credenciales no son válidas.",
  "instance": "/api/v1/authentication/sign-in",
  "code": "iam.credentials.invalid"
}
```

**Ejemplos de llamada y respuesta — device-controller**

*Registro de un dispositivo (US10).* El dispositivo se registra con estado `ONLINE` y batería al 100 %; si el número de serie ya existe, el API devuelve el dispositivo registrado en lugar de crear un duplicado.

```http
POST /api/v1/devices
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{
  "qrCodePayload": "QLIC|SN-QLC-0001|FlowMeter",
  "serialNumber": "SN-QLC-0001",
  "model": "FlowMeter",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61"
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80",
  "serialNumber": "SN-QLC-0001",
  "model": "FlowMeter",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "waterPointId": null,
  "status": "ONLINE",
  "batteryPercentage": 100,
  "lastSyncAt": "2026-10-05T10:15:03.204"
}
```

*Asignación a un Water Point (US11).* La respuesta `200 OK` devuelve el dispositivo con el `waterPointId` asignado; si el identificador del dispositivo no existe, el API responde `404 Not Found` sin cuerpo.

```http
PATCH /api/v1/devices/5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80/water-point
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{ "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13" }
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80",
  "serialNumber": "SN-QLC-0001",
  "model": "FlowMeter",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
  "status": "ONLINE",
  "batteryPercentage": 100,
  "lastSyncAt": "2026-10-05T10:15:03.204"
}
```

*Consulta de dispositivos (US12).* La respuesta es la relación de dispositivos de la cuenta con su estado, nivel de batería y última sincronización.

```http
GET /api/v1/devices?accountId=c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": "5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80",
    "serialNumber": "SN-QLC-0001",
    "model": "FlowMeter",
    "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
    "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
    "status": "ONLINE",
    "batteryPercentage": 100,
    "lastSyncAt": "2026-10-05T10:15:03.204"
  }
]
```

**Ejemplos de llamada y respuesta — leak-alert-controller**

*Evaluación de una lectura (US15).* Un caudal sostenido de 120 L/h frente a un umbral de 50 L/h supera el umbral en más de 80 %, por lo que el API abre una alerta `CRITICAL` con el volumen y el costo estimados y la acción recomendada. Si la lectura no es sostenida o está dentro del umbral, responde `204 No Content` y no genera alerta.

```http
POST /api/v1/alerts/evaluations
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
  "currentFlowLitersPerHour": 120.0,
  "thresholdLimit": 50.0,
  "isSustained": true
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "e18b4c2d-6a7f-4b3e-9d1c-0f5a2b8c7d64",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
  "state": "ACTIVE",
  "urgency": "CRITICAL",
  "detectedAt": "2026-10-05T10:20:41.517",
  "estimatedVolumeLiters": 180.00,
  "estimatedCostSoles": 0.90000,
  "recommendedAction": "Cierre la llave de paso general inmediatamente y verifique roturas en tuberia empotrada."
}
```

*Consulta de alertas (US16).* La respuesta `200 OK` es la relación de alertas de la cuenta con la misma estructura del ejemplo anterior.

```http
GET /api/v1/alerts?accountId=c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```

*Recurso protegido sin token (TS01 - Escenario 3).* Cualquier endpoint de device-controller o leak-alert-controller invocado sin token responde `401 Unauthorized`.

```http
GET /api/v1/alerts?accountId=c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61

HTTP/1.1 401 Unauthorized
WWW-Authenticate: Bearer
```

**Commits relacionados con la documentación de servicios**

| Repositorio | Branch | Commit ID | Mensaje del commit | Fecha |
|---|---|---|---|---|
| qlic-backend-api | `main` | `7e2eca3` | feat(alerting): implement US15 and US16 for leak detection evaluation and account alert retrieval | 2026-10-01 |
| qlic-backend-api | `main` | `e7d8b17` | feat(monitoring): implement US10, US11, and US12 for QR device onboarding, water point linking, and telemetry status | 2026-10-01 |
| qlic-backend-api | `main` | `c224c3f` | feat(docker): add multi-stage Dockerfile for cloud deployment | 2026-10-02 |
| qlic-backend-api | `feature/iam-authentication` | `dc5424d` | feat(iam): add domain layer for subscriber accounts (US05, US06) | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `21a5cc4` | feat(iam): implement sign-up and sign-in command handlers | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `64be58e` | feat(iam): expose authentication endpoints with JWT security (TS01) | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `efc8893` | feat(i18n): add en_US and es_419 message bundles for IAM responses | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `a77aefc` | docs(api): configure OpenAPI 3 and Swagger UI with bearer authentication | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `12a8cee` | test(iam): add unit and integration tests for registration and authentication | 2026-10-06 |
| qlic-backend-api | `feature/iam-authentication` | `24c3ea1` | chore(config): add dev and prod profiles and project README | 2026-10-06 |

#### 4.2.1.8. Software Deployment Evidence for Sprint Review

El Landing Page de Qlic se publica como sitio estático mediante GitHub Pages. La configuración de Pages utiliza GitHub Actions como fuente de despliegue, publica la rama `main` y mantiene activada la opción **Enforce HTTPS**. La evidencia confirma que el sitio está disponible públicamente y que el último despliegue fue realizado por `AaronAvilap`.

| Elemento de despliegue | Registro verificable |
|---|---|
| Producto | Landing Page estático |
| Proveedor | GitHub Pages, organización `1ACC0238-2620-13984-Aplicaciones-Mov` |
| Fuente de publicación | GitHub Actions, workflow `Deploy Qlic to GitHub Pages` |
| Rama publicada | `main` |
| URL pública | https://1acc0238-2620-13984-aplicaciones-mov.github.io/qlic-landing-page/ |
| Commit publicado | `29e4694` — `feat(landing): migrate to html css javascript and add seo metadata` |
| Seguridad de transporte | HTTPS forzado por el dominio predeterminado de GitHub Pages |
| Responsable del último despliegue | `AaronAvilap` |

![Configuración de GitHub Pages del Landing Page de Qlic](../images/deployment/github-pages-qlic.png)

*Figura 4.9.* Configuración de GitHub Pages: URL pública, fuente GitHub Actions, último despliegue y HTTPS forzado.

La evidencia corresponde al repositorio `qlic-landing-page` y permite comprobar que US01, US02, US03 y US04 están disponibles en la versión desplegada.

#### 4.2.1.9. Team Collaboration Insights during Sprint

El equipo declara el uso de GitHub, GitFlow, Trello y WhatsApp para organizar el trabajo. La matriz LACX de la sección 4.2.1.2 establece la distribución informada por el equipo: Aaron coordina planificación, backlog, SEO y despliegue del Landing Page; Ayrton coordina desarrollo, pruebas, monitoreo y alertas; Sebasthian coordina los artefactos UX/UI y la evidencia de ejecución; Alessandro coordina servicios, configuración, versionado, colaboración y release. La interpretación definitiva debe basarse en capturas de GitHub Insights y del tablero correspondientes al intervalo real del Sprint.

| Integrante | Responsabilidad de colaboración en el Sprint 1 | Evidencia que debe vincularse |
|---|---|---|
| Avila Palacios, Aaron Alexander | Planificación, backlog, SEO, despliegue del Landing Page y consolidación de su evidencia | Acta de planificación, captura/URL de despliegue, commits de SEO y backlog |
| Briceño Llanos, Ayrton Omar | Desarrollo, pruebas, monitoreo de dispositivos y alertas del backend | Commits o capturas de desarrollo, suite de pruebas, monitoreo y alertas |
| Conde Huashuayo, Sebasthian Alex | Artefactos UX/UI, aplicación nativa y evidencia de ejecución | Wireframes, mock-ups, flujos y captura de ejecución |
| Condori Lozano, Alessandro Ramiro | Servicios/API, configuración, versionado, colaboración, PDF y release | Configuración, Swagger, registro de versiones, acuerdos y release |

Para la entrega se requiere una captura de GitHub Insights con el periodo del Sprint, una captura del tablero de Trello y un registro de los acuerdos o bloqueos. La imagen general de actividad de AV1 no está disponible en esta rama; no se sustituye por una captura de otro periodo.

### 4.2.2. Sprint 2

#### 4.2.2.7. Services Documentation Evidence for Sprint Review

En esta sección se presenta la documentación de los servicios RESTful implementados durante el Sprint 2. Al igual que en el Sprint 1, la especificación OpenAPI 3 se genera a partir del código fuente en Kotlin con springdoc-openapi y se publica mediante Swagger UI, por lo que se mantiene sincronizada con la implementación (OpenAPI Initiative, 2021; springdoc, s. f.). En este Sprint, el RESTful API pasa de tres a seis bounded contexts: se completan IAM (US07, US08 y US09), Alerting (US16 a US20) y Subscriptions (US31 a US34), y se incorporan Consumption Analytics (US24), la ingesta de lecturas de consumo en Device Monitoring y Support (US35 a US38). Los nuevos controllers de IAM, Consumption Analytics y Support documentan en Swagger UI el resumen, la descripción, los códigos de respuesta y valores de ejemplo de cada operación.

Dos decisiones de diseño del Sprint 2 se reflejan en la documentación. Primero, los endpoints nuevos de IAM, Consumption Analytics y Support obtienen la cuenta y el permiso del solicitante a partir del token de acceso, por lo que no reciben un `accountId` en la solicitud: el token emitido al iniciar sesión incluye las *claims* `accountId`, `permission` (`OWNER`, `OPERATOR` o `VIEWER`) y `scope` (Jones et al., 2015). Segundo, el acceso compartido de US08 se aplica en la cadena de filtros de Spring Security (Spring, s. f.-a): las solicitudes `POST`, `PUT`, `PATCH` y `DELETE` sobre dispositivos, alertas, consumo, incidencias y suscripciones exigen el *scope* `account:write`, que no se otorga a los usuarios con permiso `VIEWER`; en ese caso el API responde `403 Forbidden` con el formato *Problem Details for HTTP APIs* (Nottingham et al., 2023).

**Acceso a la documentación**

| Recurso | URL |
|---|---|
| Swagger UI (entorno desplegado) | https://qlic-backend-api.onrender.com/swagger-ui.html |
| Especificación OpenAPI en JSON | https://qlic-backend-api.onrender.com/v3/api-docs |
| Swagger UI (entorno local) | http://localhost:8080/swagger-ui.html |
| Repositorio del RESTful API | https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/qlic-backend-api |

**Endpoints documentados en el Sprint 2**

| Sección | Acción implementada | Verbo HTTP | Sintaxis de llamada | Parámetros | Respuestas | Historia |
|---|---|---|---|---|---|---|
| Authentication | Iniciar sesión en la cuenta propia o en una cuenta compartida | POST | `/api/v1/authentication/sign-in` | Body: `email`, `password`, `accountId` (opcional) | `200` token con `permission` · `401` credenciales inválidas · `403` cuenta no compartida con el suscriptor | US06, US08 |
| Password Reset | Solicitar un enlace de restablecimiento de contraseña | POST | `/api/v1/authentication/password-reset/request` | Body: `email` | `202` solicitud aceptada (misma respuesta si el correo no existe) · `400` solicitud incompleta | US07 |
| Password Reset | Definir una nueva contraseña con el token del enlace | POST | `/api/v1/authentication/password-reset/confirm` | Body: `token`, `newPassword` (8 a 72 caracteres) | `204` contraseña actualizada · `400` token vencido, usado o inexistente | US07 |
| Shared Access | Invitar a un usuario a la cuenta | POST | `/api/v1/invitations` | Body: `email`, `permission` (`VIEWER` u `OPERATOR`) | `201` invitación registrada y notificada · `403` el solicitante no es el titular · `409` límite del plan alcanzado o persona ya invitada | US08 |
| Shared Access | Consultar las invitaciones emitidas por la cuenta | GET | `/api/v1/invitations` | — | `200` relación de invitaciones con su estado | US08 |
| Shared Access | Consultar las invitaciones recibidas pendientes | GET | `/api/v1/invitations/received` | — | `200` relación de invitaciones dirigidas al correo de la sesión | US08 |
| Shared Access | Aceptar una invitación | POST | `/api/v1/invitations/{invitationId}/acceptance` | Path: `invitationId` | `201` acceso otorgado · `403` invitación dirigida a otro correo · `409` invitación vencida o ya utilizada | US08 |
| Shared Access | Consultar los usuarios autorizados de la cuenta | GET | `/api/v1/authorized-users` | — | `200` relación de usuarios con su nivel de permiso | US08 |
| Shared Access | Revocar el acceso de un usuario autorizado | DELETE | `/api/v1/authorized-users/{authorizedUserId}` | Path: `authorizedUserId` | `204` acceso revocado · `403` el solicitante no es el titular · `404` usuario inexistente en la cuenta | US08 |
| Accounts | Consultar las cuentas compartidas con el suscriptor | GET | `/api/v1/accounts/shared-with-me` | — | `200` relación de cuentas con el permiso otorgado | US08 |
| Accounts | Consultar el perfil y la cuenta de la sesión | GET | `/api/v1/accounts/me` | — | `200` perfil, nombre del local y permiso | US09 |
| Accounts | Actualizar los datos del perfil | PUT | `/api/v1/accounts/me` | Body: `fullName`, `phone` (opcional), `accountName` (opcional, solo titular) | `200` perfil actualizado · `400` dato obligatorio vacío, indicado en `errors` · `403` renombrar el local sin ser titular | US09 |
| leak-alert-controller | Consultar el detalle de una alerta | GET | `/api/v1/alerts/{alertId}?accountId={accountId}` | Path: `alertId` · Query: `accountId` | `200` alerta · `404` alerta inexistente | US16 |
| leak-alert-controller | Configurar el umbral de consumo de un Water Point | PUT | `/api/v1/alerts/thresholds` | Body: `accountId`, `waterPointId`, `period`, `customLimitLitersPerHour` (opcional), `baselineLitersPerHour` | `200` umbral `USER_DEFINED` o `SYSTEM_CALCULATED` | US17 |
| leak-alert-controller | Consultar los umbrales de la cuenta | GET | `/api/v1/alerts/thresholds?accountId={accountId}` | Query: `accountId` | `200` relación de umbrales | US17 |
| leak-alert-controller | Configurar las preferencias de notificación | PUT | `/api/v1/alerts/preferences` | Body: `accountId`, `groupingWindowMinutes`, `minimumUrgency` | `200` preferencias registradas | US18 |
| leak-alert-controller | Consultar las preferencias de notificación | GET | `/api/v1/alerts/preferences?accountId={accountId}` | Query: `accountId` | `200` preferencias | US18 |
| leak-alert-controller | Registrar un destinatario de alertas | POST | `/api/v1/alerts/recipients` | Body: `accountId`, `fullName`, `email`, `devicePushToken`, `enabled` | `201` destinatario registrado | US19 |
| leak-alert-controller | Consultar los destinatarios de alertas | GET | `/api/v1/alerts/recipients?accountId={accountId}` | Query: `accountId` | `200` relación de destinatarios | US19 |
| leak-alert-controller | Habilitar o deshabilitar un destinatario | PATCH | `/api/v1/alerts/recipients/{recipientId}/toggle` | Path: `recipientId` · Body: `enabled` | `200` destinatario actualizado | US19 |
| leak-alert-controller | Confirmar la atención de una alerta | PATCH | `/api/v1/alerts/{alertId}/acknowledge` | Path: `alertId` · Body: `accountId`, `actionTaken` | `200` alerta en estado `ACKNOWLEDGED` | US20 |
| subscription-controller | Contratar un plan de suscripción | POST | `/api/v1/subscriptions` | Body: `accountId`, `plan`, `paymentMethod`, `simulatePaymentRejected` | `201` suscripción activa · `402` pago rechazado | US31 |
| subscription-controller | Activar el periodo de prueba | POST | `/api/v1/subscriptions/trial` | Body: `accountId` | `201` prueba activa · `409` prueba ya utilizada | US32 |
| subscription-controller | Consultar la suscripción vigente | GET | `/api/v1/subscriptions/current?accountId={accountId}` | Query: `accountId` | `200` suscripción · `404` sin suscripción | US32 |
| subscription-controller | Cambiar el plan para el siguiente periodo | PATCH | `/api/v1/subscriptions/{subscriptionId}/plan` | Path: `subscriptionId` · Body: `newPlan` | `200` cambio programado | US33 |
| subscription-controller | Cancelar la suscripción | POST | `/api/v1/subscriptions/{subscriptionId}/cancel` | Path: `subscriptionId` | `200` acceso vigente hasta el fin del periodo | US33 |
| subscription-controller | Consultar el historial de pagos | GET | `/api/v1/subscriptions/payments?accountId={accountId}` | Query: `accountId` | `200` pagos con fecha, monto, plan y estado | US34 |
| Consumption Readings | Registrar una lectura de consumo de un dispositivo | POST | `/api/v1/consumption-readings` | Body: `deviceId`, `volumeLiters`, `recordedAt` (opcional) | `201` lectura registrada · `404` dispositivo inexistente en la cuenta · `409` dispositivo sin Water Point | US24 |
| Consumption Reports | Declarar el horario de actividad del local | PUT | `/api/v1/consumption/activity-schedule` | Body: `openingTime`, `closingTime`, `activeDays` | `200` horario registrado · `400` horario inválido | US24 |
| Consumption Reports | Consultar el horario de actividad del local | GET | `/api/v1/consumption/activity-schedule` | — | `200` horario · `404` horario no declarado | US24 |
| Consumption Reports | Consultar el consumo dentro y fuera del horario de actividad | GET | `/api/v1/consumption/reports/activity-hours?from={fecha}&to={fecha}` | Query: `from`, `to` (ISO 8601) | `200` reporte del periodo · `400` periodo inválido | US24 |
| Incidents | Registrar una incidencia | POST | `/api/v1/incidents` | Body: `description`, `deviceId`, `waterPointId` o `alertId` | `201` incidencia en estado `PENDING` · `400` sin descripción o sin activo afectado · `404` dispositivo o alerta de otra cuenta · `409` alerta no activa | US35 |
| Incidents | Consultar las incidencias de la cuenta | GET | `/api/v1/incidents` | — | `200` incidencias con fecha de registro, dispositivo y estado | US37 |
| Incidents | Consultar el detalle de una incidencia | GET | `/api/v1/incidents/{incidentId}` | Path: `incidentId` | `200` incidencia · `404` incidencia inexistente en la cuenta | US37 |
| Incidents | Solicitar una visita técnica | POST | `/api/v1/incidents/{incidentId}/technical-visit` | Path: `incidentId` · Body: `preferredDate`, `fromTime`, `toTime`, `notes` (opcional) | `201` incidencia en `VISIT_REQUESTED` · `403` plan sin cobertura · `409` incidencia no pendiente | US36 |
| Support Staff | Asignar un técnico a la visita | POST | `/api/v1/incidents/{incidentId}/technical-visit/assignment` | Path: `incidentId` · Body: `technicianId` (opcional), `scheduledAt` | `200` incidencia en `IN_PROGRESS` y suscriptor notificado · `409` sin visita solicitada | US36 |
| Support Staff | Registrar la resolución de una incidencia | POST | `/api/v1/incidents/{incidentId}/resolution` | Path: `incidentId` · Body: `description` | `200` incidencia en `RESOLVED` · `409` incidencia ya resuelta | US37 |
| Support Staff | Consultar los técnicos activos | GET | `/api/v1/technicians` | — | `200` relación de técnicos | US36 |
| Terms of Service | Consultar los términos y condiciones vigentes | GET | `/api/v1/terms-of-service/current` | Header: `Accept-Language` (opcional) | `200` documento con versión y fecha de actualización | US38 |

Todos los endpoints de la tabla, salvo los de Password Reset y Terms of Service, exigen el encabezado `Authorization: Bearer <token>` y responden `401 Unauthorized` sin él (TS01).

**Ejemplos de llamada y respuesta — IAM**

*Solicitud de restablecimiento (US07 - Escenario 1).* El API emite un token de un solo uso con 30 minutos de vigencia y envía el enlace al correo. La respuesta es la misma cuando el correo no está registrado, de modo que no revela qué cuentas existen. Mientras no se integre un proveedor de correo, el token se incluye en la respuesta para la validación del flujo.

```http
POST /api/v1/authentication/password-reset/request
Content-Type: application/json

{ "email": "claudia.morales@example.com" }
```

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "message": "If the email belongs to a Qlic account, a reset link valid for a limited time was sent to it.",
  "resetToken": "Jx2f9QmKc7bV1sT0aLwE4nR8yP6uZ3dH5gN-oY1iK2A",
  "expiresAt": "2026-11-10T21:45:00Z"
}
```

*Enlace vencido (US07 - Escenario 2).* El API rechaza la operación e indica que se debe solicitar un nuevo enlace.

```http
POST /api/v1/authentication/password-reset/confirm
Accept-Language: es-419
Content-Type: application/json

{ "token": "Jx2f9QmKc7bV1sT0aLwE4nR8yP6uZ3dH5gN-oY1iK2A", "newPassword": "NuevaClave2026!" }
```

```http
HTTP/1.1 400 Bad Request
Content-Type: application/problem+json

{
  "type": "about:blank",
  "title": "Bad Request",
  "status": 400,
  "detail": "El enlace de restablecimiento venció. Solicite un nuevo enlace para definir su contraseña.",
  "instance": "/api/v1/authentication/password-reset/confirm",
  "code": "iam.reset-token.expired"
}
```

*Invitación de un usuario adicional (US08 - Escenario 1).* Solo el titular puede invitar; la cantidad de usuarios adicionales depende del plan vigente (uno en el periodo de prueba y en Home Basic, tres en Home Pro, cinco en PYME Business y diez en PYME Enterprise).

```http
POST /api/v1/invitations
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{ "email": "jorge.quispe@example.com", "permission": "VIEWER" }
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0b6f3d2a-8e1c-4a7b-9f2d-6c5e4a3b2d10",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "accountName": null,
  "invitedEmail": "jorge.quispe@example.com",
  "permission": "VIEWER",
  "state": "PENDING",
  "createdAt": "2026-11-10T20:30:00Z",
  "expiresAt": "2026-11-17T20:30:00Z"
}
```

*Acceso de solo consulta (US08 - Escenario 2).* El invitado acepta la invitación e inicia sesión en la cuenta compartida enviando su `accountId`; el token emitido lleva `permission: VIEWER`. Con ese token puede consultar los dispositivos, pero al intentar modificar su configuración el API rechaza la operación.

```http
POST /api/v1/authentication/sign-in
Content-Type: application/json

{ "email": "jorge.quispe@example.com", "password": "Qlic2026!", "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61" }
```

```http
PATCH /api/v1/devices/5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80/water-point
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...(token VIEWER)
Content-Type: application/json

{ "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13" }
```

```http
HTTP/1.1 403 Forbidden
Content-Type: application/problem+json

{
  "type": "about:blank",
  "title": "Forbidden",
  "status": 403,
  "detail": "You do not have the permission required for this operation.",
  "instance": "/api/v1/devices/5a9e2c7b-1d4f-4e8a-b3c6-7f2d9a1e5b80/water-point",
  "code": "iam.permission.denied"
}
```

*Actualización del perfil (US09 - Escenarios 1 y 2).* Los cambios se reflejan en las siguientes consultas de `GET /api/v1/accounts/me`. Si el nombre completo se envía vacío, el API no registra los cambios e indica el dato pendiente en `errors`.

```http
PUT /api/v1/accounts/me
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{ "fullName": "Claudia Morales Ríos", "phone": "+51912345678", "accountName": "Bodega Morales - Surco" }
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "subscriberId": "8f2c6a1e-4b7d-4c1a-9e3f-2d5b7a9c1e40",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "email": "claudia.morales@example.com",
  "fullName": "Claudia Morales Ríos",
  "phone": "+51912345678",
  "accountName": "Bodega Morales - Surco",
  "permission": "OWNER",
  "memberSince": "2026-10-05T15:04:12.381Z"
}
```

```http
HTTP/1.1 400 Bad Request
Content-Type: application/problem+json

{
  "type": "about:blank",
  "title": "Bad Request",
  "status": 400,
  "detail": "One or more fields are not valid.",
  "instance": "/api/v1/accounts/me",
  "code": "error.validation",
  "errors": { "fullName": "Full name is required." }
}
```

**Ejemplos de llamada y respuesta — Consumption Analytics**

*Consumo fuera del horario de actividad (US24 - Escenario 1).* El suscriptor declara el horario del local (de 08:00 a 20:00, de lunes a sábado). El reporte agrega las lecturas del periodo por Water Point y diferencia el volumen registrado dentro y fuera de ese horario; los Water Points se ordenan por el consumo fuera de horario, de modo que el desperdicio más relevante aparece primero. Si el local no declaró su horario, el reporte devuelve solo los totales (`scheduleDefined: false`).

```http
PUT /api/v1/consumption/activity-schedule
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{
  "openingTime": "08:00",
  "closingTime": "20:00",
  "activeDays": ["MONDAY", "TUESDAY", "WEDNESDAY", "THURSDAY", "FRIDAY", "SATURDAY"]
}
```

```http
GET /api/v1/consumption/reports/activity-hours?from=2026-11-02&to=2026-11-08
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "from": "2026-11-02",
  "to": "2026-11-08",
  "scheduleDefined": true,
  "schedule": {
    "openingTime": "08:00",
    "closingTime": "20:00",
    "activeDays": ["MONDAY", "TUESDAY", "WEDNESDAY", "THURSDAY", "FRIDAY", "SATURDAY"],
    "updatedAt": null
  },
  "totalLiters": 1250.00,
  "withinActivityLiters": 1010.00,
  "outsideActivityLiters": 240.00,
  "outsideActivityPercentage": 19.20,
  "byWaterPoint": [
    {
      "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
      "totalLiters": 820.00,
      "withinActivityLiters": 640.00,
      "outsideActivityLiters": 180.00
    },
    {
      "waterPointId": "2c8e5f1a-3b7d-4e9c-a6f2-1d4b8c7e9a05",
      "totalLiters": 430.00,
      "withinActivityLiters": 370.00,
      "outsideActivityLiters": 60.00
    }
  ]
}
```

**Ejemplos de llamada y respuesta — Support**

*Registro de una incidencia desde una alerta (US35 - Escenario 2).* Al enviar el `alertId` de una alerta activa, la incidencia se crea en estado `PENDING`, con origen `ALERT_DERIVED` y asociada al Water Point de la alerta. Sin dispositivo, Water Point ni alerta, el API responde `400` con el código `support.incident.asset-required`.

```http
POST /api/v1/incidents
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{
  "description": "Confirmed leak under the kitchen sink.",
  "alertId": "e18b4c2d-6a7f-4b3e-9d1c-0f5a2b8c7d64"
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "9c1d7e4b-2a6f-4c8d-b5e3-7f0a1b2c3d48",
  "accountId": "c41d8e7a-2f6b-4a9d-8c3e-5b1a7f9d2e61",
  "description": "Confirmed leak under the kitchen sink.",
  "deviceId": null,
  "waterPointId": "7d3f1b2a-9c4e-4f6a-8b1d-2e5c7a9f0b13",
  "alertId": "e18b4c2d-6a7f-4b3e-9d1c-0f5a2b8c7d64",
  "origin": "ALERT_DERIVED",
  "state": "PENDING",
  "registeredAt": "2026-11-10T20:41:05Z",
  "updatedAt": "2026-11-10T20:41:05Z",
  "technicalVisit": null,
  "resolution": null,
  "resolvedAt": null
}
```

*Solicitud de visita técnica (US36 - Escenario 1).* La incidencia debe estar en estado `PENDING` y el plan vigente debe cubrir la visita; la incidencia pasa a `VISIT_REQUESTED`.

```http
POST /api/v1/incidents/9c1d7e4b-2a6f-4c8d-b5e3-7f0a1b2c3d48/technical-visit
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{ "preferredDate": "2026-11-13", "fromTime": "09:00", "toTime": "13:00", "notes": "Ask for Claudia at the store." }
```

*Asignación del técnico (US36 - Escenario 2).* El personal de soporte registra la fecha programada; si no indica el técnico, se asigna el de menor carga de visitas en atención. El API notifica al suscriptor y la incidencia pasa a `IN_PROGRESS`; la respuesta se muestra en extracto.

```http
POST /api/v1/incidents/9c1d7e4b-2a6f-4c8d-b5e3-7f0a1b2c3d48/technical-visit/assignment
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Content-Type: application/json

{ "scheduledAt": "2026-11-13T10:00:00" }
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "9c1d7e4b-2a6f-4c8d-b5e3-7f0a1b2c3d48",
  "state": "IN_PROGRESS",
  "technicalVisit": {
    "id": "4e2a9b7c-1f3d-4a6e-8c5b-0d9f2e1a7b36",
    "preferredDate": "2026-11-13",
    "fromTime": "09:00",
    "toTime": "13:00",
    "notes": "Ask for Claudia at the store.",
    "state": "ASSIGNED",
    "technicianId": "a3f1c8e2-5b7d-4d9a-b2e6-8c1f0a4d7e93",
    "technicianName": "Miguel Torres",
    "scheduledAt": "2026-11-13T10:00",
    "requestedAt": "2026-11-10T20:45:12Z"
  }
}
```

*Seguimiento de incidencias (US37 - Escenario 1).* `GET /api/v1/incidents` devuelve las incidencias de la cuenta, de la más reciente a la más antigua, con su fecha de registro (`registeredAt`), dispositivo asociado (`deviceId`) y estado actual (`PENDING`, `VISIT_REQUESTED`, `IN_PROGRESS` o `RESOLVED`), con la misma estructura del ejemplo anterior.

*Términos y condiciones (US38 - Escenario 1).* El endpoint es público, porque el documento se muestra en el Landing Page y en la pantalla Create account antes de que exista una sesión; devuelve la versión vigente y su fecha de actualización en el idioma solicitado.

```http
GET /api/v1/terms-of-service/current
Accept-Language: es-419
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "version": "1.0",
  "language": "es",
  "title": "Términos y condiciones de Qlic",
  "content": "1. Aceptación de los términos. Al crear una cuenta de Qlic usted acepta estos Términos y Condiciones...",
  "updatedOn": "2026-10-06"
}
```

**Commits relacionados con la documentación de servicios**

| Repositorio | Branch | Commit ID | Mensaje del commit | Fecha |
|---|---|---|---|---|
| qlic-backend-api | `feature/alerting-management` | `32ed811` | feat(alerting): implement US17, US18, US19, and US20 with JUnit 5 unit tests | 2026-11-03 |
| qlic-backend-api | `feature/subscriptions-context` | `0aede0a` | feat(subscriptions): implement US31, US32, US33, and US34 with JUnit 5 test suite | 2026-11-03 |
| qlic-backend-api | `feature/iam-account-management` | `a1a5bdb` | feat(shared): add HTTP-mapped domain exception categories and JWT claim helpers | 2026-11-10 |
| qlic-backend-api | `feature/iam-account-management` | `831aa72` | feat(iam): add domain model for password reset, invitations and authorized users (US07, US08, US09) | 2026-11-10 |
| qlic-backend-api | `feature/iam-account-management` | `1a25142` | feat(iam): implement password reset, invitation, shared sign-in and profile handlers | 2026-11-10 |
| qlic-backend-api | `feature/iam-account-management` | `ac0365e` | feat(iam): persist access management, plan entitlement ACL and VIEWER write restriction | 2026-11-10 |
| qlic-backend-api | `feature/iam-account-management` | `02ff499` | feat(iam): expose password reset, shared access and profile endpoints with i18n messages | 2026-11-10 |
| qlic-backend-api | `feature/iam-account-management` | `ab4d5ff` | test(iam): add unit and integration tests for US07, US08 and US09 | 2026-11-10 |
| qlic-backend-api | `feature/support-incidents` | `dd280a7` | feat(support): add incident, technical visit and terms of service domain model (US35-US38) | 2026-11-10 |
| qlic-backend-api | `feature/support-incidents` | `045cf4f` | feat(support): implement incident registration, visit request, technician assignment and queries | 2026-11-10 |
| qlic-backend-api | `feature/support-incidents` | `39d2409` | feat(support): persist incidents, add ACL adapters to alerting, monitoring and subscriptions and seed reference data | 2026-11-10 |
| qlic-backend-api | `feature/support-incidents` | `1784567` | feat(support): expose incidents, support staff and terms of service endpoints with i18n messages | 2026-11-10 |
| qlic-backend-api | `feature/support-incidents` | `491fe8a` | test(support): add unit and integration tests for US35, US36, US37 and US38 | 2026-11-10 |
| qlic-backend-api | `feature/consumption-off-hours` | `8cca8da` | feat(monitoring): add consumption reading ingestion per Water Point | 2026-11-10 |
| qlic-backend-api | `feature/consumption-off-hours` | `901d92e` | feat(consumption): implement activity schedule and off-hours consumption report (US24) | 2026-11-10 |
| qlic-backend-api | `feature/consumption-off-hours` | `b8d142f` | test(consumption): add aggregation and integration tests for US24 | 2026-11-10 |
| qlic-backend-api | `feature/render-postgresql` | `ea93052` | chore(deploy): add Render Blueprint with managed PostgreSQL and document Sprint 2 endpoints | 2026-11-10 |


### 4.3. Validation Interviews

En esta sección se registran las sesiones de validación realizadas con representantes de los segmentos objetivo, quienes interactúan con el Landing Page y con la aplicación móvil de Qlic para cumplir los User Goals definidos en el capítulo 3. El propósito es comprobar, con evidencia de uso real, si el producto permite completar las tareas principales sin ayuda y detectar problemas de usabilidad, arquitectura de información y diseño inclusivo antes de la entrega final.

#### 4.3.1. Diseño de Entrevistas

**Objetivo de las sesiones.** Verificar que usuarios de los segmentos PYMES y Hogares pueden completar de forma autónoma los flujos F1, F2 y F3 del prototipo y de la aplicación (crear una cuenta e iniciar sesión, atender una alerta de posible fuga y registrar un dispositivo con código QR), y que entienden la propuesta de valor presentada en el Landing Page.

##### Participantes y muestra

| Segmento | Perfil de participación | Sesiones en esta entrega | Sesiones previstas hasta el TB2 | Modalidad |
|---|---|---:|---:|---|
| **PYMES y comercios locales** | Propietario, administrador o responsable de mantenimiento de una PYME que participa en las decisiones sobre el consumo de agua. | 1 | 3 a 5 | Presencial en el negocio o videollamada, con autorización de grabación. |
| **Hogares y familias** | Persona adulta que paga, revisa o decide sobre el recibo y el mantenimiento del agua del hogar. | 1 | 3 a 5 | Presencial o videollamada, con autorización de grabación. |

Los participantes pueden ser personas que ya intervinieron en las entrevistas de Needfinding, lo que permite contrastar sus necesidades declaradas con su comportamiento frente al producto.

##### Elementos incluidos en la sesión

| Producto | Qué se muestra | Dispositivo |
|---|---|---|
| Landing Page | Versión desplegada, en su vista para navegador móvil y de escritorio. | Computadora o celular del participante. |
| Aplicación móvil | APK instalado y conectado al API desplegado, distribuido mediante Firebase App Distribution. | Celular físico (el del participante o el del equipo). |

##### User Flows incluidos en la validación

| Flujo | User Goal | User Stories | Ruta esperada (happy path) |
|---|---|---|---|
| F1 | Acceder a la aplicación para monitorear el consumo | US05, US06 | Sign in → Create account → aceptar términos → Dashboard |
| F2 | Actuar a tiempo ante una fuga | US15, US16, US20 | Notificación push → Alert detail → marcar la alerta como atendida |
| F3 | Registrar un dispositivo nuevo | US10, US11, US12 | Add device (código QR) → Assign Water Point → Devices |

##### Tareas de la sesión

Las consignas se redactan sin nombrar botones ni pantallas, para observar si el participante encuentra el camino por sí mismo. El escenario se adapta a cada segmento: en PYMES, "administras una lavandería y quieres controlar el agua de tu local"; en Hogares, "eres quien paga el recibo de agua de tu casa".

| Id | Producto | Flujo | Consigna al participante | Criterio de éxito |
|---|---|---|---|---|
| T1 | Landing Page | — (US01, US02) | "Entra a esta página y cuéntame con tus palabras qué hace Qlic y cuál plan elegirías." | Explica correctamente el propósito del servicio e identifica un plan. |
| T2 | Aplicación | F1 | "Crea una cuenta para usar Qlic y entra a la aplicación." | Completa el registro, acepta los términos y llega al Dashboard sin ayuda. |
| T3 | Aplicación | F3 | "Acaban de instalar un sensor nuevo. Regístralo en tu cuenta e indica en qué punto de agua está." | El dispositivo queda vinculado y asignado a un Water Point en menos de 10 minutos y sin ayuda. |
| T4 | Aplicación | F2 | "Te llega esta notificación. Cuéntame qué está pasando y qué harías." | Identifica dónde ocurre el problema, qué tan grave es y la acción recomendada, y marca la alerta como atendida. |

La tarea T3 contrasta directamente la Hipótesis 3 (más del 85 % de los usuarios vincula su dispositivo en menos de 10 minutos sin asistencia técnica). La tarea T4 evalúa la comprensión de la alerta que pidieron los entrevistados en el Needfinding; la hipótesis sobre su atención en 24 horas solo puede comprobarse con uso prolongado y no en una sesión.

##### Qué se mide

| Medida | Cómo se registra |
|---|---|
| Resultado de cada tarea | Completó sin ayuda · Completó con ayuda · No completó. |
| Tiempo por tarea | Cronometrado por el anotador desde que termina la consigna. |
| Errores y dudas | Anotados por el anotador con el minuto del video. |
| Facilidad percibida | Pregunta final de cada tarea: "Del 1 (muy difícil) al 7 (muy fácil), ¿qué tan fácil fue?" |
| Problemas de usabilidad | Se puntúan con la escala de severidad de 1 a 4 del formato de evaluación según heurísticas (4.3.3). |

Los problemas se clasifican según tres grupos de criterios: heurísticas de usabilidad (visibilidad del estado del sistema, consistencia, prevención de errores, control del usuario, ayuda para reconocer errores), arquitectura de información (si el contenido es fácil de encontrar y de usar) y diseño inclusivo (experiencias comparables, texto alternativo, contraste y tamaño de los elementos táctiles).

##### Guion de la sesión (15 a 20 minutos)

1. **Bienvenida y consentimiento (1 min).** Se explica que se prueba el producto y no a la persona, y se pide autorización para grabar.
2. **Contexto (2 min).** "¿Cómo controlas hoy el consumo de agua en tu negocio u hogar?" y "¿Qué usas habitualmente en tu celular?"
3. **Tareas T1 a T4 (10 a 12 min).** La persona piensa en voz alta. El moderador no explica la interfaz; solo interviene si el participante lleva más de dos minutos bloqueado.
4. **Preguntas finales (3 min).**
  - ¿Qué fue lo más difícil o confuso?
  - ¿Qué cambiarías o agregarías?
  - ¿Qué tan clara te resultó la alerta?
  - ¿Usarías Qlic en tu negocio u hogar? ¿Qué te haría dudar?
5. **Cierre (1 min).** Se agradece y se confirma el uso del video.

##### Preparación previa

- El API desplegado debe estar activo y respondiendo antes de empezar.
- El APK debe estar instalado en el celular de la sesión.
- Debe haber un código QR de sensor disponible, impreso o en pantalla, para T3.
- La alerta de fuga de T4 debe haberse generado antes en la cuenta del participante.
- La sesión se graba en video (pantalla del celular y rostro del participante), con un moderador y un anotador.
- Cada video se edita a 3 a 5 minutos por entrevista, con título que indique el nombre del participante, el segmento y la fecha, y se consolida en el archivo `upc-pre-202620-1acc0238-13984-qlic-validation-av2.mp4`.

#### 4.3.2. Registro de Entrevistas

> *Se completa después de realizar las sesiones. Una ficha por entrevista.*

| Campo | Registro |
|---|---|
| Nombre y apellidos | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Distrito | **[COMPLETAR]** |
| Segmento | **[PYMES / Hogares]** |
| Fecha | **[AAAA-MM-DD]** |
| Inicio y duración en el video | **[hh:mm:ss]** · **[mm:ss]** |
| Enlace del video (OneDrive) | **[PEGAR URL]** |
| Captura del video | **[INSERTAR imagen]** |
| Resumen | Principales apreciaciones del participante sobre cada tarea (T1 a T4): qué logró, dónde dudó, qué comentó y qué problemas se observaron. |
