# Complemento Metodológico y Guía Técnica de Formatos

> **Documento de Apoyo para el Agente Copilot**  
> Este manual complementa a `SKILL.md` y `plantilla-excel-generar.md` incorporando las especificaciones gráficas de PowerPoint, normativas sensoriales avanzadas, bibliotecas de descriptores, taxonomía de verbatims y fórmulas matemáticas del «Manual de encuestas de consumidor».

---

## 1. Guía de Diseño y Estructura Diapositiva por Diapositiva en PowerPoint

El agente debe ceñirse a estas especificaciones técnicas **únicamente si el usuario solicita explícitamente la presentación en PowerPoint**.

### 1.1. Identidad Gráfica y Sistema Visual
* **Proporción de pantalla**: 16:9 (Panorámico).
* **Fondo general**: Blanco puro (`#FFFFFF`).
* **Tarjetas contenedoras**: Rectángulos con esquinas redondeadas (`roundRect` con ajuste de curvatura `4000`), fondo gris tenue (`#F4F5F7` o `#F8F9FA`) y sin borde grueso.
* **Tipografía**:
  * Título principal: Mayúsculas sostenidas, color oscuro institucional (`#1A1A1A`), negrita.
  * Subtítulos y acentos: Color morado institucional (`#6B2D5C`).
  * Cuerpo de texto y datos: Gris oscuro legible (`#333333`).
* **Banda de pie de diapositiva**: Franja delgada horizontal en la base con degradado tricolor continuo: **Naranja (`#FF6F00`) $\rightarrow$ Rosa (`#D81B60`) $\rightarrow$ Morado (`#6B2D5C`)**.
* **Paleta fija de colores por muestra**: Cada muestra conserva el mismo color en toda la presentación y en el Excel:
  * Muestra 1: Guinda (`#800020`)
  * Muestra 2: Morado (`#6B2D5C`)
  * Muestra 3: Naranja (`#E65100`)
  * Muestra 4: Rosa (`#D81B60`)

---

### 1.2. Estructura Diapositiva por Diapositiva del Informe (Slide-by-Slide)

```
[Slide 1: Portada]      --> Título del estudio, fecha, n y autoría técnica.
[Slide 2: Ejecutivo]    --> Conclusión macro, muestra ganadora y tarjetas de KPIs.
[Slide 3: Perfil]       --> Demografía (dona edad) y hábitos (barras marcas y canales).
[Slide 4: Agrado]       --> Barras apiladas 100% (1-7) y medias comparativas.
[Slide 5: JAR Sensorial]--> Gráfico divergente (Poco | Ideal | Mucho) y alertas ≥20%.
[Slide 6: Cruces Ciudad]--> Tabulación comparativa por ciudad y estrato socioeconómico.
[Slide 7: CATA Drivers] --> Barras de descriptores sensoriales clave por muestra.
[Slide 8: Ranking]      --> Distribución de preferencia y % en 1.er lugar.
[Slide 9: Verbatims]    --> Matriz temática, sentimiento y citas textuales clave.
[Slide 10: Hallazgos]   --> Diagnóstico técnico de brechas sensoriales.
[Slide 11: Insights]    --> Recomendaciones accionables de I+D, empaque y mercadeo.
```

#### Especificaciones por Diapositiva:

#### Diapositiva 1: Resumen Ejecutivo
* **Encabezado**: `RESUMEN EJECUTIVO · DIAGNÓSTICO GENERAL DEL ESTUDIO`.
* **Tarjeta Izquierda (Ganador)**: Muestra o concepto con mayor agrado e intención; código de muestra en grande, nombre o alias, porcentaje de preferencia global y % Top-2 box.
* **Tarjeta Derecha (Métricas Clave)**: Ficha técnica resumida: Base $n$ evaluada, ciudades cubiertas, fechas de campo, promedio de agrado global (/7).
* **Bloque Inferior**: Párrafo con la decisión de negocio recomendada.

#### Diapositiva 2: Perfil de Participantes y Hábitos de Consumo
* **Gráfico 1**: Dona de distribución por rango de edad (máximo 4 arcos para mantener legibilidad).
* **Gráfico 2**: Barras horizontales descendentes con marcas compradas habitualmente (% menciones).
* **Gráfico 3**: Barras horizontales de canales de compra principales (% menciones).
* **Nota al pie**: Base $n$ de encuestados que cumplieron los filtros de admisión.

