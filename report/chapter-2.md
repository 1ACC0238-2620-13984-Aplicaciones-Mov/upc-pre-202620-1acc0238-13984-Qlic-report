# Capítulo II: Requirements Development and Software Solution Design

## 2.1. Competidores

Qlic se ubica en el mercado de soluciones digitales para la gestión inteligente del agua. El análisis considera como competidores directos a Badger Meter e Itron, que ofrecen medición y analítica hídrica, y como competidor adyacente a OptiRTC, especializado en control de aguas pluviales. Wint se utiliza únicamente como referencia secundaria para la detección de fugas comerciales. La comparación permite identificar oportunidades de diferenciación para una solución móvil dirigida a PYMES y hogares (Badger Meter, s. f.; Itron, s. f.; Opti, s. f.; Wint, s. f.).

### 2.1.1. Análisis competitivo

La información de los perfiles, productos, canales y capacidades se obtuvo de la documentación pública de cada competidor. La tabla resume esos hallazgos y los contrasta con la propuesta preliminar de Qlic (Badger Meter, s. f.; Itron, s. f.; Opti, s. f.; Wint, s. f.).

#### Competitive Analysis Landscape

<table>
  <tr>
    <th colspan="22">Competitive Analysis Landscape</th>
  </tr>
  <tr>
    <td colspan="1">¿Por qué llevar a cabo el análisis?</td>
    <td colspan="17">¿Qué capacidades y enfoques debe adoptar o evitar Qlic para diferenciarse en PYMES y hogares?</td>
  </tr>
  <tr>
    <td colspan="2"></td>
    <td><img src="../images/competitors/badger-meter.jpg" alt="Badger Meter" width="120"><br><strong>Badger Meter</strong></td>
    <td><img src="../images/competitors/optirtc.jpg" alt="OptiRTC" width="120"><br><strong>OptiRTC</strong></td>
    <td><img src="../images/competitors/itron.jpg" alt="Itron" width="120"><br><strong>Itron</strong></td>
    <td><img src="../images/competitors/qlic.jpg" alt="Qlic" width="120"><br><strong>Qlic</strong></td>
  </tr>
  <tr>
    <td rowspan="2">Perfil</td>
    <td>Overview</td>
    <td>Suite de medición, conectividad, software y soporte para gestionar agua en utilities y clientes comerciales.</td>
    <td>Soluciones de control adaptativo de aguas pluviales con IoT, sensores y pronósticos.</td>
    <td>Infraestructura inteligente que integra dispositivos, redes, datos y analítica para utilities y ciudades.</td>
    <td>Propuesta móvil para que PYMES y hogares interpreten consumo, alertas y oportunidades de ahorro.</td>
  </tr>
  <tr>
    <td>Ventaja competitiva<br>¿Qué valor ofrece a los clientes?</td>
    <td>Medición inteligente y análisis que ayudan a optimizar consumo y costos operativos.</td>
    <td>Control predictivo para prevenir inundaciones, reducir riesgos y reutilizar agua.</td>
    <td>Escala, conectividad e integración de servicios urbanos con enfoque de eficiencia y resiliencia.</td>
    <td>Lenguaje claro, experiencia móvil en español, accesibilidad y acompañamiento local por validar.</td>
  </tr>
  <tr>
    <td rowspan="2">Perfil de Marketing</td>
    <td>Mercado Objetivo</td>
    <td>Utilities, municipios y clientes comerciales e industriales.</td>
    <td>Ciudades, gobiernos locales y organizaciones que gestionan aguas pluviales.</td>
    <td>Utilities de agua, ciudades y operadores de infraestructura.</td>
    <td>PYMES con consumo operativo y hogares responsables del recibo y mantenimiento.</td>
  </tr>
  <tr>
    <td>Estrategias de Marketing</td>
    <td>Venta consultiva, demostraciones técnicas, casos de uso y cotización.</td>
    <td>Casos de proyectos, educación sobre resiliencia y conferencias ambientales.</td>
    <td>Comunicación de innovación, sostenibilidad, alianzas y eventos de smart cities.</td>
    <td>Canales digitales locales, mensajes de ahorro, continuidad operativa y sostenibilidad.</td>
  </tr>
  <tr>
    <td rowspan="3">Perfil de Producto</td>
    <td>Productos y Servicios</td>
    <td>Medidores, sensores, válvulas, conectividad y analítica BlueEdge.</td>
    <td>Monitoreo continuo, CMAC, gateways, dashboard, API y control de infraestructura.</td>
    <td>Medición inteligente, comunicación, gestión de datos y detección de fugas.</td>
    <td>Aplicación móvil futura, alertas, historial, recomendaciones y acompañamiento.</td>
  </tr>
  <tr>
    <td>Precios y Costos</td>
    <td>Costos de hardware, implementación, mantenimiento y servicio.</td>
    <td>Costos asociados al sistema, integración y operación del proyecto.</td>
    <td>Contratos de despliegue, infraestructura y soporte a escala empresarial.</td>
    <td>Modelo y precio por validar con usuarios y costos de operación.</td>
  </tr>
  <tr>
    <td>Canales de distribución (Web y/o Móvil)</td>
    <td>Venta consultiva, implementación y plataformas web o de campo.</td>
    <td>Portal web, APIs, proyectos de infraestructura y servicios de implementación.</td>
    <td>Partners, plataformas de gestión e infraestructura conectada.</td>
    <td>Aplicación móvil, aliados de instalación y canales digitales.</td>
  </tr>
  <tr>
    <td rowspan="4">Análisis SWOT</td>
    <td>Fortalezas</td>
    <td>Trayectoria, suite integrada y soporte especializado.</td>
    <td>Especialización en control adaptativo y resiliencia pluvial.</td>
    <td>Escala global, infraestructura y portafolio diversificado.</td>
    <td>Foco móvil, lenguaje claro y cercanía con usuarios locales.</td>
  </tr>
  <tr>
    <td>Debilidades</td>
    <td>Complejidad y costo de adopción para hogares y microempresas.</td>
    <td>Mercado especializado y distinto al monitoreo residencial de fugas.</td>
    <td>Integración compleja y enfoque de infraestructura.</td>
    <td>Propuesta, sensores, conectividad e instalación aún por validar.</td>
  </tr>
  <tr>
    <td>Oportunidades</td>
    <td>Paquetes pequeños y partners locales.</td>
    <td>Mayor inversión en infraestructura resiliente.</td>
    <td>Digitalización de utilities y smart cities.</td>
    <td>Alianzas locales, planes para PYMES y educación de ahorro.</td>
  </tr>
  <tr>
    <td>Amenazas</td>
    <td>Startups de menor costo y proveedores locales.</td>
    <td>Regulación cambiante y soluciones especializadas.</td>
    <td>Alternativas simples y competidores especializados.</td>
    <td>Suites globales, resistencia al hardware y sensibilidad al precio.</td>
  </tr>
