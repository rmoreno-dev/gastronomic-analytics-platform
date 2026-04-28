# Metodología

## Fuente de datos

Datos exportados directamente del ERP del negocio en formato
Excel (.xlsx y .xls). Período: abril–diciembre 2024 (267 días).
Autorización explícita del propietario del establecimiento.

## Proceso de limpieza y validación

1. Eliminación de filas con total nulo o negativo
2. Remoción de ítem "Ley Redondeo" (ajuste de caja, no producto)
3. Exclusión de ventas mayoristas para análisis unitario
4. Estandarización de métodos de pago combinados
5. Parseo de fechas y horas desde formato texto del ERP

## Ingeniería de Menú — Kasavana & Smith (1982)

### Definición de variables

**Menu Mix %** = (unidades vendidas del ítem /
                  unidades totales vendidas) × 100

**Margen de contribución** = precio de venta promedio del ítem

### Umbrales de clasificación

**Umbral de popularidad** = 70 / N (donde N = número de ítems)
Para 157 productos analizados: umbral = 0.45%

**Umbral de margen** = promedio del precio de venta de todos
los ítems = $4,130 CLP

### Clasificación resultante

| Cuadrante | Condición |
|---|---|
| Estrella | Menu Mix ≥ 0.45% Y Precio ≥ $4,130 |
| Caballo de Trabajo | Menu Mix ≥ 0.45% Y Precio < $4,130 |
| Interrogante | Menu Mix < 0.45% Y Precio ≥ $4,130 |
| Perro | Menu Mix < 0.45% Y Precio < $4,130 |

## Pruebas estadísticas aplicadas

### H1 — Variación del ticket por día de semana
**Prueba:** Kruskal-Wallis (no paramétrica, datos no normales)
**Resultado:** H=115.96, p<0.001 → Rechazar H₀
**Interpretación:** el ticket varía significativamente según
el día de la semana.

### H2 — Fin de semana vs semana
**Prueba:** Mann-Whitney U (comparación de dos grupos)
**Resultado:** U=8,616,170, p<0.001 → Rechazar H₀
**Interpretación:** el fin de semana genera ticket
significativamente mayor.

### H3 — Correlación precio-popularidad
**Prueba:** Pearson r
**Resultado:** r=-0.120, p=0.136 → No rechazar H₀
**Interpretación:** no existe correlación significativa
entre el precio de un producto y su popularidad.

### H4 — Diferencia entre secciones
**Prueba:** Kruskal-Wallis
**Resultado:** H=4415.13, p<0.001 → Rechazar H₀
**Interpretación:** los ingresos difieren significativamente
entre secciones de producto.

## Normalidad de los datos

La prueba de Shapiro-Wilk confirma que ninguna de las
variables numéricas clave sigue distribución normal
(p<0.001 en todos los casos). Por esta razón se utilizaron
pruebas no paramétricas (Kruskal-Wallis, Mann-Whitney)
en lugar de pruebas paramétricas (ANOVA, t-test).