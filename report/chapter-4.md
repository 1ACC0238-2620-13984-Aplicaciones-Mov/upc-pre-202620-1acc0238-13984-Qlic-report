# Capítulo IV: Product Implementation & Validation

## 4.1. Software Configuration Management

### 4.1.1. Software Development Environment Configuration

### 4.1.2. Source Code Management

### 4.1.3. Source Code Style Guide & Conventions

### 4.1.4. Software Deployment Configuration

## 4.2. Landing Page & Mobile Application Implementation

### 4.2.1. Sprint 1

#### 4.2.1.1. Sprint Planning 1

La planificación del Sprint 1 se organiza alrededor de las historias US01–US04 del Product Backlog. El objetivo es construir y revisar la primera versión del Landing Page para que una persona visitante pueda comprender la propuesta de Qlic, comparar los planes, comunicarse con el equipo y cambiar el idioma de la interfaz.

| Campo de planificación | Registro del Sprint 1 |
|---|---|
| Sprint | Sprint 1 |
| Date | No consignada en el repositorio revisado |
| Time | No consignada en el repositorio revisado |
| Location / modalidad | No consignada en el repositorio revisado |
| Prepared by | No consignado en el repositorio revisado |
| Attendees | Avila Palacios, Aaron Alexander; Briceño Llanos, Ayrton Omar; Conde Huashuayo, Sebasthian Alex; Condori Lozano, Alessandro Ramiro |
| Sprint 0 Review Summary | No aplica: no se registró un Sprint anterior en esta rama |
| Sprint 0 Retrospective Summary | No registrada en el repositorio revisado |
| Sprint Goal | Entregar una primera versión navegable del Landing Page que cubra US01, US02, US03 y US04 |
| Sprint Velocity | No registrada; debe calcularse con las historias terminadas y aceptadas |
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

La matriz siguiente distribuye el liderazgo y la colaboración entre los cuatro integrantes. `L` significa líder del aspecto y `C` significa colaborador. La asignación se relaciona con las tareas del Sprint Backlog 1 y evita concentrar toda la responsabilidad en una sola persona.

| Team Member (Last Name, First Name) | GitHub Username | Sprint Planning 1 | Landing Page implementation | Sprint Backlog 1 | Software Deployment Evidence | Team Collaboration Insights |
|---|---|:---:|:---:|:---:|:---:|:---:|
| Avila Palacios, Aaron Alexander | No consignado en el reporte | **L** | C | C | **L** | C |
| Briceño Llanos, Ayrton Omar | No consignado en el reporte | C | **L** | C | C | C |
| Conde Huashuayo, Sebasthian Alex | No consignado en el reporte | C | C | **L** | C | C |
| Condori Lozano, Alessandro Ramiro | No consignado en el reporte | C | C | C | C | **L** |

Los nombres de usuario de GitHub deben consignarse con el identificador público real de cada integrante antes de la entrega. No se inventan identificadores a partir del nombre mostrado en los commits. La evidencia de cada liderazgo debe vincularse con la tarea correspondiente, su estado y el commit o captura de la revisión.

#### 4.2.1.3. Sprint Backlog 1

