# Capítulo III: Solution UI/UX Design

## 3.1. Product design

En este capítulo se presenta el diseño del producto Qlic en sus tres puntos de contacto con el usuario: el sitio web estático (Landing Page), la aplicación móvil nativa Android y la aplicación móvil multiplataforma. Las decisiones de estilo, arquitectura de información y flujos de interacción se derivan de los requisitos de la sección 2.4, de los User Personas de la sección 2.3.1 (Carlos Abanto, del segmento PYMES, y Claudia Morales, del segmento Hogares y Familias) y de los artefactos de Needfinding, de modo que la experiencia sea coherente en diseño, usabilidad e interacción.

### 3.1.1. Style Guidelines

En esta sección se establece el repositorio central de decisiones visuales y de comunicación que todo el equipo aplica en el Landing Page y en las aplicaciones móviles. Se toma como base el Design System Material Design 3, adaptado a la identidad de Qlic, y se sustenta cada decisión en los principios de diseño de claridad, consistencia, jerarquía visual y diseño inclusivo.

#### 3.1.1.1. General Style Guidelines

**Branding.** Qlic transmite tranquilidad y control sobre un recurso cotidiano. La identidad se apoya en el azul como color de confianza y en el logo de Qlic en versión horizontal para cabeceras y en versión de ícono para la aplicación móvil. [COMPLETAR: imagen del logo y reglas de uso: zona de respeto y tamaño mínimo].

**Tono de comunicación.** Se ubica en las cuatro dimensiones de tono de voz de Nielsen Norman Group de la siguiente manera:

| Dimensión | Posición | Justificación |
|---|---|---|
| Divertido / Serio | Serio | Se trata de dinero y de riesgo de fugas; las alertas deben tomarse en serio. |
| Formal / Casual | Casual | Carlos y Claudia piden una interfaz sin tecnicismos y cercana. |
| Respetuoso / Irreverente | Respetuoso | La aplicación comunica problemas (fugas, consumo alto) sin culpar al usuario. |
| Entusiasta / Sereno | Sereno | Las alertas no deben alarmar de más; las personas entrevistadas rechazan la saturación de notificaciones. |

El idioma por defecto de la interfaz es inglés y se ofrece español, conforme al alcance del proyecto.

**Typography.** Se utilizan dos familias: Poppins para títulos y encabezados, por su forma geométrica limpia, y Roboto para párrafos, datos y etiquetas, por su alta legibilidad en pantallas pequeñas. La escala propuesta para móvil es:

| Nivel | Familia | Tamaño | Peso |
|---|---|---|---|
| Headline | Poppins | 24 sp | SemiBold |
| Title | Poppins | 20 sp | Medium |
| Subtitle | Roboto | 16 sp | Medium |
| Body | Roboto | 14 sp | Regular |
| Caption | Roboto | 12 sp | Regular |

Se usan unidades `sp` en Android para respetar la configuración de tamaño de texto del dispositivo, lo que apoya el diseño inclusivo.

**Colors.** La paleta parte del azul primario del sitio web y se completa con colores semánticos para los estados de la aplicación.

| Token | Hex | Uso | Estado |
|---|---|---|---|
| Primary | `#0C4AFD` | Barra superior, botones principales, elementos activos de navegación | Existente |
| On Primary | `#FFFFFF` | Texto e íconos sobre Primary | Existente |
| Text Primary | `#0F0F0F` | Títulos y texto principal | Existente |
| Text Secondary | `#6B7280` | Descripciones y texto de apoyo | Existente |
| Background | `#FFFFFF` | Fondo general y cards | Existente |
| Surface Soft | `#E8FFEE` | Secciones de énfasis suave en el Landing Page | Existente |
| Success | `#22C55E` | Dispositivo conectado, operación exitosa | Existente (se redefine su uso) |
| Warning | `#F59E0B` | Consumo por encima del umbral, dispositivo con batería baja | Propuesto |
| Error / Leak | `#DC2626` | Alerta de posible fuga, credenciales inválidas | Propuesto |
| Secondary (azul oscuro) | [COMPLETAR: hex del Figma] | Contraste y encabezados | Pendiente |