#### Diapositiva 3: Evaluación de Agrado por Muestra y Atributo
* **Gráfico Principal**: Barras apiladas al 100% que muestran la distribución de la escala hedónica (niveles 1 a 7) para cada muestra.
* **Indicador Superpuesto**: Línea o etiqueta con la media aritmética calculada (escala 1 a 7) y porcentaje acumulado Top-2 Box (suma de 6 y 7).
* **Tabla Resumen**: Comparativo de medias por atributo individual (apariencia, aroma, sabor, textura y global).

#### Diapositiva 4: Diagnóstico Sensorial JAR (Just About Right)
* **Gráfico Divergente**:
  * Lado Izquierdo (Rojo/Naranja): Porcentaje acumulado de «Poco» (calificaciones 1 y 2).
  * Centro (Gris/Verde): Porcentaje de «Justo como me gusta» (calificación 3, ideal).
  * Lado Derecho (Azul/Morado): Porcentaje acumulado de «Mucho» (calificaciones 4 y 5).
* **Llamada de Alerta (Penalización)**: Resaltar en recuadro de advertencia todo atributo donde «Poco» o «Mucho» sea $\ge 20\%$.
* **Caja de Justificaciones**: Resumen de los motivos recogidos en la columna `Justificación_JAR` explicando la razón del defecto.

#### Diapositiva 5: Tabulación Cruzada por Segmentos
* **Estructura de Tabla Oficial**:

| Segmento | n | Agrado Medio (1-7) | % Top-2 Box | % Intención de Compra |
| :--- | :---: | :---: | :---: | :---: |
| **Total Muestra** | 100 | 5,4 | 62% | 58% |
| **Bogotá** | 50 | 5,6 | 67% | 63% |
| **Medellín** | 50 | 5,2 | 58% | 52% |
| **Estrato 2-3** | 60 | 5,3 | 60% | 55% |
| **Estrato 4** | 40 | 5,6 | 66% | 64% |

#### Diapositiva 6: Análisis CATA (Check-All-That-Apply)
* **Visual**: Barras horizontales por muestra comparando la frecuencia de selección de cada descriptor sensorial o funcional.
* **Interpretación**: Identificar los términos asociados estadísticamente con las muestras de mayor agrado (impulsores o *drivers* de agrado).

#### Diapositiva 7: Ranking y Selección Forzada
* **Gráfico**: Barras horizontales con el porcentaje de elección en 1.er lugar para cada muestra.
* **Métrica Secundaria**: Suma de rangos o posición media ordinal (1 a N).

#### Diapositiva 8: Análisis Cualitativo de Verbatims
* **Gráfico de Barras**: Conteo porcentual de menciones por tópico clave (sabor, textura, precio, empaque, practicidad).
* **Distribución de Sentimiento**: Porcentaje de menciones positivas, neutras y negativas por muestra.
* **Citas Textuales**: 2 a 3 citas literales destacadas entrecomilladas que ilustren el porqué de los resultados.

#### Diapositiva 9: Hallazgos Principales
* Síntesis en viñetas estructuradas que explican las brechas estadísticas entre fórmulas, fortalezas competitivas y puntos débiles identificados.

#### Diapositiva 10: Insights Accionables y Caminos de Negocio
* Recomendaciones directas de formulación (I+D), ajustes de comunicación visual (empaque) o posicionamiento de precio y canales (mercadeo).

---

## 2. Metodología de Análisis de Penalización JAR (ASTM MNL63)

El análisis de penalización (*Penalty Analysis*) determina qué tanto castiga el consumidor el agrado global de un producto cuando percibe que un atributo sensorial está fuera de su punto ideal.

### 2.1. Cálculo de la Caída Media de Agrado (Mean Drop)
Por cada atributo evaluado con escala JAR (1 a 5), los consumidores se agrupan en tres categorías:
1. **Poco (Too Low)**: Calificaciones 1 y 2.
2. **Ideal (JAR)**: Calificación 3.
3. **Mucho (Too High)**: Calificaciones 4 y 5.

La caída media de agrado (*Mean Drop*) se calcula como:
$$\text{Mean Drop}_{\text{Poco}} = \text{Media de Agrado Global}_{\text{Grupo Ideal}} - \text{Media de Agrado Global}_{\text{Grupo Poco}}$$
$$\text{Mean Drop}_{\text{Mucho}} = \text{Media de Agrado Global}_{\text{Grupo Ideal}} - \text{Media de Agrado Global}_{\text{Grupo Mucho}}$$

