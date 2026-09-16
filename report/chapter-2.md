# Capítulo II: Requirements Development and Software Solution Design

> **Alcance de AV1.** Este capítulo documenta la investigación y el diseño de investigación de Qlic. No afirma que la aplicación móvil, los dispositivos IoT ni los servicios hayan sido implementados; su desarrollo corresponde a los siguientes hitos.

## 2.1. Competidores

Qlic propone una solución móvil para que propietarios y administradores de PYMES, así como responsables de hogares, visualicen el consumo de agua, identifiquen anomalías y tomen decisiones oportunas. Para evitar comparar productos de dominios distintos sin explicarlo, se tomó como punto de partida el repositorio guía de WASD25, cuya rama chapter-2 analiza Qlic con los segmentos PYMES y hogares y propone como referentes a Badger Meter, Itron y OptiRTC. La selección fue corroborada con las páginas oficiales vigentes de cada organización.

Badger Meter e Itron son referentes directos de smart water a escala de utilities, ciudades y operaciones comerciales; OptiRTC es un competidor adyacente de gestión de agua pluvial con IoT y control adaptativo. Los tres compiten por la necesidad de convertir datos hídricos en decisiones, aunque Qlic busca una experiencia móvil localizada para PYMES y hogares. Wint se conserva como benchmark secundario de detección de fugas comerciales, pero no reemplaza el conjunto comparable de la guía.

### 2.1.1. Análisis competitivo

#### Evidencia de consistencia con el repositorio guía

| Criterio | Repositorio guía | Qlic en este informe | Decisión |
|---|---|---|---|
| Problema | Gestión inteligente del agua, desperdicio, costos y monitoreo. | Monitoreo móvil, alertas y optimización del consumo en PYMES y hogares. | Consistente. |
| Segmentos | PYMES, locales e instituciones y hogares/familias. | PYMES y comercios locales; hogares y familias. | Consistente para AV1. |
| Competidores base | Badger Meter, Itron y OptiRTC. | Mismos tres referentes, corroborados en sus sitios oficiales. | Se mantienen para comparabilidad. |
| Diferenciación | Solución digital accesible y sostenible. | Experiencia móvil en español, onboarding de baja fricción y soporte local por validar. | Se adapta a la visión móvil. |

#### Competitive Analysis Landscape

**Pregunta de análisis.** ¿Qué capacidades y enfoques de los referentes de smart water debe adoptar o evitar Qlic para ofrecer una experiencia móvil diferenciada a PYMES y hogares de Lima Metropolitana?