Decisiones de contraste: `#0C4AFD` sobre blanco tiene una relación aproximada de 6,1:1 y `#6B7280` sobre blanco de 4,8:1, ambas por encima del mínimo de 4,5:1 de WCAG 2.1 nivel AA para texto normal. `#22C55E` sobre blanco no alcanza ese mínimo, por lo que el verde nunca se usa como color de texto sobre fondo claro: acompaña a un ícono y a una etiqueta. Además, ningún estado se comunica solo con color; siempre lleva ícono y texto (por ejemplo, "Leak alert" con ícono de advertencia).

Regla de uso del verde: se reserva para estados de éxito y conexión. Los botones de acción principal son siempre azules, incluido el envío del formulario de contacto del Landing Page.

**Spacing.** Se usa una cuadrícula base de 8 dp (4, 8, 16, 24, 32). Las cards tienen esquinas de 12 dp y sombra suave (elevación de 1 a 2 dp), y el margen lateral de pantalla es de 16 dp. Las áreas táctiles miden como mínimo 48 × 48 dp, conforme a las pautas de accesibilidad de Android.

**Componentes móviles base** (Material 3 en Jetpack Compose):

- **Botón principal:** fondo Primary, texto On Primary, altura de 48 dp, esquinas de 12 dp.
- **Botón secundario:** contorno Primary, fondo transparente.
- **Campo de texto:** con etiqueta flotante, mensaje de error debajo en color Error y ícono de error.
- **Card de dispositivo:** nombre, Water Point, estado con ícono y última lectura.
- **Card de alerta:** ícono de severidad, título, ubicación, hora y botón "Acknowledge".
- **Barra de navegación inferior:** cinco destinos (ver 3.1.2.5).
  **Principios de diseño aplicados.** Jerarquía visual (título > dato clave > detalle) para que Claudia encuentre el consumo del día sin leer; consistencia entre Landing Page, aplicación Android y aplicación Flutter mediante los mismos tokens; retroalimentación inmediata en formularios; y diseño inclusivo (contraste, tamaños escalables, etiquetas de accesibilidad `contentDescription` en íconos y color no como único medio de información).

### 3.1.2. Information Architecture

Las decisiones de esta sección organizan el contenido del Landing Page y de la aplicación móvil para que Carlos y Claudia encuentren lo que necesitan sin esfuerzo: el estado de su agua, las alertas y sus dispositivos. Se priorizan las tareas de mayor frecuencia e importancia de la User Task Matrix (sección 2.3.2): detectar fugas o consumos anómalos, verificar el nivel de tanques y comparar el gasto entre periodos.

#### 3.1.2.1. Organization Systems

| Contenido | Sistema de organización | Justificación |
|---|---|---|
| Landing Page | Secuencial, de lo general a lo específico: propuesta de valor → funcionalidades → segmentos → planes → testimonios → preguntas frecuentes → contacto | Acompaña el proceso de decisión del visitante (US01, US02, US03). |
| Home de la aplicación | Jerárquico (visual hierarchy): estado general y consumo del día arriba, alertas activas en medio, accesos a dispositivos abajo | El dato más importante para ambos segmentos es saber si hay algo anormal. |
| Lista de dispositivos | Por tópicos (por local y por Water Point) | Responde a US13 y al segmento PYMES con más de un local. |
| Alertas | Cronológico, con filtros por estado y urgencia | Las alertas recientes son las más accionables. |
| Reportes | Cronológico (periodos) | Permite comparar entre periodos (US22). |
| Planes de suscripción | Matricial (plan × características) | Facilita la comparación de Plan Básico y Plan Gestión Pro (US02). |
| Contenido por segmento | Según audiencia (Hogares / PYMES) | Los segmentos difieren en el nivel de detalle que requieren. |
| Registro de dispositivo | Secuencial (paso a paso) | Usuarios sin conocimientos técnicos necesitan una guía lineal (US10, US16 del segmento). |

#### 3.1.2.2. Labelling Systems

Las etiquetas usan el mínimo de palabras y el mismo término en toda la experiencia. El idioma base es inglés, con su equivalente en español latinoamericano.

