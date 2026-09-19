# 2. Estado del arte

[← Volver al Hito 1](README.md)

La revisión se organiza en las cuatro fuentes exigidas por la rúbrica: artículos académicos,
patentes, revistas de catálogos y páginas de fabricantes.

---

## 2.1 Artículos académicos

Se analizaron en profundidad seis publicaciones que cubren las dos cadenas de medición del
sistema (movimiento fetal y frecuencia cardíaca fetal) y las estrategias de discriminación de
artefactos.

| # | Tema | Aporte al proyecto |
|---|---|---|
| 1 | Sistema wearable no invasivo de fabricación propia con algoritmo híbrido para reconocimiento de movimiento fetal (Delay et al., 2021) | Referencia de arquitectura de bajo costo fabricada en laboratorio; valida la viabilidad de un sistema construido fuera de la industria |
| 2 | Electrocardiografía fetal no invasiva: significado electrofisiológico, procedimientos de registro y técnicas de procesamiento (Agostinelli et al., 2015) | Fundamenta el **descarte del fECG** frente al fPCG: el fECG exige electrodos, preparación de piel y separación de la señal materna, poco viable en contexto rural |
| 3 | Evaluación de un prototipo en fase inicial de un dispositivo portátil económico y no intrusivo para detección domiciliaria de movimientos fetales y sufrimiento fetal (Mohamed et al., 2024) | **Paper conceptualmente más cercano**; sus debilidades (dependencia de la nube, sensor único, sin canal de referencia) son precisamente nuestros diferenciadores |
| 4 | Reconocimiento automático de movimientos fetales a partir de datos de acelerometría multicanal (Mesbah et al., 2021) | Justifica la arquitectura **multicanal** y el tratamiento de la señal por ventanas |
| 5 | Rendimiento de un sistema acústico portátil para la discriminación de movimientos fetales (Lai et al., 2018) | Rango de duración de eventos de movimiento fetal (**0,1 a 3 s**), usado como criterio de la lógica de decisión |
| 6 | Detección de patadas fetales mediante acelerómetros llevados en el cuerpo durante el embarazo (Altini et al., 2016) | **Valida la configuración de sensores adoptada**: número y posicionamiento de acelerómetros, y uso de un canal de referencia para artefactos maternos |

> 📌 **Pendiente.** Los PDF completos están en el material del curso. Para el informe final hay
> que redactar las referencias completas en formato IEEE (autores, revista, volumen, páginas,
> DOI) y verificar el año exacto de cada una.

**Conclusión de la revisión:** el problema del monitoreo fetal domiciliario está activamente
investigado, pero las soluciones reportadas comparten tres limitaciones recurrentes —
dependencia de conectividad, ausencia de canal de referencia para artefactos maternos, y
medición de un solo parámetro — que definen el espacio de oportunidad de este proyecto.

---

## 2.2 Patentes

### Patente 1 — KRIYA: dispositivo portátil para monitorear la salud del feto

| Campo | Dato |
|---|---|
| Número | **WO2020194350A1** |
| Autor | S. Kapil |
| Fecha | 01/10/2020 |

Dispositivo portátil orientado al monitoreo de la salud fetal.

### Patente 2 — Wearable device for monitoring fetus health

| Campo | Dato |
|---|---|
| Número | **US20180368753A1** |
| Autor | Yin Bin |
| Fecha | 27/12/2018 |

Dispositivo vestible para monitoreo de la salud fetal.

> 📌 **Pendiente.** Incorporar las figuras de ambas patentes (las de la solicitud publicada) en
> `img/` y describir en el informe qué reivindicaciones cubren, para delimitar el espacio de
> diseño libre del proyecto.

---

## 2.3 Revistas de catálogos

### Bloomlife (EE. UU.)

