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

**Modelo de ramas: GitFlow**

El equipo adopta el modelo GitFlow propuesto por Driessen (2010), que separa el código listo para producción del código en integración mediante dos ramas permanentes y tres tipos de ramas de soporte:

| Rama | Origen | Destino | Uso en Qlic |
|---|---|---|---|
| `master` / `main` | — | — | Contiene únicamente versiones publicadas; cada merge corresponde a un release etiquetado. El Project Report utiliza `master` y los repositorios de código, `main`. |
| `develop` | `master` / `main` | `release/*` | Integra las funcionalidades terminadas del Sprint en curso. |
| `feature/*` | `develop` | `develop` | Una rama por historia o grupo de historias, con nombre en *kebab-case* (por ejemplo, `feature/iam-authentication` o `feature/chapter-4`). |
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
| `chore` | Configuración, dependencias o tareas de mantenimiento | `chore(deploy): add Dockerfile and prod profile` |

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
- Los verbos HTTP y los códigos de estado se utilizan según su semántica estándar (Fielding et al., 2022): `201 Created` al crear un recurso, `400 Bad Request` ante datos inválidos, `401 Unauthorized` ante credenciales ausentes o inválidas y `409 Conflict` ante un recurso duplicado.
- Los errores se devuelven con el formato *Problem Details for HTTP APIs* (`application/problem+json`), definido en el RFC 9457 (Nottingham et al., 2023).
- Las tablas y columnas de la base de datos se nombran en *snake_case* y en plural (`subscribers`, `password_hash`).
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

Pasos de despliegue en Render (Render, s. f.):

1. Crear una base de datos PostgreSQL en Render y anotar su *host*, nombre de base, usuario y contraseña.
2. Crear un *Web Service* conectado al repositorio `qlic-backend-api`, rama `main`, con entorno de ejecución Docker; Render detecta el `Dockerfile` de la raíz.
3. Registrar en el servicio las variables de entorno indicadas en la tabla *Configuración del entorno `prod`*, presentada a continuación.
4. Render construye la imagen, la ejecuta y expone el servicio en `https://qlic-backend-api.onrender.com`; cada merge a `main` dispara un nuevo despliegue automático. El `Dockerfile` inicia la aplicación con el puerto de la variable `PORT` asignada por la plataforma (`-Dserver.port=${PORT:-8080}`).
5. Verificar el despliegue accediendo a `https://qlic-backend-api.onrender.com/swagger-ui.html`.

**Configuración del entorno `prod`**

| Variable | Valor |
|---|---|
| `SPRING_PROFILES_ACTIVE` | `prod` |
| `SPRING_DATASOURCE_URL` | `jdbc:postgresql://<host>:5432/<base>` |
| `SPRING_DATASOURCE_USERNAME` | Usuario de la base de datos |
| `SPRING_DATASOURCE_PASSWORD` | Contraseña de la base de datos |
| `JWT_SECRET` | Clave de firma HS256 de al menos 32 caracteres |
| `JWT_EXPIRATION_MINUTES` | Vigencia del token de acceso; por defecto, 1440 |

Dado que el plan gratuito de Render suspende el servicio tras un periodo de inactividad y limita la vigencia de la base de datos gratuita (Render, s. f.), la primera solicitud después de un periodo sin uso puede demorar algunos segundos; esta restricción es aceptable para la etapa de validación académica del producto.

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

* **US15: Anomaly evaluation**
    * **Descripción:** Ingesta y analiza lecturas de telemetría de flujo hídrico para evaluar anomalías frente a umbrales configurados. Determina la severidad (`CRITICAL`, `MODERATE`, `INFORMATIONAL`), calculando el volumen derramado acumulado y su costo económico estimado en moneda local (PEN).
    * **Endpoint:** `POST /api/v1/alerts/evaluations`
    * **Escenario de Alerta Positiva (Flujo Sostenido):** Retorno de código `201 Created` con la alerta de fuga persistida y la acción de mitigación recomendada.
    * **Escenario de Contorno (Lectura Aislada / Falso Positivo):** Retorno de código `204 No Content`, validando que consumos transitorios no disparen falsas alarmas.
    * **Evidencias de ejecución (Postman):**

![alertings_POST_201.png](../images/postman_evidence/alertings_POST_201.png)

![alertings_POST_204.png](../images/postman_evidence/alertings_POST_204.png)

---

* **US16: Alert retrieval**
    * **Descripción:** Obtiene la relación de alertas preventivas y críticas activas asociadas a una cuenta para su visualización y priorización en el cliente móvil.
    * **Endpoint:** `GET /api/v1/alerts?accountId={accountId}`
    * **Código de respuesta:** `200 OK`
    * **Evidencia de ejecución (Postman):**

![alerts_GET.png](../images/postman_evidence/alerts_GET.png)

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