</table>

### 2.1.2. Estrategias y tácticas frente a competidores

Las siguientes estrategias convierten la comparación en hipótesis accionables para Qlic. Deben validarse mediante el diseño de entrevistas antes de convertirse en requisitos. Se apoyan en la escala, interoperabilidad y automatización observadas en el mercado; la aplicación móvil, el soporte local y los indicadores propuestos siguen siendo decisiones de diseño por comprobar (Badger Meter, s. f.; Itron, s. f.; Opti, s. f.; Wint, s. f.).

| Estrategia | Tácticas iniciales | Competidor / hallazgo atendido | Indicador a validar |
|---|---|---|---|
| **Diferenciación móvil y local** | Diseñar alertas en español claro, niveles de urgencia y acciones concretas para cada segmento. | Las soluciones de mayor escala priorizan infraestructura; Qlic debe acercar el dato al usuario cotidiano. | El participante entiende una alerta y puede explicar qué acción tomaría. |
| **Escala progresiva para PYMES** | Proponer onboarding por etapas, sensor inicial y reportes que no requieran una plataforma empresarial completa. | Badger Meter e Itron ofrecen suites amplias; la barrera de complejidad debe comprobarse. | Tiempo aceptable de configuración, roles que usarían la solución y funciones mínimas. |
| **Interoperabilidad antes que encierro tecnológico** | Preguntar por medidores existentes, conectividad, APIs y necesidad de exportar datos. | Itron y Opti muestran valor en redes, integraciones y APIs. | Dispositivos actuales, restricciones de integración y formato de datos preferido. |
| **Respuesta ante fugas y anomalías** | Diseñar un flujo de alerta, confirmación, escalamiento y contacto de soporte; no prometer corte automático antes de validar riesgos. | Wint y las suites de medición convierten detección en acción. | Tipo de incidente, tiempo de respuesta y confianza para seguir una recomendación. |
| **Soporte y confianza local** | Validar instalación guiada, acompañamiento remoto, privacidad, continuidad sin conexión y derivación a técnicos. | La escala de los competidores no garantiza soporte cercano para PYMES y hogares locales. | Condiciones para autorizar sensores, canal de soporte y señales de confianza. |
| **Sostenibilidad con evidencia** | Mostrar ahorro, consumo y tendencias solo cuando el usuario pueda interpretarlos y relacionarlos con una decisión. | Los competidores comunican eficiencia y conservación; Qlic debe probar qué métrica es útil. | Métricas consultadas, frecuencia de revisión y decisión que cambia gracias al dato. |

