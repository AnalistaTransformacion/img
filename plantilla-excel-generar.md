# Especificación y Plantilla de Estructura de Excel

> **Documento de Referencia Técnica para el Agente Copilot**  
> Este documento define la estructura exacta, columnas, formatos y reglas de generación de los libros de Microsoft Excel que el agente debe construir en la **Etapa Previa** (preparación y campo) y en la **Etapa Posterior** (tabulación y análisis).

---

## 1. Libros de la Etapa Previa (Antes de Campo)

En la fase de diseño, el agente genera los archivos que se llevarán a campo y que configurarán Microsoft Forms.

---

### 1.1. Estructura de la Hoja: `Instrucciones`
Esta hoja formaliza el protocolo operativo del estudio para el equipo de campo, encuestadores y supervisores.

* **Columnas obligatorias**:
  1. `Tema`: Parámetro metodológico o directriz.
  2. `Instrucción`: Descripción operativa detallada y no ambigua.

#### Diccionario de Temas y Contenido Estándar:

| Tema | Instrucción Estándar |
| :--- | :--- |
| **Objetivo** | «Evaluar [N] propuestas/muestras de [categoría] en [público objetivo] para identificar la opción con mayor potencial, aceptación e intención de compra.» |
| **Público** | «Personas de [rango edad] años, residentes en [ciudades], estratos [estratos/NSE], responsables de compra o consumo en el hogar.» |
| **Admisión** | «Consumidores o compradores habituales de la categoría en los últimos [X] meses. Quienes no cumplan o trabajen en publicidad, alimentos o competencia finalizan la encuesta.» |
| **Diseño** | «Evaluación monádica secuencial: presentar una muestra/concepto completo a la vez y aplicar su bloque completo antes de pasar al siguiente.» |
| **Muestra** | «[N_Total] entrevistas útiles: [N_Ciudad] por ciudad. Cuotas balanceadas por edad y nivel socioeconómico.» |
| **Reclutamiento**| «Reclutar 10-15% adicional ([N_Extra] contactos) para cubrir filtros, ausencias y deserciones. Aplicar consentimiento informado.» |
| **Conceptos / Muestras** | «Identificar con códigos ciegos aleatorios de 3 dígitos (ej. 382, 507, 941) o letras neutras. No revelar marcas reales ni expectativas.» |
| **Rotación** | «Seguir estrictamente la fila asignada por ciudad e ID de participante. Cada muestra/concepto debe aparecer el mismo número de veces en cada posición ordinal.» |
| **Aplicación** | «Mostrar las muestras en el orden exacto de Posición 1, Posición 2, etc. Realizar pausa obligatoria con agua neutra entre muestras en pruebas físicas.» |
| **Medición** | «Evaluación hedónica (1-7), escalas JAR (1-5) con justificación obligatoria del porqué, CATA, intención de compra (1-5) y preguntas abiertas de diagnóstico.» |
| **Escalas** | «Agrado: 1-7 (1 = Me disgusta mucho, 7 = Me gusta mucho). JAR: 1-5 (3 = Justo como me gusta / ideal). Intención: 1-5 con anclas verbales completas.» |
| **Piloto** | «Realizar prueba piloto con 5 personas antes de liberar campo para verificar comprensión, saltos condicionales y visualización en dispositivos móviles.» |
| **Privacidad** | «Consentimiento informado obligatorio y aviso de tratamiento de datos personales aprobado. Evitar recolectar datos personales no esenciales.» |
| **Control de calidad** | «Auditar duplicados, entrevistas atípicamente rápidas, inconsistencias en filtros demográficos y cumplimiento estricto de cuotas.» |
| **Duración estimada** | «[X-Y] minutos según número de muestras y preguntas abiertas.» |

---

### 1.2. Estructura de la Hoja: `Rotacion`
Define el orden balanceado de presentación (Cuadrado Latino) para cada evaluador, neutralizando el sesgo de primacía.