| Qlic | Badger Meter | Itron | OptiRTC |
|---|---|---|---|
| <img src="../images/competitors/qlic.jpg" alt="Logotipo de Qlic" width="150"><br>**Qlic** | <img src="../images/competitors/badger-meter.jpg" alt="Logotipo de Badger Meter" width="150"><br>[**Badger Meter**](https://www.badgermeter.com/blueedge/) | <img src="../images/competitors/itron.jpg" alt="Logotipo de Itron" width="150"><br>[**Itron**](https://emea.itron.com/categories/smart-water-solutions) | <img src="../images/competitors/optirtc.jpg" alt="Logotipo de Opti" width="150"><br>[**OptiRTC / Opti**](https://www.optirtc.com/solution) |

*Fuente de los logotipos:* assets de la rama chapter-2 del repositorio guía de WASD25. Antes de la entrega, el equipo debe conservar únicamente activos cuyo uso académico esté autorizado.

| Dimensión | Qlic (propuesta) | Badger Meter | Itron | OptiRTC |
|---|---|---|---|---|
| **Perfil / overview** | Startup propuesta para ayudar a PYMES y hogares peruanos a interpretar consumo, alertas y oportunidades de ahorro desde el móvil. | BlueEdge integra medición, conectividad, software y servicios para gestionar agua de forma continua en utilities, clientes comerciales e industriales. | Portafolio de smart water para utilities y ciudades que combina dispositivos, redes, plataformas y analítica para transformar datos en decisiones operativas. | Plataforma de monitoreo continuo y control adaptativo de aguas pluviales que combina sensores, pronósticos y reglas de control en la nube. |
| **Ventaja competitiva** | Hipótesis de diferenciación: lenguaje claro, experiencia móvil en español, acompañamiento local y foco en necesidades de PYMES que no disponen de equipos especializados. | Escala, experiencia histórica en medición y suite integrada de dispositivos, software y soporte. | Cobertura de infraestructura, conectividad y analítica interoperable para utilities y ciudades. | Control predictivo de infraestructura pluvial, integración con sensores externos y automatización basada en pronósticos. |
| **Mercado objetivo** | PYMES con consumo operativo de agua y hogares responsables del recibo y mantenimiento básico. | Utilities, municipios y clientes comerciales e industriales. | Utilities de agua, ciudades y operadores de infraestructura. | Autoridades, municipios y operadores de infraestructura de aguas pluviales. |
| **Estrategias de marketing observables** | Por validar: comunicar ahorro, continuidad operativa y sostenibilidad en canales móviles y redes locales. | Venta consultiva, demostraciones técnicas, casos de uso y solicitud de cotización. | Posicionamiento como socio de modernización de utilities y comunicación de eficiencia, conservación y resiliencia. | Casos de proyectos, metodología de implementación y comunicación de resiliencia urbana. |
| **Productos y servicios** | Propuesta futura de aplicación móvil, alertas, historial, recomendaciones y acompañamiento de instalación; el alcance depende de la investigación. | Medidores, sensores, válvulas, conectividad y analítica BlueEdge para medición y control. | Medición inteligente, módulos de comunicación, gestión de datos, detección de fugas y plataformas para utilities. | CMAC, gateways, paneles, portal web, API e integración de sensores y actuadores para stormwater. |
| **Precios y costos** | Modelo y precio por validar con usuarios y costos de operación; no se declara una tarifa en AV1. | No publica una tarifa estándar; su sitio dirige a solicitar una cotización. | Soluciones empresariales cuyo costo depende del despliegue, infraestructura y servicio contratado. | Precio sujeto al proyecto, activos, integración y operación; no se muestra una tarifa estándar. |
| **Canales de distribución** | Aplicación móvil, aliados de instalación y canales digitales dirigidos a PYMES y hogares; hipótesis por validar. | Venta consultiva, servicios de implementación y plataformas web/campo. | Venta a utilities, partners, infraestructura conectada y plataformas de gestión. | Proyectos de infraestructura, portal web, APIs y servicios de implementación. |

Las capacidades se corroboraron con las fuentes oficiales: BlueEdge declara medición, conectividad y analítica para operaciones de agua; Itron documenta dispositivos, redes, leak sensing y plataformas para utilities; Opti describe monitoreo continuo, pronósticos, control adaptativo, dashboard y APIs. Estas evidencias confirman que la guía escogió competidores del mismo dominio, aunque a una escala mayor que el alcance inicial de Qlic. Wint se mantiene como referencia secundaria porque su plataforma comercial añade detección de anomalías y cierre remoto, útil para comparar la respuesta ante fugas, pero no forma parte del conjunto base de la guía.

#### Análisis SWOT

El FODA es preliminar y orienta las entrevistas; no sustituye evidencia de usuarios ni demuestra implementación.

| Producto | Fortalezas | Debilidades | Oportunidades | Amenazas |
|---|---|---|---|---|
| **Qlic** | Foco móvil en español, segmentos locales y posibilidad de convertir datos hídricos en decisiones simples. | Marca y propuesta aún por validar; dependencia de sensores, conectividad, instalación y soporte. | Alianzas con instaladores, planes para PYMES, educación de ahorro y acompañamiento local. | Suites globales con mayor escala, resistencia al hardware y sensibilidad al precio. |
| **Badger Meter** | Suite integrada, experiencia en medición y cobertura de clientes municipales, comerciales e industriales. | Complejidad y probable costo de adopción para hogares y microempresas. | Paquetes pequeños, partners locales y experiencias móviles para usuarios finales. | Startups de menor costo, plataformas especializadas y proveedores locales. |
| **Itron** | Infraestructura, conectividad, analítica y experiencia con utilities y ciudades en múltiples países. | Enfoque de infraestructura que puede quedar lejos de la necesidad cotidiana de un hogar o una PYME. | Integraciones con utilities, educación del consumidor y soluciones de conservación. | Licitaciones, ciclos de compra largos y alternativas más simples de instalación. |
| **OptiRTC / Opti** | Control adaptativo, pronósticos, sensores, APIs y experiencia en resiliencia de aguas pluviales. | Dominio principal distinto al monitoreo de fugas de consumo; no es una solución residencial directa. | Extender analítica a pequeños sistemas y crear alianzas con municipios. | Soluciones especializadas en stormwater, cambios regulatorios y complejidad de infraestructura. |

### 2.1.2. Estrategias y tácticas frente a competidores

Las siguientes estrategias convierten la comparación en hipótesis accionables para Qlic. Deben validarse mediante el diseño de entrevistas antes de convertirse en requisitos.

| Estrategia | Tácticas iniciales | Competidor / hallazgo atendido | Indicador a validar |
|---|---|---|---|
| **Diferenciación móvil y local** | Diseñar alertas en español claro, niveles de urgencia y acciones concretas para cada segmento. | Las soluciones guía priorizan infraestructura; Qlic debe acercar el dato al usuario cotidiano. | El participante entiende una alerta y puede explicar qué acción tomaría. |
| **Escala progresiva para PYMES** | Proponer onboarding por etapas, sensor inicial y reportes que no requieran una plataforma empresarial completa. | Badger Meter e Itron ofrecen suites amplias; la barrera de complejidad debe comprobarse. | Tiempo aceptable de configuración, roles que usarían la solución y funciones mínimas. |
| **Interoperabilidad antes que encierro tecnológico** | Preguntar por medidores existentes, conectividad, APIs y necesidad de exportar datos. | Itron y Opti muestran valor en redes, integraciones y APIs. | Dispositivos actuales, restricciones de integración y formato de datos preferido. |
| **Respuesta ante fugas y anomalías** | Diseñar un flujo de alerta, confirmación, escalamiento y contacto de soporte; no prometer corte automático antes de validar riesgos. | Wint y las suites de medición convierten detección en acción. | Tipo de incidente, tiempo de respuesta y confianza para seguir una recomendación. |
| **Soporte y confianza local** | Validar instalación guiada, acompañamiento remoto, privacidad, continuidad sin conexión y derivación a técnicos. | La escala de los competidores no garantiza soporte cercano para PYMES y hogares locales. | Condiciones para autorizar sensores, canal de soporte y señales de confianza. |
| **Sostenibilidad con evidencia** | Mostrar ahorro, consumo y tendencias solo cuando el usuario pueda interpretarlos y relacionarlos con una decisión. | Los competidores comunican eficiencia y conservación; Qlic debe probar qué métrica es útil. | Métricas consultadas, frecuencia de revisión y decisión que cambia gracias al dato. |

#### Referentes oficiales consultados

- Badger Meter. (s. f.). *BlueEdge Suite of Scalable Solutions*. https://www.badgermeter.com/blueedge/
- Itron. (s. f.). *Smart Water Solutions*. https://emea.itron.com/categories/smart-water-solutions
- Opti. (s. f.). *The Opti Solution*. https://www.optirtc.com/solution
- Wint. (s. f.). *Commercial Water Management & Leak Prevention Solutions*. https://wint.ai/

## 2.2. Entrevistas

La investigación utilizará entrevistas semiestructuradas. Este formato permite comparar variables comunes entre participantes y, a la vez, profundizar en situaciones reales de consumo, fugas, mantenimiento, decisiones y uso de tecnología. Las entrevistas no deben presentar Qlic como una solución terminada ni inducir una respuesta favorable; primero se debe entender el comportamiento actual del participante.

### 2.2.1. Diseño de entrevistas

#### Objetivo de investigación

Identificar características objetivas y subjetivas de los segmentos PYMES y hogares, sus procesos actuales para gestionar el agua, los problemas que enfrentan, sus canales digitales y las condiciones que necesitarían para confiar en una futura solución móvil de monitoreo hídrico.

#### Participantes y muestra

| Segmento | Perfil de inclusión | Cantidad requerida | Exclusión | Modalidad sugerida |
|---|---|---:|---|---|
| **PYMES y comercios locales** | Propietario, administrador o responsable de operaciones/mantenimiento de una PYME que participa en decisiones sobre consumo o incidencias de agua. | 3 a 5 entrevistas | Personas que no conocen el consumo, mantenimiento ni decisiones asociadas al agua del negocio. | Presencial en el negocio o videollamada, con autorización de grabación. |
| **Hogares y familias** | Persona adulta que paga, revisa o participa en decisiones sobre el recibo, el mantenimiento o el uso de agua del hogar. | 3 a 5 entrevistas | Personas que no tienen experiencia ni responsabilidad sobre el consumo o mantenimiento del hogar. | Presencial o videollamada, con autorización de grabación. |

#### Protocolo de sesión

| Momento | Tiempo estimado | Actividad | Evidencia esperada |
|---|---:|---|---|
| Apertura | 3 min | Presentar objetivo, uso académico, duración, autorización de video y posibilidad de no responder. | Consentimiento registrado y fecha. |
| Contexto del participante | 5 min | Conocer rol, edad, distrito, ocupación, composición familiar o tipo de negocio. | Variables demográficas del registro. |
| Situación actual | 12 min | Explorar consumo, lectura de recibos, mantenimiento, incidentes y decisiones actuales. | Respuestas descriptivas y ejemplos concretos. |
| Hábitos digitales | 8 min | Identificar dispositivos, navegador, canales, marcas, fuentes de influencia y habilidades tecnológicas. | Variables subjetivas y de interacción. |
| Necesidades y frustraciones | 8 min | Profundizar en objetivos, preocupaciones, costos, tiempos de respuesta y resultados esperados. | Pains, gains y tareas actuales. |
| Cierre | 4 min | Solicitar una reflexión final, confirmar si se puede usar la información y agradecer. | Nota de cierre y confirmación de uso académico. |

#### Preguntas generales para ambos segmentos

1. ¿Cuál es su relación con el consumo, pago o mantenimiento del agua en su hogar o negocio?
2. Cuénteme cómo se informa actualmente sobre el consumo de agua y qué hace con esa información.
3. ¿Recuerda una situación reciente de fuga, consumo inusual, corte o recibo inesperado? ¿Qué ocurrió desde que la detectó hasta que la resolvió?
4. ¿Qué personas intervienen cuando aparece un problema relacionado con el agua y cómo se coordinan?
5. ¿Qué consecuencias tienen estos problemas en tiempo, dinero, tranquilidad u operación?
6. ¿Qué dispositivo utiliza con mayor frecuencia y para qué trámites o decisiones cotidianas usa el teléfono?
7. ¿Qué aplicaciones, marcas o personas influyen cuando decide probar una herramienta digital o contratar mantenimiento?
8. ¿Qué canal prefiere para recibir información importante: llamada, WhatsApp, correo, SMS, notificación móvil u otro? ¿Por qué?
9. ¿Qué información le resultaría útil revisar antes de tomar una decisión sobre el uso de agua? ¿Cómo la entendería mejor?
10. ¿Qué tendría que ocurrir para que confíe o desconfíe de un dispositivo o aplicación que le avise sobre consumo o fugas?

**Preguntas de profundización.** ¿Puede darme un ejemplo?, ¿qué hizo primero?, ¿quién tomó la decisión?, ¿con qué frecuencia sucede?, ¿qué le resultó difícil?, ¿cómo se sintió?, ¿qué alternativa ya intentó? Estas preguntas se usan solo cuando ayudan a entender un hecho narrado por el participante.

#### Segmento 1: PYMES y comercios locales

1. ¿Qué tipo de negocio es, cuántas personas trabajan y en qué actividades se utiliza agua?
2. ¿Quién revisa el recibo, el medidor y el estado de las instalaciones? ¿Qué decisiones puede tomar cada rol?
3. ¿En qué horarios o procesos un corte, fuga o baja presión afectaría más la operación?
4. ¿Cómo registra hoy el consumo, los recibos y los incidentes? ¿Qué información falta para decidir?
5. ¿Qué costos directos o interrupciones ha causado un problema de agua reciente?
6. Cuando necesita mantenimiento, ¿cómo encuentra y coordina al técnico o proveedor?
7. ¿Qué alertas operativas recibe hoy y cuáles son útiles o molestas?
8. ¿Qué tan cómodo se siente usando aplicaciones para controlar gastos, inventario o tareas del negocio? ¿Qué le facilita o dificulta usarlas?
9. ¿Qué dispositivos y canales emplea durante la jornada para coordinarse con el personal?
10. ¿Qué indicadores necesitaría ver para justificar una decisión de ahorro o mantenimiento?
11. ¿Qué condiciones de instalación, soporte o costo considerarían aceptables para evaluar una solución nueva?
12. Si pudiera cambiar una parte del proceso actual de gestión del agua, ¿cuál sería y por qué?

#### Segmento 2: Hogares y familias

1. ¿Quiénes viven en el hogar y quién suele revisar o pagar el recibo de agua?
2. ¿Cómo se enteran actualmente de cuánto consumen y cómo deciden si el monto es normal?
3. ¿Ha tenido una fuga o un cobro inesperado? Cuénteme qué señales observó y qué hizo.
4. ¿Qué espacios del hogar le generan más preocupación respecto al agua y por qué?
5. ¿Cómo se coordina con otras personas de la vivienda cuando aparece un problema?
6. ¿Cómo encuentra a un gasfitero o decide realizar una reparación? ¿Qué le genera confianza?
7. ¿Qué aplicaciones utiliza para pagos, avisos del hogar o seguimiento de gastos? ¿Qué le gusta y qué le frustra de ellas?
8. ¿Qué celular, navegador y canales de comunicación utiliza con más frecuencia?
9. ¿Qué tipo de aviso le ayudaría a actuar a tiempo y cuál preferiría no recibir?
10. ¿Qué información sobre consumo sería útil para usted o su familia y con qué frecuencia la revisaría?
11. ¿Qué dudas tendría antes de permitir que un dispositivo monitoree el agua de su vivienda?
12. ¿Qué resultado le haría sentir que una nueva herramienta realmente le aportó valor?

### 2.2.2. Registro de entrevistas

> **Plantilla obligatoria.** Esta sección debe completarse únicamente después de realizar entrevistas reales. La rúbrica exige de 3 a 5 entrevistas por segmento, nombre y apellido, edad, distrito, captura del video, momento de inicio, URL del video consolidado y un resumen descriptivo por participante. La plantilla no es evidencia por sí sola.

#### Video consolidado de entrevistas

| Campo | Registro por completar por el equipo |
|---|---|
| Archivo del video | upc-pre-202620-1acc0238-13984-Qlic-needfinding-av1.mp4 |
| Ubicación | OneDrive facilitado por el docente |
| URL de acceso | **[PEGAR URL PRIVADA DEL VIDEO]** |
| Contenido | Entrevistas de ambos segmentos, cada una con título que indique participante, segmento y fecha. |
| Calidad mínima | Secuencia identificable, ambiente apropiado, sin interrupciones relevantes y autorización del participante para el uso académico. |

#### Índice de entrevistas: PYMES y comercios locales

| ID | Nombres y apellidos | Edad | Distrito | Fecha | Inicio en video | Duración | URL / captura | Consentimiento | Estado |
|---|---|---:|---|---|---|---|---|---|---|
| PYME-01 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| PYME-02 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| PYME-03 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| PYME-04 | **[Opcional: completar si se entrevista]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| PYME-05 | **[Opcional: completar si se entrevista]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |

#### Índice de entrevistas: Hogares y familias

| ID | Nombres y apellidos | Edad | Distrito | Fecha | Inicio en video | Duración | URL / captura | Consentimiento | Estado |
|---|---|---:|---|---|---|---|---|---|---|
| HOG-01 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| HOG-02 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| HOG-03 | **[COMPLETAR]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| HOG-04 | **[Opcional: completar si se entrevista]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |
| HOG-05 | **[Opcional: completar si se entrevista]** | **[ ]** | **[ ]** | **[ ]** | **[mm:ss]** | **[mm:ss]** | **[URL y ruta de imagen]** | **[Sí / No]** | Pendiente |

#### Ficha de registro individual

Copiar esta ficha una vez por cada participante y reemplazar los campos entre corchetes con información comprobable de la entrevista.

##### Entrevista [ID]

| Campo | Registro |
|---|---|
| Segmento | **[PYMES y comercios locales / Hogares y familias]** |
| Nombres y apellidos | **[COMPLETAR]** |
| Edad | **[COMPLETAR]** |
| Distrito de residencia o trabajo | **[COMPLETAR]** |
| Fecha y modalidad | **[COMPLETAR: presencial / videollamada]** |
| Inicio y duración en video | **[mm:ss] / [mm:ss]** |
| Enlace al video consolidado | **[PEGAR LA MISMA URL PRIVADA DE ONEDRIVE REGISTRADA EN LA TABLA "VIDEO CONSOLIDADO DE ENTREVISTAS"]** |
| Captura de evidencia | **[INSERTAR una captura independiente de esta entrevista en images/interviews/ y referenciarla aquí]** |
| Autorización de uso académico | **[Sí / No; indicar modalidad de consentimiento]** |

**Resumen descriptivo de la entrevista.**

- **Contexto, biografía y rol:** [ocupación, tipo de negocio o composición del hogar, responsabilidades y antecedentes relevantes].
- **Proceso actual de gestión del agua:** [cómo se informa, detecta, registra y resuelve incidencias; incluir un caso narrado].
- **Objetivos y motivaciones:** [qué busca lograr, por qué le importa y cómo define un resultado satisfactorio].
- **Frustraciones, pains y barreras:** [costos, demoras, incertidumbre, problemas de coordinación, dificultades de instalación o confianza].
- **Personalidad, habilidades y toma de decisiones:** [forma de decidir, nivel de autonomía digital, participación de terceros y criterio de confianza].
- **Marcas e influencias:** [marcas, servicios, familiares, técnicos, redes u otras fuentes que influyen en sus decisiones].
- **Tecnología y canales de interacción:** [celular, sistema operativo si lo mencionó, navegador, aplicaciones, canales preferidos y frecuencia de uso].
- **Citas o evidencias relevantes:** [paráfrasis fiel o cita textual breve con el minuto del video].
- **Datos para el análisis posterior:** [variables observables que podrán contabilizarse, sin concluir ni generalizar antes de completar la muestra].

## Referencias

- Badger Meter. (s. f.). *BlueEdge Suite of Scalable Solutions*. https://www.badgermeter.com/blueedge/
- Itron. (s. f.). *Smart Water Solutions*. https://emea.itron.com/categories/smart-water-solutions
- Opti. (s. f.). *The Opti Solution*. https://www.optirtc.com/solution
- Wint. (s. f.). *Commercial Water Management & Leak Prevention Solutions*. https://wint.ai/
- WASD25. (2026). *Final report* [Repositorio de referencia, rama chapter-2]. https://github.com/wasd25/final-report/tree/chapter-2
