# Capítulo IV: Product Implementation & Validation

Este capítulo organiza la implementación y la validación del alcance inicial de Qlic. Para el Sprint 1 se toma como referencia el Product Backlog documentado en el Capítulo II: US01, US02, US03 y US04, correspondientes al Landing Page informativo. Las afirmaciones de implementación se separan de las decisiones planificadas y de la evidencia que todavía debe adjuntarse.

## 4.1. Software Configuration Management

El trabajo se gestiona con Git y GitHub siguiendo un flujo de ramas por entregable y mensajes de commit basados en Conventional Commits. La rama `feature/chapter-4` concentra este capítulo y permanece separada de `master` mientras el equipo revisa su contenido.

### 4.1.1. Software Development Environment Configuration

El alcance del Sprint 1 se limita al Landing Page estático asociado al epic EP01. La solución descrita en el Capítulo II identifica HTML5, CSS3 y JavaScript como tecnologías del sitio web. La configuración del entorno debe permitir editar Markdown y los archivos estáticos, revisar el resultado en un navegador y registrar los cambios en Git.

| Elemento | Uso en el Sprint 1 | Evidencia disponible |
|---|---|---|
| Git y GitHub | Control de versiones, ramas y revisión de cambios | Repositorio del Project Report |
| Markdown | Documentación del sprint y trazabilidad de requisitos | Este capítulo y el README del proyecto |
| HTML5, CSS3 y JavaScript | Implementación del Landing Page | Tecnología definida para el container Landing Page en el Capítulo II |
| Navegador web | Revisión visual y funcional del sitio | Revisión local o URL pública que debe adjuntarse |
| Trello | Organización del Product Backlog y tareas | Enlace al tablero registrado en el Capítulo II |

### 4.1.2. Source Code Management

El repositorio remoto del proyecto es `1ACC0238-2620-13984-Aplicaciones-Mov/upc-pre-202620-1acc0238-13984-Qlic-report`. Se utiliza una rama específica para este capítulo, `feature/chapter-4`, y la integración a `master` se realizará después de la revisión del equipo. La documentación conserva los identificadores de las historias y evita duplicar requisitos ya definidos en el Capítulo II.

### 4.1.3. Source Code Style Guide & Conventions

La documentación utiliza títulos numerados, tablas para requisitos y evidencias, nombres de historias con el formato `USnn` y mensajes de commit con Conventional Commits. Las tareas del sprint se expresan con un verbo de acción, una estimación en horas y un responsable. Las afirmaciones sobre despliegue, ejecución o pruebas solo se incorporan cuando existe una captura, URL, commit o registro verificable.

### 4.1.4. Software Deployment Configuration

El modelo de arquitectura del Capítulo II describe el Landing Page como un sitio estático servido mediante HTTPS desde un proveedor de hosting. Esta sección documenta la configuración esperada; la URL pública, el proveedor utilizado y la captura de producción deben registrarse en la evidencia de despliegue del Sprint 1.

## 4.2. Landing Page & Mobile Application Implementation

El Sprint 1 prioriza la validación de la propuesta de valor antes de construir funcionalidades autenticadas de las aplicaciones móviles. El alcance funcional se deriva de US01 a US04: conocer Qlic, comparar planes, contactar al equipo y consultar el contenido en el idioma preferido.

### 4.2.1. Sprint 1

#### 4.2.1.1. Sprint Planning 1

**Objetivo del Sprint.** Construir y revisar la primera versión del Landing Page para que una persona visitante pueda comprender la propuesta de Qlic, comparar los planes, comunicarse con el equipo y cambiar el idioma de la interfaz.

**Criterio de validación.** El Sprint se considera encaminado cuando una persona puede recorrer la página, identificar el beneficio principal, consultar las diferencias entre planes, enviar una consulta y seleccionar español latinoamericano o inglés sin depender de una explicación del equipo.

| User Story | Resultado esperado | Story Points |
|---|---|---:|
| US01 | Presentar la propuesta de valor, el problema y los beneficios principales de Qlic | 3 |
| US02 | Mostrar una comparación comprensible de los planes disponibles | 2 |
| US03 | Permitir el contacto del visitante con el equipo | 2 |
| US04 | Permitir consultar la página en inglés o español latinoamericano | 2 |
| **Total** |  | **9** |

#### 4.2.1.2. Aspect Leaders and Collaborators