* **Columnas obligatorias**:
  1. `Ciudad`: Ciudad donde se aplica la entrevista.
  2. `ID_Participante`: Identificador alfanumérico único (ej. `BOG-001`, `MED-001`, `CAL-001`, `BAQ-001`).
  3. `Estrato_Cuota`: Nivel socioeconómico o estrato de cuota (ej. `2`, `3`, `4`).
  4. `Posición_1`: Código de 3 dígitos o nombre ciego de la muestra/concepto a evaluar en 1.er lugar.
  5. `Posición_2`: Muestra/concepto a evaluar en 2.º lugar.
  6. `Posición_3`: Muestra/concepto a evaluar en 3.er lugar.
  7. `Posición_N`: Posiciones sucesivas según el número total de muestras evaluadas.

#### Reglas de Construcción de la Rotación:
* En cada ciudad y para cada cuota demográfica, **cada muestra debe aparecer exactamente el mismo número de veces en cada posición ordinal**.
* Si el número de participantes no es múltiplo exacto del número de muestras, el agente debe repartir las posiciones con la máxima uniformidad posible y dejar constancia en la hoja de instrucciones.

---

### 1.3. Estructura de la Hoja: `Preguntas_Forms`
Estructura tabular lista para copiar y parametrizar en Microsoft Forms (o mediante automatizaciones de Copilot).

* **Columnas obligatorias**:
  1. `ID`: Identificador alfanumérico secuencial (`P001`, `P002`, `P003`...).
  2. `Sección`: Bloque temático (`Consentimiento`, `Demográfico`, `Hábitos y uso`, `Frecuencia de compra`, `[Muestra/Concepto A]`, `Ranking`, `Cierre`).
  3. `Texto`: Redacción exacta y neutral del enunciado de la pregunta.
  4. `Objetivo`: Meta de investigación o función analítica del campo.
  5. `Tipo Forms`: Tipo de control nativo en Forms: `Opción`, `Texto`, `Calificación`, `Clasificación` o `Fecha`.
  6. `Opciones / escala`: Valores admisibles, niveles o anclas verbales:
     * Para `Calificación`: Especificar número de niveles y anclas (ej. `7 niveles; 1 = Me disgusta mucho; 7 = Me gusta mucho` o `5 niveles; 1 = Mucho menos de lo que me gusta; 3 = Justo como me gusta; 5 = Mucho más de lo que me gusta`).
     * Para `Opción`: Lista separada por punto y coma (ej. `Bogotá; Medellín; Cali; Barranquilla; Otra`).
  7. `Obligatoria`: `Sí` o `No`.
  8. `Salto`: Lógica condicional de bifurcación (ej. `No -> finalizar`, `Otra -> finalizar`, `Sí -> preguntar cuál`).
  9. `Variable`: Nombre técnico estandarizado para la base de datos relacional (ej. `Agrado_Global`, `JAR_Dulzor`, `Justificacion_JAR`, `Intencion_Compra`).
  10. `Observaciones`: Instrucciones para el encuestador o configuración técnica en Forms (ej. `Activar varias respuestas`, `Insertar imagen del anaquel`, `Analizar media y Top-2 Box`).

---

## 2. Libro de la Etapa Posterior: `Ejemplo Tabulación - Formato.xlsx`

Cuando el usuario adjunte la exportación de respuestas desde Forms, el agente construirá este libro consolidado compuesto por 7 hojas dinámicas:

```
+-----------------------------------------------------------------------------------+
|               ARQUITECTURA DEL EXCEL MAESTRO DE RESULTADOS                        |
|                                                                                   |
|  1. Sheet1          : Base de datos cruda pegada tal cual de Forms.               |
|  2. Dashboard_Data  : Hoja oculta con tablas de cálculo dinámico por fórmulas.    |
|  3. Dashboard       : Tablero ejecutivo con KPIs, 15 gráficos y lectura dinámica. |
|  4. Ranking Personas: Matriz participante x muestra con posiciones asignadas.     |
|  5. Base_Larga      : Formato largo (1 fila por consumidor-muestra evaluada).     |
|  6. Analisis_Data   : Cruces demográficos, correlaciones de Pearson y medias.     |
|  7. Verbatims       : Matriz de respuestas abiertas codificadas por tema y ánimo. |
+-----------------------------------------------------------------------------------+
```

