# Capítulo II: Requirements Development and Software Solution Design

> **Alcance de AV1.** Este capítulo documenta la investigación y el diseño de investigación de Qlic. No afirma que la aplicación móvil, los dispositivos IoT ni los servicios hayan sido implementados; su desarrollo corresponde a los siguientes hitos.

## 2.1. Competidores

Qlic es una propuesta móvil para que propietarios y administradores de PYMES, así como responsables de hogares, visualicen el consumo de agua, identifiquen anomalías y tomen decisiones oportunas. El análisis considera tres productos digitales con capacidades similares: Wint, Flo by Moen y Phyn. Se clasifican como competidores indirectos mientras Qlic no se comercialice: atienden mercados y canales distintos, pero compiten por la necesidad de monitorear, detectar fugas y reducir el desperdicio de agua.

### 2.1.1. Análisis competitivo

#### Competitive Analysis Landscape

**Pregunta de análisis.** ¿Qué capacidades de producto y enfoques de mercado de las soluciones de monitoreo hídrico deben guiar una propuesta móvil diferenciada para PYMES y hogares de Lima Metropolitana?

Para la versión exportada del informe, cada cabecera debe incluir el nombre y el logotipo oficial autorizado de Qlic, Wint, Flo by Moen y Phyn. Los archivos de marca no se incorporan aún para no reutilizar logotipos de terceros sin autorización.

| Dimensión | Qlic (propuesta) | Wint | Flo by Moen | Phyn |
|---|---|---|---|---|
| **Perfil / overview** | Propuesta orientada a PYMES y hogares peruanos para interpretar consumo, alertas y oportunidades de ahorro desde una experiencia móvil en español. | Plataforma de inteligencia hídrica para edificios comerciales e institucionales; combina monitoreo en tiempo real, detección de anomalías y corte remoto. | Sistema doméstico de seguridad hídrica que se administra desde una aplicación móvil y alerta ante fugas o uso anómalo. | Monitor doméstico autoinstalable para una vivienda; detecta fugas, analiza uso por accesorios y notifica mediante su aplicación. |
| **Ventaja competitiva** | Hipótesis de diferenciación: acompañamiento local, lenguaje claro, flujos móviles de baja fricción y priorización de PYMES que no disponen de equipos especializados. | Cobertura empresarial, analítica basada en IA y capacidad de cerrar el suministro ante incidentes. | Integración entre dispositivo de corte y aplicación con panel de consumo, alertas y modos de uso. | Instalación bajo un lavadero, análisis de consumo y notificaciones de fuga mediante aplicación, SMS y soporte para contactar a un gasfitero. |
| **Mercado objetivo** | PYMES con consumo operativo de agua y hogares responsables de su recibo y mantenimiento básico. | Instalaciones comerciales, institucionales, construcción y portafolios de inmuebles. | Hogares que buscan proteger su instalación principal de agua. | Hogares que desean detectar fugas y comprender su consumo doméstico. |
| **Estrategias de marketing observables** | Por validar mediante entrevistas: comunicación de ahorro, continuidad operativa y sostenibilidad en canales digitales locales. | Posicionamiento de prevención de daños, sostenibilidad y eficiencia para organizaciones. | Comunicación de seguridad del hogar y control desde la aplicación. | Comunicación de instalación sencilla, protección del hogar, alertas y visibilidad del consumo. |
| **Productos y servicios** | Futuro sistema móvil de monitoreo, alertas, historial y acompañamiento de instalación; las funcionalidades finales dependen de la investigación de usuarios. | Plataforma, unidades de control y servicios de monitoreo para prevenir fugas y desperdicios. | Dispositivo Smart Water Shutoff y aplicación Flo by Moen para control, consumo y alertas. | Phyn Smart Water Assistant, aplicación móvil, alertas y funciones de revisión de instalaciones. |
| **Precios y costos** | Modelo y precio por validar; no se debe publicar una tarifa antes de contrastarla con usuarios y costos de operación. | Precio público no identificado en la información revisada; su sitio dirige a una solicitud comercial. | Precio sujeto al distribuidor y mercado; el manual revisado no establece una tarifa oficial. | El sitio de Phyn muestra US$299.99 para Smart Water Assistant al momento de la revisión. |
| **Canales de distribución** | Hipótesis: aplicación móvil, instalación con aliados locales y canales digitales dirigidos a PYMES y hogares. | Venta consultiva y operación de plataforma en canales empresariales. | Dispositivo físico y aplicación para iOS y Android. | Venta directa del dispositivo y aplicación disponible para iOS y Android. |

Las características comparadas se verificaron en las páginas oficiales de cada producto. Wint describe monitoreo, detección de anomalías y cierre remoto para instalaciones de mayor escala; Flo by Moen documenta en su aplicación el panel de consumo y alertas; Phyn presenta alertas por aplicación y SMS, análisis de uso y el precio publicado de Smart Water Assistant (Wint, s. f.; Flo by Moen, s. f.; Phyn, s. f.).

