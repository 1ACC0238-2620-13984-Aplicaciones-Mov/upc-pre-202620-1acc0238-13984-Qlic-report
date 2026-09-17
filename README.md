# Qlic — Project Report

Informe del trabajo final del curso **Aplicaciones para Dispositivos Móviles**
(1ACC0238, NRC 13984), Universidad Peruana de Ciencias Aplicadas.

## Proyecto

Qlic es una solución móvil conectada con dispositivos IoT para monitorear el
consumo de agua, detectar fugas y entregar alertas y reportes útiles a PYMES,
comercios locales, hogares y familias.

## Equipo

- Avila Palacios, Aaron Alexander — `u201823654`
- Briceño Llanos, Ayrton Omar — `u202311077`
- Conde Huashuayo, Sebasthian Alex — `u20241e356`
- Condori Lozano, Alessandro Ramiro — `u20211a118`

## Informe

La versión integrada del informe se encuentra en `master`:

- [Carátula, registro de versiones y Student Outcome](report/caratula.md)
- [Capítulo I: Introducción](report/chapter-1.md)
- [Capítulo II: Requirements Development and Software Solution Design](report/chapter-2.md)
- [Capítulo V: Conclusiones, Bibliografía y Anexos](report/chapter-5.md)

## Ramas

| Rama | Contenido | Estado |
|---|---|---|
| `master` | Informe integrado y versión principal del repositorio | Actualizada |
| `feature/caratula` | Carátula, registro de versiones, Student Outcome y objetivos SMART | Integrada en `master` |
| `feature/chapter-1` | Capítulo I: Introducción, perfiles, problemática y Lean UX | Integrada en `master` |
| `feature/chapter-2` | Capítulo II: competidores, entrevistas, needfinding, requisitos y diseño de la solución | Integrada en `master` |
| `feature/chapter-5` | Capítulo V: conclusiones, bibliografía y anexos | Integrada en `master` |
| `develop` | Rama de integración y preparación de cambios | Disponible |

Las ramas de capítulo se trabajan de forma independiente y se integran en
`master` después de revisar el contenido. La integración utiliza GitFlow y
mensajes de commit con la convención Conventional Commits.

## Estructura del repositorio

```text
report/
├── caratula.md
├── chapter-1.md
├── chapter-2.md
└── chapter-5.md
images/
├── c4/
├── competitors/
├── interviews/
├── journey_map/
├── needfinding/
├── uml/
└── ...
```

Las imágenes utilizadas por cada capítulo se conservan dentro de `images/` y
se referencian desde los documentos del informe.

## Revisión de la versión integrada

La versión actual de `master` fue verificada para confirmar que:

- los cuatro capítulos están presentes;
- las imágenes y enlaces locales del contenido de `report/` existen;
- el capítulo 2 mantiene tres entrevistas registradas;
- no hay referencias a integrantes retirados ni marcadores de plantilla en
  los capítulos finales.

## Repositorio remoto

[Repositorio de Qlic en GitHub](https://github.com/1ACC0238-2620-13984-Aplicaciones-Mov/upc-pre-202620-1acc0238-13984-Qlic-report)