| Etiqueta (Ingles) | Español | Qué agrupa |
|---|---|---|
| Home | Inicio | Resumen de consumo y alertas activas |
| Devices | Dispositivos | Sensores, Water Points y estado de conexión |
| Alerts | Alertas | Fugas, consumo anómalo y nivel bajo de tanque |
| Reports | Reportes | Consumo por periodo, comparación y costo estimado |
| Account | Cuenta | Perfil, plan, usuarios autorizados, términos y condiciones |
| Sign in | Iniciar sesión | Acceso a la aplicación |
| Create account | Crear cuenta | Registro de suscriptor |
| Forgot password? | ¿Olvidaste tu contraseña? | Recuperación de acceso |
| Acknowledge | Confirmar atención | Marca una alerta como atendida |

Se evita el uso de términos técnicos como "sensor IoT" o "umbral" en las pantallas principales; en su lugar se usan "device" y "limit". Los términos del dominio coinciden con el Ubiquitous Language de la sección 2.3.6 (por ejemplo, Water Point).

#### 3.1.2.3. SEO Tags and Meta Tags

Los valores de esta sección mantienen una propuesta de valor coherente con los segmentos PYMES y Hogares y Familias: detectar fugas y consumos anómalos, consultar el consumo desde el celular y recibir alertas accionables. El idioma principal de publicación es inglés y se incluye la localización `es-419` para español latinoamericano. El campo **Author** identifica al equipo responsable del producto, no a una persona individual.

**Landing Page (sitio web estático).** La página pública utiliza una sola experiencia con navegación por anclas; por eso cada fila identifica la página o sección que debe conservar sus metadatos al generarse o compartirse.

| Página o sección | Title | Meta description | Meta keywords | Author |
|---|---|---|---|---|
| Home / propuesta de valor | `Qlic \| Smart Water Monitoring` | `Detect leaks and unusual water consumption before they become costly. Monitor your home or business with Qlic.` | `Qlic, smart water monitoring, leak detection, water consumption, home, business` | `Qlic Team` |
| Soluciones para PYMES | `Qlic for Businesses \| Prevent Water Loss` | `Give your business clear water-consumption data, timely leak alerts and practical actions to reduce operating costs.` | `water monitoring for business, leak alerts, commercial water use, Qlic` | `Qlic Team` |
| Soluciones para hogares | `Qlic for Homes \| Prevent Leaks` | `Protect your home from hidden leaks and unusual consumption with simple mobile alerts and clear water data.` | `home water monitoring, household leak detection, water alerts, Qlic` | `Qlic Team` |
| Planes | `Qlic Plans \| Choose Your Water Monitoring Plan` | `Compare Qlic plans and choose the level of water monitoring, alerts and reports that fits your needs.` | `Qlic plans, water monitoring subscription, leak detection plan, water reports` | `Qlic Team` |
| Contacto | `Contact Qlic \| Water Monitoring Support` | `Talk to the Qlic team about water monitoring, installation guidance, support and subscription plans.` | `contact Qlic, water monitoring support, sensor installation, Qlic` | `Qlic Team` |
| Términos y condiciones | `Qlic Terms and Conditions` | `Review the terms that govern access to Qlic services, accounts, alerts and water-monitoring features.` | `Qlic terms, service conditions, water monitoring privacy` | `Qlic Team` |

**Web Application.** Estas etiquetas corresponden a las vistas principales descritas en la arquitectura de información. Las rutas son nombres funcionales de pantalla; no se presentan como URL públicas hasta que se implemente el frontend.