La comparación muestra dos espacios de aprendizaje para Qlic. Por un lado, Wint demuestra que la detección de anomalías debe traducirse en una acción clara y oportuna, no solo en la visualización de datos. Por otro, Flo by Moen y Phyn confirman que las alertas, el consumo comprensible y el acompañamiento desde el teléfono son capacidades centrales para el segmento residencial. Qlic debe validar si estos patrones se trasladan a PYMES locales y qué barreras aparecen en la instalación, conectividad, confianza y disposición de pago.

#### Análisis SWOT

El siguiente análisis es preliminar y sirve para formular preguntas de investigación; no sustituye la evidencia que el equipo obtendrá en las entrevistas.

| Producto | Fortalezas | Debilidades | Oportunidades | Amenazas |
|---|---|---|---|---|
| **Qlic** | Enfoque móvil en español, propuesta para dos segmentos locales y posibilidad de traducir datos de agua en decisiones simples. | Marca sin validación, ausencia de evidencia de uso e incertidumbre sobre instalación, costos y soporte. | Diseñar una experiencia ajustada al contexto peruano, alianzas con instaladores y mensajes de ahorro verificable. | Competidores consolidados, dependencia de hardware/conectividad y desconfianza frente a sensores nuevos. |
| **Wint** | Monitoreo en tiempo real, detección basada en IA, corte remoto y experiencia empresarial. | Enfoque corporativo que puede resultar complejo o costoso para micro y pequeñas empresas. | Paquetes de menor escala y alianzas regionales para expandir su mercado. | Soluciones móviles más simples, proveedores locales y restricciones presupuestales de sus clientes. |
| **Flo by Moen** | Aplicación con alertas, panel de consumo y controles de seguridad doméstica. | Alcance centrado en hogar; no se evidencia una propuesta específica para la operación cotidiana de PYMES peruanas. | Extender servicios para propiedades múltiples y distribuidores regionales. | Diferencias de infraestructura, soporte e instalación entre mercados; alternativas que adapten lenguaje y operación local. |
| **Phyn** | Instalación doméstica guiada, analítica de uso, alertas por aplicación y SMS, y orientación de soporte. | Producto focalizado en viviendas y dependiente de condiciones de instalación compatibles. | Integraciones de hogar conectado y expansión de servicios de mantenimiento. | Disponibilidad local, sensibilidad al precio y propuestas que combinen soporte cercano con flujos móviles más sencillos. |

### 2.1.2. Estrategias y tácticas frente a competidores

Las estrategias de Qlic se plantean como hipótesis para validar con los dos segmentos objetivo antes de decidir el alcance del producto.

| Estrategia | Tácticas iniciales | Competidor / hallazgo atendido | Indicador a validar en entrevistas |
|---|---|---|---|
| **Diseño móvil local y comprensible** | Redactar alertas en español claro, mostrar el nivel de urgencia y proponer el siguiente paso según el tipo de incidente. | Las alertas móviles son una capacidad esperada en Flo by Moen y Phyn; Qlic debe diferenciarse por contexto y claridad. | Comprensión de una alerta y acción que la persona declara que tomaría. |
| **Valor para la operación de PYMES** | Investigar horarios críticos, responsables de mantenimiento, impacto de cortes y reportes requeridos para decidir si se priorizan funciones operativas. | Wint atiende instalaciones de mayor escala; existe una hipótesis de necesidad no cubierta para PYMES. | Problemas operativos recurrentes, costo percibido y disposición a probar una solución. |
| **Onboarding y soporte de baja fricción** | Validar preferencias sobre instalación guiada, acompañamiento remoto y derivación a un técnico cuando corresponda. | Flo by Moen y Phyn hacen visible el valor de la instalación y el control desde la aplicación. | Barreras de confianza, tiempo aceptable de instalación y canal de soporte preferido. |
| **Decisiones basadas en evidencia** | Probar qué resumen de consumo, alerta o comparación resulta útil antes de definir visualizaciones y notificaciones. | Wint y Phyn convierten datos de agua en analítica; Qlic debe evitar presentar métricas que no sean accionables. | Datos que el usuario consulta, periodicidad y decisión que espera tomar con ellos. |
| **Confianza y protección de datos** | Preguntar por autorizaciones, datos que generarían confianza y expectativas de continuidad cuando falle la conectividad. | Los productos IoT dependen de datos, conectividad y dispositivos instalados. | Condiciones mínimas para permitir el uso de sensores y notificaciones. |

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
| Enlace al video consolidado | **[PEGAR URL]** |
| Captura de evidencia | **[INSERTAR captura del video en images/interviews/ y referenciarla aquí]** |
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

### 2.2.3. Análisis de entrevistas

Pendiente de elaboración tras completar las entrevistas reales y las fichas de registro. El equipo deberá consolidar por segmento las variables objetivas y subjetivas en cuadros con frecuencias y porcentajes, indicando el tamaño de muestra utilizado. Cada conclusión deberá poder rastrearse a los registros y a los videos; esta sección no debe llenarse con supuestos previos ni datos inventados.

## Referencias

- Flo by Moen. (s. f.). *Smart water shutoff manual*. https://manuals.meetflo.com/Smart-Water-Shutoff-Manual.pdf
- Phyn. (s. f.). *Phyn Smart Water Assistant*. https://phyn.com/products/phyn
- Wint. (s. f.). *Commercial water management and leak prevention solutions*. https://wint.ai/
