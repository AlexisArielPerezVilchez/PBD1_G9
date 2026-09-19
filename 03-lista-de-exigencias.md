# 3. Lista de exigencias

[← Volver al Hito 1](README.md)

Elaborada según la metodología **Pahl & Beitz**, con clasificación **E** (Exigencia, de
cumplimiento obligatorio) y **D** (Deseo, deseable pero no vinculante).

---

## Encabezado del documento

| Campo | Contenido |
|---|---|
| **Proyecto** | Sistema wearable no invasivo y de bajo costo para el registro objetivo de movimientos fetales y la estimación de la frecuencia cardíaca fetal en gestantes del tercer trimestre, como herramienta de apoyo al seguimiento prenatal en zonas con acceso limitado a atención especializada |
| **Cliente** | **Usuaria final:** gestantes del tercer trimestre (28–40 semanas).<br>**Usuario operador:** personal de salud de establecimientos del primer nivel de atención en zonas rurales del Perú |
| **Edición** | Revisión 1 |
| **Fecha** | 11/09/2026 |
| **Elaborado por** | Alexis Ariel Pérez Vílchez (A.P) · Juan Carlos Lugo Rodríguez (J.L) · Taline Dione Llactahuamán Díaz (T.L) · Alejandra Abigail Araoz Miranda (A.A) · Ana Paula Cornejo Salazar (P.C) |

---

## Lista de exigencias — Revisión 1

| Fecha | E/D | Descripción | Responsable |
|---|:---:|---|---|
| 11/09/2026 | **E** | **Función principal.** Registrar de forma no invasiva y objetiva los eventos compatibles con movimiento fetal y estimar la frecuencia cardíaca fetal (FCF) promedio, en sesiones de reposo de 15 a 25 minutos, en gestantes del tercer trimestre (≥ 28 semanas de gestación). | Todos |
| 11/09/2026 | **D** | **Función secundaria.** Registrar la temperatura superficial abdominal materna como dato contextual complementario de la sesión. No constituye medición de temperatura fetal ni parámetro diagnóstico. | Todos |
| 11/09/2026 | **D** | **Función secundaria.** Registrar la presión arterial de la madre gestante como dato contextual complementario de la sesión. No constituye parámetro de diagnóstico. | Todos |
| 11/09/2026 | **E** | **Geometría.** Cinturón ajustable a perímetro abdominal de **75 a 120 cm**, con ancho de banda de **8 a 12 cm** para distribuir la presión de sujeción. Peso total del sistema portátil **≤ 400 g** (sistema y textil). Espesor máximo de los módulos encapsulados: **25 mm**, para permitir su uso bajo ropa holgada. Cámara acústica del canal de FCF: diámetro de **35 a 45 mm** y cavidad interna de **15 a 20 mm** de altura. | Todos |
| 11/09/2026 | **E** | **Cinemática.** El sistema es de uso estático: la medición se realiza con la gestante en reposo, sentada o en decúbito lateral izquierdo. No está diseñado para monitoreo ambulatorio continuo. El sistema debe registrar eventos vibratorios transitorios de duración entre **0,1 y 3 s**, correspondientes al rango de movimientos fetales reportados en la literatura (Altini et al., 2016; Lai et al., 2018). El sensor acústico debe permitir reposicionamiento manual sobre el abdomen (fijación por velcro), dado que el foco de auscultación varía con la posición fetal. | Todos |
| 11/09/2026 | **E** | **Fuerzas.** La sujeción debe ejercer una presión uniforme suficiente para mantener el acoplamiento sensor-piel sin generar compresión abdominal ni incomodidad, mediante banda elástica con cierre regulable tipo velcro, sin hebillas rígidas sobre el abdomen. Los sensores deben montarse sobre base flexible de silicona, sin bordes ni aristas vivas en contacto con la piel. El sistema debe soportar caída accidental desde **1 m** sobre superficie dura sin pérdida de funcionalidad, considerando su uso en campo. | Todos |

---

## Filas propuestas para completar la Revisión 2

> ⚠️ **Estas filas no forman parte de la Revisión 1 entregada.** Están redactadas a partir de
> las especificaciones ya definidas en el [documento técnico](../docs/documento-tecnico.md) y
> quedan **a revisión del equipo** antes de incorporarlas. La rúbrica valora que las exigencias
> sean *claras, medibles y relacionadas con la solución propuesta*; las categorías de Pahl &
> Beitz que aún no están cubiertas son las que siguen.

| E/D | Categoría | Descripción propuesta |
|:---:|---|---|
| **E** | **Energía** | Alimentación autónoma por batería de ion-litio 18650 con módulo de carga TP4056 por USB 5 V, compatible con cargadores convencionales y sistemas fotovoltaicos. Autonomía mínima para **8 sesiones consecutivas** de 30 min sin recarga. Operación sin conexión a red eléctrica durante la medición. |
| **E** | **Señales** | Adquisición del canal de movimiento a **200 muestras/s por canal** con resolución de **16 bits** (ADS1115), banda útil de **1 a 20 Hz**. Adquisición del canal acústico a **8 kHz** por I2S, banda útil de **20 a 110 Hz**. Rango de estimación de FCF: **110 a 160 lpm**. |
| **E** | **Seguridad** | Sensores estrictamente **pasivos**: no inyectan energía eléctrica, acústica ni térmica hacia la gestante ni hacia el feto. Protección de entrada frente a sobretensiones del elemento piezoeléctrico. Sin transmisión inalámbrica activa durante la adquisición. |
| **E** | **Ergonomía / Uso** | Operación mediante **un único pulsador** y un indicador luminoso tipo semáforo, sin dependencia de teléfono móvil, adecuado a usuarios con baja alfabetización digital. Rutina de autodiagnóstico de sensores al iniciar la sesión. |
| **E** | **Material / Mantenimiento** | Superficies en contacto con la piel desinfectables entre pacientes (uso compartido en establecimiento de salud). Fundas y encapsulados removibles. |
| **E** | **Costos** | Costo de materiales **≤ S/ 500** por unidad de prototipo. *Valor actual estimado: ≈ S/ 231.* |
| **E** | **Control** | Lógica de decisión implementada mediante **reglas explícitas y trazables**, no como modelo de caja negra: cada evento contabilizado debe poder justificarse indicando qué criterios satisfizo. |
| **E** | **Plazos** | Prototipo funcional validado en banco de pruebas antes del **05/12/2026** (Hito 4). |

---

## Criterio de diseño transversal: prioridad sobre el falso positivo

En esta aplicación, el **falso positivo es el error de mayor consecuencia clínica**. Un conteo
sobreestimado puede transmitir falsa tranquilidad ante una disminución real de la actividad
fetal, retrasando la consulta.

Por ello, todos los parámetros de la lógica de decisión se ajustan priorizando la minimización
de falsos positivos, **incluso a costa de una ligera reducción de la sensibilidad**. Este
criterio atraviesa varias exigencias y debe declararse explícitamente en el informe.

---

## Criterios de aceptación cuantitativos

| Métrica | Valor exigido |
|---|---|
| Sensibilidad de detección de movimiento | ≥ 80 % |
| Tasa de falsos positivos | ≤ 10 % |
| Error de estimación de FCF (rango 110 a 160 lpm) | ≤ ± 5 lpm |

Los valores se establecen en referencia al desempeño reportado por sistemas equivalentes en la
literatura especializada.

---

[← Anterior: Estado del arte](02-estado-del-arte.md) · [Siguiente: Estructura de funciones →](04-estructura-de-funciones.md)
