# Capítulo IV: Product Implementation & Validation

## 4.1. Software Configuration Management

### 4.1.1. Software Development Environment Configuration

### 4.1.2. Source Code Management

### 4.1.3. Source Code Style Guide & Conventions

### 4.1.4. Software Deployment Configuration

## 4.2. Landing Page & Mobile Application Implementation

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
| Avila Palacios, Aaron Alexander | No registrado en el reporte | Sprint Planning 1; Sprint Backlog 1; Software Deployment Evidence; Team Collaboration Insights | Leader (L) |

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

#### 4.2.1.4. Development Evidence for Sprint Review

#### 4.2.1.5. Testing Suite Evidence for Sprint Review

#### 4.2.1.6. Execution Evidence for Sprint Review

#### 4.2.1.7. Services Documentation Evidence for Sprint Review

#### 4.2.1.8. Software Deployment Evidence for Sprint Review

El Capítulo II define el Landing Page como un container estático que debe servirse mediante HTTPS. En el repositorio revisado no se encuentra todavía una URL pública de producción ni una captura de la configuración del proveedor. Por ello, no se declara un despliegue realizado.

| Producto | Configuración esperada | Evidencia que debe acompañar la revisión | Estado verificable |
|---|---|---|---|
| Landing Page | Hosting estático con acceso HTTPS | URL pública, captura de la página desplegada, proveedor y commit publicado | No registrada en el repositorio revisado |

La evidencia debe corresponder al mismo commit revisado en el Sprint Backlog y debe permitir comprobar que US01, US02, US03 y US04 son accesibles desde la versión desplegada.

#### 4.2.1.9. Team Collaboration Insights during Sprint

El equipo declara el uso de GitHub, GitFlow, Trello y WhatsApp para organizar el trabajo. La captura `images/collaboration/av1_git.png` documenta la actividad general del repositorio durante AV1, pero no permite aislar por sí sola la actividad del Sprint 1. Para que la evidencia sea específica del Sprint se necesita una captura de GitHub Insights con el intervalo correspondiente y una interpretación de los commits de cada integrante.

| Evidencia | Qué permite comprobar | Estado |
|---|---|---|
| Historial de GitHub | Ramas, commits y mensajes asociados al trabajo | Disponible a nivel general del repositorio |
| Captura de GitHub Insights | Distribución de commits durante el Sprint 1 | Debe generarse con el periodo del Sprint |
| Tablero de Trello | Estado de las historias y tareas del Sprint Backlog | Enlace registrado; falta la captura específica del Sprint |
| Registro de comunicación | Coordinación, acuerdos y bloqueos | Debe adjuntarse una evidencia de la sesión o canal utilizado |

La interpretación final debe explicar qué se completó, qué bloqueos aparecieron, cómo se distribuyó el trabajo y qué ajustes se realizarán en el siguiente Sprint. No se atribuyen actividades individuales que no estén respaldadas por el historial o por un registro del equipo.

## 4.3. Validation Interviews

### 4.3.1. Diseño de Entrevistas

### 4.3.2. Registro de Entrevistas

### 4.3.3. Evaluaciones según heurísticas