### 2.2. Reglas de Decisión para Reformulación
* **Zona de Alerta Crítica**: Si el porcentaje de evaluadores en «Poco» o «Mucho» es **$\ge 20\%$** Y el *Mean Drop* asociado es **$\ge 1,0$ punto** en la escala hedónica de 7 puntos, el atributo debe reformularse de manera mandatoria.
* **Zona de Oportunidad Menor**: Si el porcentaje está entre $10\%$ y $19\%$, se clasifica como punto de monitoreo o mejora secundaria.
* **Zona de Calibración Óptima**: Si el porcentaje en «Ideal» (nivel 3) es **$\ge 70\%$**, el atributo no debe modificarse.

---

## 3. Taxonomía Estandarizada para Codificación de Verbatims

Para procesar respuestas cualitativas y justificaciones del JAR sin sesgos del investigador:

### 3.1. Categorías Temáticas Obligatorias
1. **`Sabor`**: Comentarios sobre intensidad de sabor característico, naturalidad, balance dulce/ácido/salado, persistencia o regusto.
2. **`Textura / Consistencia`**: Fluidez, viscosidad, cremosidad, presencia de grumos, dureza, suavidad, sensación en boca.
3. **`Apariencia / Color`**: Tono, brillo, uniformidad visual, transparencia, aspecto apetitoso o artificial.
4. **`Aroma / Olor`**: Intensidad del olor, agrado, correspondencia con la fruta o ingrediente real, olores extraños.
5. **`Empaque / Anaquel`**: Tamaño de letra, visibilidad en vitrina, practicidad de apertura, material, colores del diseño.
6. **`Precio / Valor Percibido`**: Relación costo-beneficio, percepción de producto costoso, accesible o económico.
7. **`Practicidad / Preparación`**: Facilidad de servicio en el hogar, versatilidad en recetas, ocasiones de consumo.
8. **`Salud / Bienestar`**: Contenido calórico, azúcar percibida, adición de conservantes, adecuación para niños o personas con condiciones de salud.

### 3.2. Criterios de Clasificación de Polaridad de Sentimiento
* **`Positivo (+1)`**: La frase elogia o destaca un beneficio (ej. *«Tiene excelente sabor frutal»*, *«Llama la atención en el anaquel»*).
* **`Neutral (0)`**: La frase describe un hecho o forma de consumo sin juicio valorativo (ej. *«La consumo al desayuno con tostadas»*).
* **`Negativo (-1)`**: La frase señala una queja, inconformidad o sugerencia de corrección (ej. *«Muy dulce, empalaga rápido»*, *«Letras ilegibles»*).

---

## 4. Fórmulas de Cálculo para el Dashboard de Excel

Para implementar en la hoja `Dashboard_Data` conectada a `Sheet1`:

### 4.1. Porcentaje Top-2 Box Hedónico (Niveles 6 y 7)
```excel
=CONTAR.SI.CONJUNTO(Sheet1!$G$2:$G$101, ">=6", Sheet1!$E$2:$E$101, "Muestra_382") / CONTAR.SI(Sheet1!$E$2:$E$101, "Muestra_382")
```

### 4.2. Promedio Ponderado de Agrado Sensorial
```excel
=PROMEDIO.SI(Sheet1!$E$2:$E$101, "Muestra_382", Sheet1!$G$2:$G$101)
```

### 4.3. Porcentaje JAR "Justo como me gusta" (Ideal = Nivel 3)
```excel
=CONTAR.SI.CONJUNTO(Sheet1!$H$2:$H$101, 3, Sheet1!$E$2:$E$101, "Muestra_382") / CONTAR.SI(Sheet1!$E$2:$E$101, "Muestra_382")
```

### 4.4. Porcentaje de Penalización JAR por Defecto (Poco = Niveles 1 y 2)
```excel
=CONTAR.SI.CONJUNTO(Sheet1!$H$2:$H$101, "<=2", Sheet1!$E$2:$E$101, "Muestra_382") / CONTAR.SI(Sheet1!$E$2:$E$101, "Muestra_382")
```

### 4.5. Correlación de Atributo con el Agrado Global (Pearson $r$)
```excel
=COEF.DE.CORREL(Sheet1!$G$2:$G$101, Sheet1!$H$2:$H$101)
```

---

## 5. Control de Contingencias en Campo

* **Participante que deserta a mitad del test**: Se elimina su registro incompleto y se convoca a un reemplazo utilizando la misma fila de rotación asignada para ese ID de cuota.
* **Respuestas atípicamente veloces (*Speeders*)**: Encuestas diligenciadas en menos del 40% del tiempo medio estándar deben excluirse de la base analítica.
* **Calificaciones en línea recta (*Straight-lining*)**: Evaluadores que asignan idéntico valor numérico a todos los atributos sin variación deben auditarse y depurarse si muestran falta de atención manifiesta.