| Vista | Title | Meta description | Meta keywords | Author |
|---|---|---|---|---|
| Sign in | `Sign in \| Qlic` | `Sign in to Qlic to review water consumption, devices and active alerts.` | `Qlic sign in, water monitoring account, water alerts` | `Qlic Team` |
| Home dashboard | `Dashboard \| Qlic` | `See today's water consumption, active alerts and device status in one place.` | `Qlic dashboard, water consumption, leak alerts, device status` | `Qlic Team` |
| Devices | `Devices \| Qlic` | `Review connected devices and Water Points, their status and latest readings.` | `Qlic devices, Water Point, connected water sensors` | `Qlic Team` |
| Alerts | `Alerts \| Qlic` | `Review, filter and acknowledge water leaks, unusual consumption and low-battery alerts.` | `Qlic alerts, leak alert, unusual water consumption` | `Qlic Team` |
| Reports | `Reports \| Qlic` | `Compare water consumption and estimated cost by period and location.` | `Qlic water reports, consumption comparison, estimated water cost` | `Qlic Team` |
| Account | `Account \| Qlic` | `Manage your Qlic profile, plan, authorized users and service preferences.` | `Qlic account, subscription plan, authorized users` | `Qlic Team` |

Además de los metadatos mínimos solicitados, el Landing Page debe declarar `lang="en"`, `hreflang="en"` y `hreflang="es-419"`, una URL canónica y etiquetas Open Graph (`og:title`, `og:description`, `og:type`, `og:url` y `og:image`) para que el enlace compartido conserve el contexto de la página. En las pantallas autenticadas se prioriza el título de la vista y la accesibilidad; el contenido no debe depender de `meta keywords` para funcionar.

Ejemplo de implementación para la página principal:

```html
<title>Qlic | Smart Water Monitoring</title>
<meta name="description" content="Detect leaks and unusual water consumption before they become costly. Monitor your home or business with Qlic.">
<meta name="keywords" content="Qlic, smart water monitoring, leak detection, water consumption, home, business">
<meta name="author" content="Qlic Team">
<link rel="canonical" href="/">
<meta property="og:title" content="Qlic | Smart Water Monitoring">
<meta property="og:description" content="Detect leaks and unusual water consumption before they become costly.">
```

La ruta `/` representa la página principal; el hosting debe resolverla al dominio público real del proyecto. La imagen Open Graph debe apuntar al recurso gráfico versionado que el equipo publique. La longitud de los títulos y descripciones se mantiene deliberadamente breve para evitar truncamiento en resultados y enlaces compartidos.

**ASO para las aplicaciones móviles.** Los siguientes valores se aplican a la ficha de Qlic en una tienda de aplicaciones y se localizan para inglés y español latinoamericano.

| Elemento ASO | English (en-US) | Español latinoamericano (es-419) |
|---|---|---|
| App Title | `Qlic Water Monitor` | `Qlic Monitor de Agua` |
| App subtitle | `Detect leaks. Control water use.` | `Detecta fugas. Controla tu consumo.` |
| App keywords | `water monitoring, leak detection, water alerts, consumption, smart home, business` | `monitoreo de agua, detección de fugas, alertas, consumo, hogar inteligente, negocio` |
| App description | `Qlic helps homes and businesses monitor water consumption, detect unusual use and act on clear mobile alerts. Review devices, compare periods and keep water costs under control.` | `Qlic ayuda a hogares y negocios a monitorear el consumo de agua, detectar usos inusuales y actuar con alertas móviles claras. Revisa dispositivos, compara periodos y mantén bajo control el gasto de agua.` |

La descripción ASO no promete corte automático ni ahorro garantizado; comunica únicamente capacidades contempladas en el alcance de Qlic. Las palabras clave se relacionan con las necesidades observadas en las entrevistas y no incluyen marcas de terceros.

#### 3.1.2.4. Searching Systems

La aplicación ofrece búsqueda donde el volumen de información lo justifica:

| Ubicación | Qué se busca | Filtros | Cómo se muestran los resultados |
|---|---|---|---|
| Devices | Nombre de dispositivo o de Water Point | Local, estado (Connected / Offline / Low battery) | Lista de cards de dispositivo con el término coincidente resaltado |
| Alerts | Texto de la alerta o ubicación | Estado (Open / Acknowledged), urgencia (High / Medium / Low), rango de fechas | Lista cronológica inversa con ícono de severidad |
| Reports | No aplica búsqueda de texto | Periodo (día, semana, mes) y local | Gráfico y tabla del periodo |

Si no hay coincidencias, se muestra un estado vacío con un mensaje claro ("No devices match your search") y una acción para limpiar los filtros. En el Landing Page, el acceso a la información se resuelve con navegación anclada y una sección de preguntas frecuentes, ya que su contenido es breve y no justifica un buscador.