### 2.1. Hoja `Sheet1`
* Almacena las respuestas crudas de Microsoft Forms.
* Incluye encabezados que corresponden unívocamente a los campos `Variable` definidos en la hoja `Preguntas_Forms`.
* Incluye de forma mandatoria la columna `Justificación_JAR` para registrar los motivos de las calificaciones JAR.

### 2.2. Hoja `Dashboard_Data` (Oculta)
* Contiene fórmulas dinámicas vinculadas a `Sheet1`:
  * Fórmulas de Promedio: `=PROMEDIO.SI.CONJUNTO(...)` para medias de agrado por muestra y atributo.
  * Fórmulas de Top-2 Box: Porcentaje de calificaciones 6 y 7 en escala hedónica o 4 y 5 en intención:
    $$\text{\% Top-2 Box} = \frac{\text{CONTAR.SI.CONJUNTO}(\text{Rango}, ">=6")}{\text{CONTAR}(\text{Rango})}$$
  * Fórmulas de Penalización JAR: Porcentaje de consumidores en 'Poco' (1-2), 'Ideal' (3) y 'Mucho' (4-5).
  * Fórmulas de Ranking: Frecuencia de selección en 1.er lugar.

### 2.3. Hoja `Dashboard`
Tablero de control ejecutivo para toma de decisiones:
* **Tarjetas KPI principales**:
  * Muestra / Concepto Ganador.
  * Base total de evaluadores ($n$).
  * Promedio de agrado global ponderado (/7).
  * % Top-2 Box general acumulado.
* **Bloque de Visualización (15 Gráficos Oficiales)**:
  1. Dona demográfica de edad (máximo 4 categorías).
  2. Barras de nivel socioeconómico / estrato.
  3. Barras de marcas consumidas en la categoría (ordenadas de mayor a menor mención).
  4. Barras de canales habituales de compra.
  5. Columnas de frecuencia de consumo.
  6. Columnas de frecuencia de compra.
  7. Barras apiladas 100% de agrado global por muestra con línea de media (1-7).
  8. Barras apiladas 100% de apariencia visual por muestra.
  9. Barras apiladas 100% de aroma/olor por muestra.
  10. Barras apiladas 100% de sabor general por muestra.
  11. Barras apiladas 100% de textura/consistencia por muestra.
  12. Gráfico divergente JAR de atributos clave (alerta visual si 'Poco' o 'Mucho' $\ge 20\%$).
  13. Barras de términos CATA seleccionados por muestra.
  14. Barras apiladas de intención de compra (Top-2 box).
  15. Barras de preferencia y ranking (% en 1.er lugar).
* **Lectura Ejecutiva Automatizada**: Párrafos concatenados dinámicamente con fórmulas de Excel (`=CONCATENAR(...)` o `TEXTO`) que redactan el diagnóstico cuantitativo automáticamente.

### 2.4. Hoja `Base_Larga`
Reestructura las columnas de `Sheet1` en una tabla normalizada donde cada fila representa una evaluación única de una muestra por un consumidor:
* Columnas: `ID_Consumidor`, `Ciudad`, `Edad`, `NSE_Estrato`, `Codigo_Muestra`, `Orden_Evaluacion`, `Agrado_Global`, `JAR_Color`, `JAR_Aroma`, `JAR_Sabor`, `JAR_Textura`, `Justificacion_JAR`, `Intencion_Compra`.

### 2.5. Hoja `Analisis_Data`
Tablas de contingencia y estadística inferencial descriptiva:
* Tablas cruzadas por Ciudad y Estrato.
* Matriz de correlación de Pearson entre atributos sensoriales y el agrado global.
* Distribución de satisfacción: % Insatisfechos (1-3), % Neutros (4), % Satisfechos (5-7).

### 2.6. Hoja `Verbatims`
Estructura para el procesamiento de respuestas de texto libre:
* Columnas: `ID_Participante`, `Estudio`, `Muestra_Concepto`, `Variable_Origen`, `Cita_Verbatim`, `Categoria_Tema`, `Sentimiento` (`Positivo`, `Neutral`, `Negativo`).
