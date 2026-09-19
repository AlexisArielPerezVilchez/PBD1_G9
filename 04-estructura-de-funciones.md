# 4. Estructura de funciones óptima

[← Volver al Hito 1](README.md)

Esta sección cubre los tres componentes evaluados por la rúbrica: **caja negra** (1 pt),
**secuencia de operaciones** (1 pt) y **estructura de funciones** (2 pts).

---

## 4.1 Caja negra (*black box*)

El modelo de caja negra representa el sistema **sin mostrar su funcionamiento interno**,
indicando únicamente las entradas de energía y señal que recibe, y las salidas de energía y
señal que genera.

![Caja negra del sistema](img/black-box.svg)

*Figura 1. Caja negra del Sistema de Monitoreo Fetal Portátil.*

### Entradas

| Tipo | Entrada |
|---|---|
| Energía | Energía eléctrica (batería 18650) |
| Energía | Energía mecánica — vibración de la pared abdominal |
| Energía | Energía acústica — tonos cardíacos fetales |
| Energía | Energía térmica — calor corporal |
| Señal | Señal de activación (pulsador) |
| Señal | Señal de configuración (app móvil) |

### Salidas

| Tipo | Salida |
|---|---|
| Energía | Energía térmica disipada |
| Energía | Energía luminosa — indicador tipo semáforo |
| Señal | Conteo de eventos compatibles con movimiento fetal |
| Señal | FCF promedio (lpm) |
| Señal | Alerta orientativa para la gestante |
| Señal | Registro de sesión transferido por BLE |

### Notación

Siguiendo la notación estándar del modelo de caja negra, **las líneas continuas representan
flujo de energía** y **las líneas punteadas, flujo de información o señal**. El contorno
discontinuo delimita la frontera del sistema.

---

## 4.2 Secuencia de operaciones

El cinturón sigue un ciclo de **captación → filtrado → validación → cálculo → resultado**. La
validación es la etapa crítica: distingue si el evento registrado corresponde a movimiento
fetal o a un artefacto, antes de contabilizarlo.

![Secuencia de operaciones](img/secuencia-de-operaciones.svg)

*Figura 2. Secuencia de operaciones del sistema.*

### Árbol de reglas de decisión

| N.º | Criterio | Fundamento |
|:---:|---|---|
| 1 | ¿Existe actividad inercial significativa en una ventana de ±0,5 s? | En caso afirmativo, el evento se descarta por corresponder a movimiento materno |
| 2 | ¿La amplitud es equivalente en ambos sensores abdominales? | Un evento **global** sugiere artefacto; un evento **localizado** sugiere origen fetal |
| 3 | ¿La duración se encuentra entre 0,1 y 3 s? | Duraciones fuera de rango corresponden a ruido impulsivo o a desplazamiento del cinturón |
| 4 | Si supera los criterios anteriores | El evento se contabiliza como compatible con movimiento fetal y se registra |

> **Decisión de diseño.** La lógica se implementa mediante **reglas explícitas y no como modelo
> de caja negra**. Esto responde a un requisito de trazabilidad: cada evento contabilizado puede
> justificarse indicando qué criterios satisfizo, lo cual es indispensable tanto para la defensa
> técnica del proyecto como para una eventual evaluación clínica.

### Por qué dos sensores piezoeléctricos y no uno

La razón **no es redundancia sino obtención de información espacial**. Un movimiento fetal es
un evento *localizado*: se manifiesta con amplitud elevada en el sensor más próximo y atenuada
en el distante. Un movimiento materno es un evento *global*: aparece simultáneamente y con
amplitud similar en ambos. Esta diferencia constituye el primer criterio de discriminación.

### Clasificación de salida

| Indicador | Condición | Mensaje al usuario |
|---|---|---|
| 🟢 Verde | Conteo dentro del patrón habitual y FCF entre 110 y 160 lpm | Sesión sin hallazgos; continuar seguimiento habitual |
| 🟡 Ámbar | Conteo reducido respecto a sesiones previas o señal de calidad insuficiente | Repetir la medición; si persiste, acudir al establecimiento de salud |
| 🔴 Rojo | FCF fuera del rango de 110 a 160 lpm o ausencia de eventos en la sesión | Acudir al establecimiento de salud |

Los mensajes se formulan **exclusivamente como recomendación de consulta**. En ningún caso se
emplea terminología diagnóstica ni se comunica una interpretación clínica del hallazgo.

---

## 4.3 Estructura de funciones

La solución se desglosa en **cinco dominios funcionales** que interactúan entre sí. El flujo de
la señal fisiológica recorre los cuatro dominios principales en secuencia, mientras que la
gestión de energía alimenta transversalmente a todos.

![Estructura de funciones](img/estructura-de-funciones.svg)

*Figura 3. Estructura de funciones por dominios.*

### Dominio mecánico

1. Adaptación al abdomen
2. Sujeción y posicionamiento de sensores
3. Transmisión de vibraciones fetales

### Dominio electrónico

1. Captación y conversión de señales
2. Acondicionamiento y filtrado
3. Digitalización de señales

### Dominio de control

1. Procesamiento y extracción de características
2. Discriminación fetal – materna
3. Estimación de FC fetal

### Dominio integrado

1. Integración de resultados
2. Registro e historial de sesiones
3. Comunicación, visualización y alertas

### Gestión de energía

1. Almacenamiento y protección de energía
2. Regulación de alimentación
3. Distribución de energía al sistema

---

### Acoplamiento entre dominios

- **Señal fisiológica** (línea azul continua): mecánico → electrónico → control → integrado.
  Es el recorrido del movimiento fetal y de los tonos cardíacos desde la pared abdominal hasta
  el resultado.
- **Señal de control** (línea naranja punteada): el dominio de control retroalimenta al dominio
  electrónico con los parámetros de adquisición y los umbrales adaptativos.
- **Energía** (línea negra continua): la gestión de energía alimenta los cuatro dominios.

### Ejecución concurrente

Las dos cadenas de medición son **independientes a nivel de hardware**: la cadena de movimiento
emplea el bus **I2C** y la cadena de FCF el bus **I2S**, por lo que no comparten líneas de
comunicación ni se interfieren. El ESP32 las ejecuta **en paralelo sobre sus dos núcleos**
mediante tareas de FreeRTOS, de modo que ninguna interfiere con los requisitos temporales de la
otra. Esto permite además desarrollarlas y depurarlas por separado.

---

## Archivos de las figuras

Los tres diagramas están en [`img/`](img/) en formato **SVG**: se insertan en Word y PowerPoint
sin pérdida de calidad a cualquier tamaño, y se pueden editar con Inkscape si hay que corregir
un texto.

---

[← Anterior: Lista de exigencias](03-lista-de-exigencias.md) · [Siguiente: Gantt →](05-gantt.md)