| Bounded Context | Clase de Prueba | Caso de Prueba / Escenario | Resultado |
| :--- | :--- | :--- | :--- |
| **Alerting** | `AnomalyDetectionServiceTest` | Flujo sostenido sobre el umbral genera alerta `CRITICAL` con cálculo de volumen y costo. | **Passed** |
| **Alerting** | `AnomalyDetectionServiceTest` | Lectura transitoria aislada superior al umbral no genera alerta (`null`). | **Passed** |
| **Alerting** | `AnomalyDetectionServiceTest` | Consumo dentro de límites estándar retorna evaluación limpia sin alertas. | **Passed** |
| **Monitoring** | `DeviceCommandHandlerTest` | Registro de nuevo dispositivo IoT mediante payload QR persiste con estado `ONLINE` y batería en 100%. | **Passed** |
| **Monitoring** | `DeviceCommandHandlerTest` | Asignación de Water Point actualiza la referencia de infraestructura hidráulica en el dispositivo. | **Passed** |

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
| RESTful API | Endpoints de Authentication, device-controller y leak-alert-controller | US05, US06, US10 a US12, US15, US16 | Figuras 4.5 a 4.8 (sección 4.2.1.7) |

![Landing Page desplegado en navegador de escritorio](../images/execution/landing-desktop.png)

*Figura 4.2.* Landing Page de Qlic en navegador de escritorio: sección Hero y planes de suscripción.

![Landing Page desplegado en navegador móvil](../images/execution/landing-mobile.png)

*Figura 4.3.* Landing Page de Qlic en navegador móvil: formulario de contacto y selector de idioma.

**Video de ejecución del Sprint.** El video `upc-pre-202620-1acc0238-13984-wasd-productnavigation-tb1.mp4` muestra y explica la navegación lograda en el Sprint 1: el recorrido del Landing Page en escritorio y en móvil, el cambio de idioma y el envío del formulario de contacto, y la ejecución de los endpoints del RESTful API desde Swagger UI con un token de acceso. Está publicado en [COMPLETAR: enlace del video en Microsoft Stream u OneDrive].

![Captura del video de ejecución del Sprint 1](../images/execution/product-navigation-video.png)

*Figura 4.4.* Captura del video de ejecución del Sprint 1.

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

**Evidencia de interacción con la documentación**

La Figura 4.5 muestra la vista general de Swagger UI con las secciones Authentication, device-controller y leak-alert-controller, y el esquema de seguridad `bearerAuth`.

<img src="../images/services/swagger_overview.png" alt="Vista general de Swagger UI del RESTful API de Qlic" width="800">

*Figura 4.5.* Documentación OpenAPI del RESTful API de Qlic publicada con Swagger UI.

La Figura 4.6 muestra la ejecución del endpoint de registro con los datos de muestra y su respuesta `201 Created`.

<img src="../images/services/swagger_sign_up.png" alt="Ejecución de POST sign-up en Swagger UI" width="800">

*Figura 4.6.* Ejecución de `POST /api/v1/authentication/sign-up` (US05).

La Figura 4.7 muestra la ejecución del inicio de sesión y el token de acceso emitido.

<img src="../images/services/swagger_sign_in.png" alt="Ejecución de POST sign-in en Swagger UI" width="800">

*Figura 4.7.* Ejecución de `POST /api/v1/authentication/sign-in` (US06).

La Figura 4.8 muestra la consulta de un recurso protegido luego de registrar el token en el diálogo *Authorize*.

<img src="../images/services/swagger_authorized_request.png" alt="Consulta de recurso protegido con token en Swagger UI" width="800">

*Figura 4.8.* Ejecución de `GET /api/v1/devices` con el token de acceso (US12).

**Commits relacionados con la documentación de servicios**

| Repositorio | Branch | Commit ID | Mensaje del commit | Fecha |
|---|---|---|---|---|
| qlic-backend-api | `main` | `7e2eca3` | feat(alerting): implement US15 and US16 for leak detection evaluation and account alert retrieval | 2026-10-01 |
| qlic-backend-api | `main` | `e7d8b17` | feat(monitoring): implement US10, US11, and US12 for QR device onboarding, water point linking, and telemetry status | 2026-10-01 |
| qlic-backend-api | `main` | `c224c3f` | feat(docker): add multi-stage Dockerfile for cloud deployment | 2026-10-02 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | feat(iam): add domain layer for subscriber accounts (US05, US06) | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | feat(iam): implement sign-up and sign-in command handlers | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | feat(iam): expose authentication endpoints with JWT security (TS01) | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | feat(i18n): add en_US and es_419 message bundles for IAM responses | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | docs(api): configure OpenAPI 3 and Swagger UI with bearer authentication | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | test(iam): add unit and integration tests for registration and authentication | 2026-10-05 |
| qlic-backend-api | `feature/iam-authentication` | [COMPLETAR] | chore(config): add dev and prod profiles and project README | 2026-10-05 |

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
