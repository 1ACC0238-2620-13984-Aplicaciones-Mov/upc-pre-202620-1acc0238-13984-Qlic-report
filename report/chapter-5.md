# Capítulo V: Conclusiones, Bibliografía y Anexos

## 5.1. Conclusiones

## 5.1. Conclusiones

1. Qlic aborda la necesidad de mejorar la visibilidad del consumo de agua y la detección oportuna de anomalías en PYMES, comercios locales y hogares.
2. El análisis competitivo permitió reconocer capacidades relevantes del mercado: medición conectada, analítica, alertas, interoperabilidad y soporte para la toma de decisiones. La oportunidad preliminar de Qlic está en traducir esos datos a una experiencia móvil clara, accesible y cercana para usuarios locales (Badger Meter, s. f.; Itron, s. f.; Opti, s. f.; Wint, s. f.).
3. Badger Meter e Itron representan soluciones directas de smart water, mientras que OptiRTC aporta un referente adyacente de monitoreo y control de aguas pluviales. Wint se conserva como referencia secundaria para la respuesta ante fugas comerciales (Badger Meter, s. f.; Itron, s. f.; Opti, s. f.; Wint, s. f.).
4. Las estrategias propuestas —diferenciación móvil y local, escala progresiva, interoperabilidad, respuesta ante fugas, soporte cercano y sostenibilidad con evidencia— se consolidaron como guías directas para la definición de los Bounded Contexts y la arquitectura de software.
5. Las cinco entrevistas registradas —dos del segmento PYMES y comercios locales y tres del segmento hogares y familias— aportaron información objetiva y subjetiva fundamental para delimitar las reglas de negocio, los umbrales de flujo volumétrico y los requerimientos de priorización visual de alertas.
6. Se completó con éxito el desarrollo del backend bajo el framework Spring Boot y lenguaje Kotlin, estructurado bajo Clean Architecture y Tactical DDD en dos Bounded Contexts operativos: Alerting (US15, US16) y Device Monitoring (US10, US11, US12).
7. La suite de pruebas unitarias implementada con JUnit 5 alcanzó un 100% de efectividad (pass rate) sobre las reglas de negocio críticas, garantizando la correcta evaluación de anomalías volumétricas sin incurrir en falsos positivos ante flujos transitorios.
8. La solución Web Service fue contenerizada y desplegada exitosamente en producción sobre la plataforma Render, integrando una base de datos relacional PostgreSQL administrada y una interfaz interactiva OpenAPI/Swagger plenamente operativa para el consumo de clientes móviles.

## 5.2. Bibliografía

### 5.2.1. Dominio de negocio y competidores

Badger Meter. (s. f.). *BlueEdge Suite of Scalable Solutions*. https://www.badgermeter.com/blueedge/

Banco Interamericano de Desarrollo. (2025). *Peril and promise: Tackling climate change in Latin America and the Caribbean*. https://publications.iadb.org/publications/english/document/Peril-and-Promise-Tackling-Climate-Change-in-Latin-America-and-the-Caribbean.pdf

Itron. (s. f.). *Smart Water Solutions*. https://emea.itron.com/categories/smart-water-solutions

Ministerio de Vivienda, Construcción y Saneamiento. (2024). *¡Cifra histórica! Casi 600 mil peruanos accedieron al servicio de agua potable durante el último año con obras del MVCS*. https://www.gob.pe/institucion/vivienda/noticias/954978-cifra-historica-casi-600-mil-peruanos-accedieron-al-servicio-de-agua-potable-durante-el-ultimo-ano-con-obras-del-mvcs

Opti. (s. f.). *The Opti Solution*. https://www.optirtc.com/solution

Superintendencia Nacional de Servicios de Saneamiento. (2023). *El buen dato Sunass: El impacto del agua potable y saneamiento en la calidad de vida*. https://www.gob.pe/institucion/sunass/colecciones/47085-el-buen-dato-sunass

Superintendencia Nacional de Servicios de Saneamiento. (2025). *Agua no facturada en el Perú: Un desafío de gestión para las empresas prestadoras de servicios de agua potable*. https://cdn.www.gob.pe/uploads/document/file/8960946/7375591-agua-no-facturada-en-el-peru-un-desafio-de-gestion-para-las-empresas-prestadoras-de-servicios-de-agua-potable.pdf

U.S. Environmental Protection Agency. (2024). *The WaterSense current: Winter 2024*. https://www.epa.gov/watersense/watersense-current-winter-2024

Zipdo. (2025). *Water crisis statistics*. https://zipdo.co/water-crisis-statistics/

Wint. (s. f.). *Commercial Water Management & Leak Prevention Solutions*. https://wint.ai/

### 5.2.2. Métodos y técnicas de ingeniería de software

Driessen, V. (2010). *A successful Git branching model*. https://nvie.com/posts/a-successful-git-branching-model/

Gothelf, J. (s. f.). *Lean UX Canvas*. https://jeffgothelf.com/blog/leanuxcanvas/

Gothelf, J., & Seiden, J. (2021). *Lean UX: Creating great products with agile teams* (3.ª ed.). O'Reilly Media.

Universidad Peruana de Ciencias Aplicadas. (2026). *Trabajo Final 1ACC0238 202620: Rúbrica y lineamientos del proyecto* [Documento del curso].

### 5.2.3. Herramientas y documentación técnica

GitHub. (s. f.). *GitHub documentation*. https://docs.github.com/

Google. (s. f.). *Android Developers documentation*. https://developer.android.com/

## 5.3. Anexos

### Anexo A. Recursos gráficos del análisis competitivo

Los logos utilizados en el landscape corresponden al apartado **2.1.1. Análisis competitivo** del Capítulo II.

![Logo de Badger Meter](../images/competitors/badger-meter.jpg)

![Logo de OptiRTC](../images/competitors/optirtc.jpg)

![Logo de Itron](../images/competitors/itron.jpg)

![Logo de Qlic](../images/competitors/qlic.jpg)

**Nota.** Logotipos reproducidos con fines académicos. Fuentes: Badger Meter (s. f.), Opti (s. f.) e Itron (s. f.); el logotipo de Qlic es elaboración propia.