#### 3.1.2.5. Navigation Systems

**Aplicación móvil.** Se adopta una barra de navegación inferior con cinco destinos (Home, Devices, Alerts, Reports, Account), patrón recomendado por Material Design para entre tres y cinco destinos de primer nivel y de alcance cómodo con el pulgar. Además:

- El flujo de autenticación (Sign in, Create account, Forgot password) se presenta fuera de la barra inferior y, una vez iniciada la sesión, el usuario llega a Home.
- Las pantallas de detalle (detalle de dispositivo, detalle de alerta) se abren con navegación jerárquica y botón "Back" en la barra superior.
- Las acciones de mayor frecuencia se ubican en Home: ver alertas activas y acceder al detalle de consumo.
- Las notificaciones push llevan directamente al detalle de la alerta correspondiente (deep link), lo que reduce pasos para la tarea crítica.
- El registro de un dispositivo nuevo se inicia desde Devices y usa un flujo secuencial con lectura de código QR.
  **Landing Page.** Barra de navegación superior fija con anclas a cada sección; en móvil se convierte en menú hamburguesa. El botón de llamada a la acción "Contact Sales" permanece visible, y el enlace a Terms and Conditions se ubica en el footer. [COMPLETAR: confirmar etiquetas finales de la barra].

### 3.1.3. Landing Page UI Design

El Landing Page traduce las decisiones de las secciones 3.1.1 y 3.1.2 en una página informativa que presenta el modelo de negocio, los planes de suscripción y el llamado a la descarga de la aplicación. Se diseñó primero para pantalla móvil y luego se extendió a escritorio.

#### 3.1.3.1. Landing Page Wireframe

Se presentan los wireframes para Desktop Web Browser y Mobile Web Browser. La estructura sigue el orden definido en 3.1.2.1: encabezado con logo y navegación, Hero con propuesta de valor y dos llamados a la acción, funcionalidades, soluciones por segmento, planes, testimonios, preguntas frecuentes, formulario de contacto y footer con enlaces legales.

-

Explicación: en la versión de escritorio las funcionalidades y los planes se presentan en columnas; en móvil pasan a una sola columna y la navegación se colapsa en menú hamburguesa, manteniendo el orden de lectura. La jerarquía visual coloca la propuesta de valor y el botón principal en la primera pantalla. Se aplica diseño inclusivo con orden lógico de lectura, etiquetas claras y atributos ARIA en navegación, formulario y preguntas frecuentes. [COMPLETAR: ajustar si los wireframes cambian tras corregir el contenido].

#### 3.1.3.2. Landing Page Mock-up

Los mock-ups aplican el Design System definido en 3.1.1: Poppins y Roboto, azul `#0C4AFD` para acciones principales, cards con esquinas redondeadas y verde reservado a estados de éxito.

-

Explicación: el Hero comunica el beneficio central de Qlic (visibilidad del consumo de agua y alertas oportunas) para hogares y PYMES. La sección de planes presenta Plan Básico y Plan Gestión Pro en formato de comparación (US02). Los testimonios provienen de las entrevistas de validación del proyecto. El formulario de contacto informa el dato faltante en caso de error (US03) y el selector de idioma permite cambiar entre inglés y español latinoamericano (US04). El footer incluye el enlace a los términos y condiciones del servicio y el video About-the-Product. [COMPLETAR: confirmar nombres de planes y precios con el equipo].

### 3.1.4. Mobile Applications UX/UI Design

#### 3.1.4.2. Mobile Applications Wireflow Diagrams

Se presenta un wireflow por cada User goal de las funcionalidades de autenticación y de la pantalla Home. Cada wireflow encadena wireframes y agrega un paso cuando la interacción modifica la pantalla. Se elaboran en Lucidchart u Overflow a partir de los wireframes de Figma.

#### 3.1.4.4. Mobile Applications User Flow Diagrams

Los User Flows incluyen los mock-ups de cada pantalla y las rutas esperada (happy path) y alternativas (unhappy paths). Son consistentes con los wireflows anteriores.