La asignación confirmada para este bloque identifica a Avila Palacios, Aaron Alexander como líder de los aspectos de planificación del Sprint 1, descomposición del backlog, SEO y metadatos, despliegue y registro de colaboración. La matriz no asigna líderes adicionales sin una confirmación explícita del equipo.

| Team Member (Last Name, First Name) | GitHub Username | Aspect | Role |
|---|---|---|---|
| Avila Palacios, Aaron Alexander | No registrado en el reporte | Sprint Planning 1; Sprint Backlog 1; SEO Tags and Meta Tags; Software Deployment Evidence; Team Collaboration Insights | Leader (L) |

La asignación de los demás aspectos del Sprint requiere la matriz de líderes y colaboradores acordada por el equipo, de modo que la responsabilidad de cada tarea coincida con la tabla del Sprint Backlog.

#### 4.2.1.3. Sprint Backlog 1

El siguiente backlog descompone US01–US04 en tareas estimadas entre cuatro y ocho horas. Las estimaciones representan la planificación inicial del Sprint y no constituyen evidencia de ejecución hasta que se acompañen con el estado, el commit y la revisión correspondiente.

| Sprint | User Story | Work-item / Task | Description | Estimation (Hours) | Assigned to | Status |
|---|---|---|---|---:|---|---|
| Sprint 1 | US01 | T01 | Construir la sección Hero con el problema, la propuesta de valor y el llamado a la acción | 6 | Aaron | To-do |
| Sprint 1 | US02 | T02 | Implementar la tabla comparativa de Plan Básico y Plan Gestión Pro | 6 | Aaron | To-do |
| Sprint 1 | US03 | T03 | Implementar el formulario y los canales de contacto del equipo | 4 | Aaron | To-do |
| Sprint 1 | US04 | T04 | Incorporar el selector de idioma para español latinoamericano e inglés | 6 | Aaron | To-do |
| Sprint 1 | US01–US04 | T05 | Aplicar diseño responsive, jerarquía visual, etiquetas accesibles y revisión en móvil | 6 | Aaron | To-do |
| Sprint 1 | US01–US04 | T06 | Añadir título, descripción, viewport, URL canónica y metadatos sociales | 4 | Aaron | To-do |
| Sprint 1 | US01–US04 | T07 | Preparar la configuración de hosting estático y verificar la URL de producción | 4 | Aaron | To-do |

#### 4.2.1.8. Software Deployment Evidence for Sprint Review

El Capítulo II define el Landing Page como un container estático que debe servirse mediante HTTPS. En el repositorio revisado no se encuentra todavía una URL pública de producción ni una captura de la configuración del proveedor. Por ello, no se declara un despliegue realizado.

| Producto | Configuración esperada | Evidencia que debe acompañar la revisión | Estado verificable |
|---|---|---|---|
| Landing Page | Hosting estático con acceso HTTPS | URL pública, captura de la página desplegada, proveedor y commit publicado | No registrada en el repositorio revisado |

La evidencia de esta sección debe corresponder al mismo commit revisado en el Sprint Backlog y debe permitir comprobar que US01, US02, US03 y US04 son accesibles desde la versión desplegada.

#### 4.2.1.9. Team Collaboration Insights during Sprint

El equipo declara el uso de GitHub, GitFlow, Trello y WhatsApp para organizar el trabajo. La captura `images/collaboration/av1_git.png` documenta la actividad general del repositorio durante AV1, pero no permite aislar por sí sola la actividad del Sprint 1. Para que la evidencia sea específica del Sprint se necesita una captura de GitHub Insights con el intervalo correspondiente y una interpretación de los commits de cada integrante.

| Evidencia | Qué permite comprobar | Estado |
|---|---|---|
| Historial de GitHub | Ramas, commits y mensajes asociados al trabajo | Disponible a nivel general del repositorio |
| Captura de GitHub Insights | Distribución de commits durante el Sprint 1 | Debe generarse con el periodo del Sprint |
| Tablero de Trello | Estado de las historias y tareas del Sprint Backlog | Enlace registrado; falta la captura específica del Sprint |
| Registro de comunicación | Coordinación, acuerdos y bloqueos | Debe adjuntarse una evidencia de la sesión o canal utilizado |

La interpretación final debe explicar qué se completó, qué bloqueos aparecieron, cómo se distribuyó el trabajo y qué ajustes se realizarán en el siguiente Sprint. No se atribuyen actividades individuales que no estén respaldadas por el historial o por un registro del equipo.