## 2.2. Entrevistas

La investigación utilizará entrevistas semiestructuradas para conocer cómo los representantes de PYMES y hogares gestionan actualmente el agua. Las preguntas se formularán de manera abierta y neutral, solicitando ejemplos de experiencias reales antes de presentar cualquier propuesta. La información permitirá describir características demográficas, personalidad, habilidades, influencias, tecnología, canales de interacción, objetivos, frustraciones y antecedentes necesarios para construir los arquetipos de ambos segmentos.

### 2.2.1. Diseño de entrevistas

#### Participantes y muestra

| Segmento | Perfil de inclusión | Cantidad requerida | Exclusión | Modalidad sugerida |
|---|---|---:|---|---|
| **PYMES y comercios locales** | Propietario, administrador o responsable de operaciones/mantenimiento de una PYME que participa en decisiones sobre consumo o incidencias de agua. | 3 a 5 entrevistas | Personas que no conocen el consumo, mantenimiento ni decisiones asociadas al agua del negocio. | Presencial en el negocio o videollamada, con autorización de grabación. |
| **Hogares y familias** | Persona adulta que paga, revisa o participa en decisiones sobre el recibo, el mantenimiento o el uso de agua del hogar. | 3 a 5 entrevistas | Personas que no tienen experiencia ni responsabilidad sobre el consumo o mantenimiento del hogar. | Presencial o videollamada, con autorización de grabación. |

#### Segmento 1: PYMES y comercios locales

**Preguntas**

1. ¿Cómo controlan actualmente el consumo de agua en su negocio y quién se encarga de revisar esa información?
2. ¿Qué problemas han tenido relacionados con desperdicios, fugas, medidores o cobros inesperados?
3. ¿Con qué frecuencia revisan los medidores, recibos o registros de consumo y cómo guardan esa información?
4. ¿De qué manera el consumo de agua afecta sus costos operativos, la continuidad del negocio o las decisiones de mantenimiento?
5. ¿Qué tan útil sería consultar desde el celular reportes semanales o mensuales sobre el consumo? ¿Qué datos debería mostrar el reporte?
6. ¿Qué opinan de recibir alertas móviles en tiempo real sobre fugas o consumos inusuales? ¿Qué debería incluir una alerta para ayudarles a actuar?
7. ¿Qué características esperan de una aplicación móvil para gestionar el agua y qué tan fácil debería ser usarla desde sus dispositivos actuales?
8. ¿Qué condiciones de precio, suscripción, instalación y soporte considerarían razonables si la aplicación ayudara a reducir costos y mejorar la gestión del agua?

#### Segmento 2: Hogares y familias

**Preguntas**

1. ¿Cómo controlan actualmente el consumo de agua en su hogar y quién revisa o paga el recibo?
2. ¿Han tenido problemas con medidores defectuosos, fugas o cobros inesperados en sus recibos de agua?
3. ¿Cómo suelen identificar una fuga en casa y qué hacen después de detectarla?
4. ¿Qué medidas aplican en el día a día para ahorrar agua y cómo evalúan si están funcionando?
5. ¿Qué tan útil sería recibir en el celular alertas sobre consumos excesivos o fugas? ¿Qué información debería mostrar una alerta?
6. ¿Preferirían un plan móvil básico con funciones esenciales o uno avanzado con reportes detallados? ¿Qué tendría que incluir cada opción?
7. ¿Qué importancia tiene el ahorro de agua en la economía familiar y qué decisiones cambiarían con información más clara del consumo?
8. ¿Qué esperan de una aplicación móvil para gestionar el consumo del hogar y qué condiciones de privacidad, soporte y costo les generarían confianza?

### 2.2.2. Registro de entrevistas

Aquí registraremos las entrevistas de PYMES y hogares. Cada ficha debe incluir los datos del entrevistado, el inicio y fin dentro del video, el enlace, una captura y un resumen de sus respuestas. Si se realizan cuatro o cinco entrevistas, se copia la misma ficha para cada participante.

**Archivo del video consolidado:** `upc-pre-202620-1acc0238-13984-Qlic-needfinding-av1.mp4`<br>
**URL privada de OneDrive:** **[PEGAR URL DEL VIDEO]**

