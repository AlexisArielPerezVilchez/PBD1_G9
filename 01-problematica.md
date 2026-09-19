# 1. Problemática y justificación

[← Volver al Hito 1](README.md)

---

## 1.1 Introducción

El bienestar materno-fetal durante la gestación es un indicador crítico de salud pública. El
monitoreo de la actividad motora y de la frecuencia cardíaca fetal resulta fundamental para
la detección temprana de complicaciones y la prevención de la mortalidad perinatal.

En el Perú existen desafíos significativos de accesibilidad oportuna a controles prenatales
especializados, que afectan de manera desproporcionada a las gestantes de zonas rurales.
Además, el seguimiento ambulatorio tradicional depende en gran medida de la **percepción
subjetiva** de los movimientos fetales por parte de la madre. Esto evidencia la necesidad
clínica y tecnológica de descentralizar la atención mediante herramientas que brinden
mediciones objetivas y confiables fuera del entorno hospitalario estricto.

---

## 1.2 Magnitud del problema

A nivel mundial, UNICEF estima que en **2021 aproximadamente 1,9 millones de bebés nacieron
sin signos de vida después de las 28 semanas de gestación** [2].

En el Perú, según la ENDES, persiste una brecha entre el ámbito rural y el urbano en el
acceso oportuno al primer control prenatal durante el primer trimestre:

| Ámbito | Primer control prenatal en el primer trimestre |
|---|---|
| Nacional | 80,9 % |
| Urbano | 82,3 % |
| **Rural** | **76,8 %** |

Asimismo, aunque el 87,8 % de las mujeres recibió al menos seis atenciones prenatales, la
disponibilidad de **evaluaciones especializadas entre controles** representa una dificultad
para las gestantes que viven alejadas de los establecimientos de salud [1].

> ⚠️ **Pendiente de verificación.** En los documentos del hito conviven dos versiones de esta
> cifra: ENDES 2024 (76,8 % rural / 82,3 % urbano) en la sección de problema general, y ENDES
> 2023 (76,6 % rural / 82,1 % urbano) en la problemática final y en el PPT. Antes del informe
> final hay que unificar **una sola fuente y un solo año** en los tres documentos.

---

## 1.3 Limitaciones de los métodos actuales

El seguimiento del bienestar fetal requiere evaluar varios parámetros, entre ellos los
movimientos fetales y la frecuencia cardíaca. La evaluación de los movimientos fetales
presenta dificultades por la variabilidad de la percepción materna y por las limitaciones de
los métodos disponibles en el Perú [3] [4].

En establecimientos del primer nivel de atención en zonas rurales:

- **No se dispone de cardiotocógrafo ni de ecógrafo**, ni de personal especializado para su
  operación e interpretación.
- **Entre controles prenatales** —que pueden estar separados por semanas y a horas de
  traslado— la única vigilancia disponible es la percepción materna de movimientos:
  subjetiva, sin registro objetivo y sin criterios claros de alarma.
- **La auscultación con estetoscopio de Pinard** depende de la destreza del operador, no
  genera registro y solo está disponible durante la consulta presencial.
- **Las soluciones wearable reportadas en la literatura** dependen de análisis en la nube o
  de cobertura de telefonía móvil, condiciones no garantizadas en el contexto de uso.

### Fundamento fisiopatológico

La disminución de los movimientos fetales constituye un signo de alarma reconocido de
compromiso fetal. Su mecanismo se explica por la **redistribución del gasto energético**:
ante una insuficiencia placentaria que limita el aporte de oxígeno y nutrientes, el feto
reduce su actividad motora como mecanismo de conservación. Esta reducción se asocia a
restricción del crecimiento intrauterino, oligohidramnios, resultados perinatales adversos y
muerte fetal intrauterina.

---

## 1.4 Necesidad identificada (*need statement*)

> Una forma **no invasiva, de bajo costo, operable sin personal especializado y funcional sin
> conectividad**, de registrar objetivamente los movimientos fetales y la frecuencia cardíaca
> fetal en gestantes del tercer trimestre de zonas rurales del Perú, que oriente la consulta
> temprana ante signos de posible compromiso fetal.

---

## 1.5 Problemática final

En el Perú, las gestantes de zonas rurales y alejadas presentan mayores dificultades para
acceder oportunamente al seguimiento prenatal. El seguimiento del bienestar fetal entre
controles puede verse limitado por la dependencia de la percepción materna de los movimientos
fetales. Investigaciones recientes señalan que la medición objetiva de estos movimientos
continúa siendo un desafío y que existen diferentes estrategias tecnológicas para su
monitorización.

Ante esta situación, **se propone desarrollar un dispositivo biomédico no invasivo** que
integre sensores para detectar los movimientos fetales y obtener la frecuencia cardíaca
fetal. Los datos se registran localmente y pueden transmitirse a una aplicación móvil que
permita visualizarlos y almacenarlos, generando una **orientación de seguimiento** que indique
cuándo sería recomendable acudir a un profesional de la salud.

Como trabajo futuro se contempla incorporar la **medición de la presión arterial materna**,
con el fin de contribuir a la prevención de preeclampsia, así como el registro de la
**temperatura superficial abdominal materna** como parámetro complementario de seguimiento.

---

## 1.6 Delimitación del alcance

- El sistema **registra y cuantifica**; no interpreta patrones cardiotocográficos
  (variabilidad, aceleraciones, desaceleraciones), lo cual corresponde a evaluación
  especializada.
- La salida es un **indicador orientativo con recomendación de consulta**, nunca un
  diagnóstico ni un pronóstico.
- La validación del presente proyecto se realiza en **banco de pruebas con modelo físico
  (phantom)**; los ensayos con gestantes quedan como trabajo futuro sujeto a aprobación de
  comité de ética.

### Consideración ética relevante

Los ensayos clínicos de gran escala sobre concientización de movimientos fetales basados en
percepción materna **no han demostrado reducción significativa de la mortalidad fetal**. El
presente sistema aborda una dimensión distinta: la obtención de un registro **objetivo y
reproducible** en un contexto donde actualmente no existe vigilancia alguna entre controles
prenatales.

---

## Bibliografía

[1] Instituto Nacional de Estadística e Informática (INEI). (2025). *Perú: Encuesta Demográfica y de Salud Familiar – ENDES 2024*.

[2] UNICEF. *A Neglected Tragedy: The global burden of stillbirths*. UNICEF DATA.

[3] World Health Organization. (2025). *WHO recommendations on maternal health: guidelines approved by the WHO Guidelines Review Committee*. https://www.ncbi.nlm.nih.gov/books/NBK615644/

[4] American College of Obstetricians and Gynecologists (ACOG). (2021). *Indications for Outpatient Antenatal Fetal Surveillance*. https://www.acog.org/clinical/clinical-guidance/committee-opinion/articles/2021/06/indications-for-outpatient-antenatal-fetal-surveillance

---

[← Volver al Hito 1](README.md) · [Siguiente: Estado del arte →](02-estado-del-arte.md)