Dispositivo wearable de uso prescriptivo, aprobado por la FDA, diseñado para el monitoreo
materno-fetal remoto desde el hogar o la clínica. Utiliza sensores no invasivos adheridos al
abdomen mediante un parche, que registran de forma continua la frecuencia cardíaca fetal y
materna, así como la actividad uterina. Los datos se transmiten de forma inalámbrica a una
plataforma en la nube, permitiendo que el personal de salud revise la información y realice
pruebas no estresantes (NST) a distancia.

| Parámetro | Detalle |
|---|---|
| Parámetros medidos | Frecuencia cardíaca fetal, frecuencia cardíaca materna, actividad uterina |
| Tipo de sujeción | Parche adhesivo sobre el abdomen |
| Conectividad | Inalámbrica, con envío a plataforma en la nube |
| Uso | Prescriptivo (bajo indicación médica) |

### INVU by Nuvo (Israel)

Monitor materno-fetal que mide y muestra de forma no invasiva la frecuencia cardíaca fetal
(FCF), la frecuencia cardíaca materna (FCM) y la actividad uterina (AU). La banda de sensores
*INVU Sensor Band* captura las señales del electrocardiograma fetal y materno mediante
electrodos en la superficie abdominal, así como las señales del **fonocardiograma** fetal y
materno mediante sensores acústicos de superficie. Indicado desde la semana 32 de gestación en
embarazo único.

| Parámetro | Detalle |
|---|---|
| Parámetros medidos | FCF, FCM, actividad uterina (contracciones) |
| Sensores incorporados | Bioseñal (ECG), movimiento, acústicos |
| Tipo de sujeción | Cinturón autoaplicable sobre el abdomen |
| Procesamiento | Basado en la nube, con IA/ML |
| Uso | Prescriptivo, autoaplicado por la paciente |
| Indicación | Gestantes desde la semana 32, embarazo único |

---

## 2.4 Páginas de fabricantes

### Novii Wireless Patch System Fetal Monitor — GE HealthCare

Sistema de monitoreo fetal inalámbrico por parche, de uso hospitalario. Representa la
referencia de desempeño del segmento clínico profesional, contra el cual se contrasta el
posicionamiento de costo y contexto del presente proyecto.

🔗 https://www.gehealthcare.com — *Novii Wireless Patch System Fetal Monitor*

---

## 2.5 Diferenciación respecto al estado del arte

Esta tabla resume por qué el sistema propuesto no es una réplica de lo existente:

| Aspecto | Sistemas reportados | **Sistema propuesto** |
|---|---|---|
| Parámetros medidos | Mayoritariamente movimiento fetal de forma aislada | Movimiento fetal **y** FCF de forma integrada |
| Arquitectura de sensado | Sensor único, o múltiples sensores sin canal de referencia | Dos sensores abdominales **más canal de referencia inercial externo** |
| Procesamiento | Dependiente de servicios en la nube o de cobertura celular | **Íntegramente local**, con prioridad fuera de línea |
| Contexto de diseño | Uso doméstico individual en entornos con infraestructura | **Uso compartido en establecimiento de primer nivel**, con desinfección entre pacientes |
| Validación | En algunos casos, exclusivamente por simulación | **Banco de pruebas físico** con verdad de referencia y estudio de ablación |

Los tres diferenciadores centrales del proyecto son:

1. **Integración bimodal** con arquitectura multicanal y sensor de referencia.
2. **Procesamiento en el borde, sin nube ni GSM** — offline-first.
3. **Diseño para uso compartido en puestos de salud rurales**: desinfectable, con interfaz para
   usuarios de baja alfabetización digital.

---

## Referencias de esta sección

[5] Bloomlife. *Bloomlife MFM-Pro*. https://www.bloom-life.com/services

[6] Nuvo Group. *Remote fetal monitoring: Innovative care solutions*. https://www.nuvocares.com/solutions

[7] GE HealthCare. *Novii Wireless Patch System Fetal Monitor*.

---

[← Anterior: Problemática](01-problematica.md) · [Siguiente: Lista de exigencias →](03-lista-de-exigencias.md)