#### Primer segmento - PYMES y comercios locales

##### ENTREVISTA 1

| Campo | Registro |
|---|---|
| **ENTREVISTA 1** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [edad, género, distrito, profesión y contexto del negocio]<br><br>**Características subjetivas:** [personalidad, habilidades, objetivos, frustraciones, marcas e influencias]<br><br>**Tecnología y canales:** [dispositivos, navegador, aplicaciones y canales de interacción]<br><br>**Evidencia:** [minuto o cita breve que sustenta el resumen] |

##### ENTREVISTA 2

| Campo | Registro |
|---|---|
| **ENTREVISTA 2** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [COMPLETAR]<br><br>**Características subjetivas:** [COMPLETAR]<br><br>**Tecnología y canales:** [COMPLETAR]<br><br>**Evidencia:** [minuto o cita breve] |

##### ENTREVISTA 3

| Campo | Registro |
|---|---|
| **ENTREVISTA 3** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [COMPLETAR]<br><br>**Características subjetivas:** [COMPLETAR]<br><br>**Tecnología y canales:** [COMPLETAR]<br><br>**Evidencia:** [minuto o cita breve] |

#### Segundo segmento - Hogares y familias

##### ENTREVISTA 1

| Campo | Registro |
|---|---|
| **ENTREVISTA 1** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [edad, género, distrito, profesión y composición familiar]<br><br>**Características subjetivas:** [personalidad, habilidades, objetivos, frustraciones, marcas e influencias]<br><br>**Tecnología y canales:** [dispositivos, navegador, aplicaciones y canales de interacción]<br><br>**Evidencia:** [minuto o cita breve que sustenta el resumen] |

##### ENTREVISTA 2

| Campo | Registro |
|---|---|
| **ENTREVISTA 2** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [COMPLETAR]<br><br>**Características subjetivas:** [COMPLETAR]<br><br>**Tecnología y canales:** [COMPLETAR]<br><br>**Evidencia:** [minuto o cita breve] |

##### ENTREVISTA 3

| Campo | Registro |
|---|---|
| **ENTREVISTA 3** | **[COMPLETAR]** |
| Nombre entrevistado | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Profesión / rol | **[COMPLETAR]** |
| Distrito / departamento | **[COMPLETAR]** |
| Inicio del video | **[hh:mm:ss]** |
| Fin del video | **[hh:mm:ss]** |
| Link del video | **[PEGAR URL DEL VIDEO CONSOLIDADO]** |
| Foto entrevista | **[INSERTAR captura en `images/interviews/`]** |
| Resumen | **Principales respuestas:** [COMPLETAR]<br><br>**Características objetivas:** [COMPLETAR]<br><br>**Características subjetivas:** [COMPLETAR]<br><br>**Tecnología y canales:** [COMPLETAR]<br><br>**Evidencia:** [minuto o cita breve] |

## 2.3. Needfinding

### 2.3.1. User Personas

### 2.3.2. User Task Matrix

### 2.3.3. User Journey Mapping

### 2.3.4. Empathy Mapping

### 2.3.5. Big Picture EventStorming

### 2.3.6. Ubiquitous Language

## 2.4. Requirements specification

### 2.4.1. User Stories

#### Epics

#### User Stories

#### Technical Stories

#### Spike Stories

### 2.4.2. Impact Mapping

### 2.4.3. Product Backlog

## 2.5. Strategic-Level Domain-Driven Design

### 2.5.1. EventStorming

#### 2.5.1.1. Candidate Context Discovery

#### 2.5.1.2. Domain Message Flows Modeling

#### 2.5.1.3. Bounded Context Canvases

### 2.5.2. Context Mapping

### 2.5.3. Software Architecture

#### 2.5.3.1. Software Architecture Context Level Diagrams

#### 2.5.3.2. Software Architecture Container Level Diagrams

#### 2.5.3.3. Software Architecture Deployment Diagrams

## 2.6. Tactical-Level Domain-Driven Design

### 2.6.1. Bounded Context: **[COMPLETAR: nombre del BC]**

#### 2.6.1.1. Domain Layer

#### 2.6.1.2. Interface Layer

#### 2.6.1.3. Application Layer

#### 2.6.1.4. Infrastructure Layer

#### 2.6.1.5. Bounded Context Software Architecture Component Level Diagrams

#### 2.6.1.6. Bounded Context Software Architecture Code Level Diagrams

##### 2.6.1.6.1. Bounded Context Domain Layer Class Diagrams

##### 2.6.1.6.2. Bounded Context Database Design Diagram