El Sprint Backlog 1 descompone US01–US04 en tareas estimadas entre cuatro y ocho horas. El Product Backlog registrado para Qlic está disponible en el [tablero de Trello](https://trello.com/invite/b/6aa1e6966e4df21cb3a4eef9/ATTIe6a46d0c84f618e9bccb9c4de3ce13f711448192/product-backlog-qlic). Las estimaciones son de planificación; el estado debe actualizarse con la evidencia de ejecución del Sprint.

| Sprint # | User Story Id | User Story Title | Task Id | Task Title | Task Description | Estimation (Hours) | Assigned To | Status |
|---:|---|---|---|---|---|---:|---|---|
| 1 | US01 | Conocer la propuesta de valor de Qlic | T01 | Hero de propuesta de valor | Construir la sección Hero con el problema, la propuesta de valor y el llamado a la acción | 6 | Condori Lozano, Alessandro Ramiro | To-do |
| 1 | US02 | Comparar los planes de suscripción disponibles | T02 | Comparador de planes | Implementar la comparación de Plan Básico y Plan Gestión Pro con información legible | 6 | Briceño Llanos, Ayrton Omar | To-do |
| 1 | US03 | Contactar al equipo desde el Landing Page | T03 | Formulario de contacto | Implementar el formulario y los canales de contacto del equipo | 4 | Conde Huashuayo, Sebasthian Alex | To-do |
| 1 | US04 | Consultar el Landing Page en el idioma de preferencia | T04 | Selector de idioma | Incorporar el selector para español latinoamericano e inglés | 6 | Avila Palacios, Aaron Alexander | To-do |
| 1 | US01–US04 | Historias del Landing Page | T05 | Responsive y accesibilidad | Aplicar diseño responsive, jerarquía visual, etiquetas accesibles y revisión en móvil | 6 | Condori Lozano, Alessandro Ramiro | To-do |
| 1 | US01–US04 | Historias del Landing Page | T06 | SEO y metadatos | Añadir título, descripción, viewport, URL canónica y metadatos sociales; el detalle SEO se documenta en el capítulo correspondiente | 4 | Avila Palacios, Aaron Alexander | To-do |
| 1 | US01–US04 | Historias del Landing Page | T07 | Verificación del despliegue | Preparar la configuración de hosting estático y verificar la URL de producción | 4 | Briceño Llanos, Ayrton Omar | To-do |

La captura del tablero y el enlace público deben incorporarse como evidencia visual de la revisión. En esta rama solo se dispone del enlace registrado; no se declara una captura que no está almacenada en el repositorio.

#### 4.2.1.4. Development Evidence for Sprint Review

#### 4.2.1.5. Testing Suite Evidence for Sprint Review

#### 4.2.1.6. Execution Evidence for Sprint Review

#### 4.2.1.7. Services Documentation Evidence for Sprint Review

#### 4.2.1.8. Software Deployment Evidence for Sprint Review

El Capítulo II define el Landing Page como un container estático que debe servirse mediante HTTPS. En el repositorio revisado no se encuentra una URL pública de producción ni una captura de la configuración del proveedor; por eso no se declara un despliegue realizado.

| Elemento de despliegue | Registro verificable |
|---|---|
| Producto | Landing Page estático |
| Proveedor o cuenta cloud | No registrado en el repositorio revisado |
| URL pública | No registrada en el repositorio revisado |
| Commit publicado | No registrado en el repositorio revisado |
| Evidencia requerida | URL pública, captura de la página desplegada, proveedor, recursos y configuración |

La evidencia final debe corresponder al mismo commit revisado en el Sprint Backlog y permitir comprobar que US01, US02, US03 y US04 son accesibles desde la versión desplegada.

#### 4.2.1.9. Team Collaboration Insights during Sprint

El equipo declara el uso de GitHub, GitFlow, Trello y WhatsApp para organizar el trabajo. La distribución del Sprint 1 asigna un liderazgo diferente a cada integrante: Aaron en planificación y despliegue, Ayrton en implementación, Sebasthian en backlog y Alessandro en colaboración. La interpretación definitiva debe basarse en capturas de GitHub Insights y del tablero correspondientes al intervalo real del Sprint.

| Integrante | Responsabilidad de colaboración en el Sprint 1 | Evidencia que debe vincularse |
|---|---|---|
| Avila Palacios, Aaron Alexander | Coordinar la planificación, revisar el despliegue y consolidar la evidencia | Acta de planificación, URL/captura de despliegue y commits |
| Briceño Llanos, Ayrton Omar | Coordinar la implementación de la comparación de planes y apoyar la revisión | Commit de T02/T07 y captura de revisión |
| Conde Huashuayo, Sebasthian Alex | Mantener el backlog, las estimaciones y el estado de las tareas | Captura del tablero y actualización de T03 |
| Condori Lozano, Alessandro Ramiro | Consolidar la colaboración del equipo y apoyar la interfaz | Capturas de coordinación y commits de T01/T05 |

Para la entrega se requiere una captura de GitHub Insights con el periodo del Sprint, una captura del tablero de Trello y un registro de los acuerdos o bloqueos. La imagen general de actividad de AV1 no está disponible en esta rama; no se sustituye por una captura de otro periodo.

## 4.3. Validation Interviews

### 4.3.1. Diseño de Entrevistas

### 4.3.2. Registro de Entrevistas

### 4.3.3. Evaluaciones según heurísticas
