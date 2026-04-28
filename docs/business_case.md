# Caso de Negocio — Plataforma Analítica Gastronómica

## Contexto

Cafetería japonesa ubicada en Concepción, Chile.
Operación diaria desde abril 2024. Menú de 160 productos
entre panadería artesanal, panadería japonesa, pastelería,
café, té, bubble tea y frappés.

## Problema identificado

### Síntoma 1 — Datos atrapados en el ERP
El sistema de punto de venta registra cada transacción pero
los datos no estaban disponibles para análisis histórico.
Además, el ERP tiene el defecto de no registrar correctamente 
los costos del menú.
El dueño no podía responder preguntas básicas como:
- ¿Cuál fue el mes de mayor ingreso?
- ¿Qué producto generó más margen en el año?
- ¿A qué hora se concentra el 80% de las ventas?

### Síntoma 2 — Decisiones de menú por intuición
El menú se diseñaba basado en preferencias personales y
percepción del dueño, sin evidencia de qué productos
realmente generaban rentabilidad vs cuáles consumían
recursos sin retorno proporcional.

### Síntoma 3 — Producción sin planificación basada en datos
La cantidad de productos a hornear cada día se decidía
por experiencia, generando desperdicio en días de bajo
tráfico y quiebres de stock en días peak.

## Solución propuesta

Plataforma analítica de 4 capas que transforma los datos
del ERP en insights accionables:

1. Pipeline ETL en AWS para centralizar y procesar datos
2. Análisis estadístico para validar hipótesis operacionales
3. Ingeniería de Menú para clasificar productos por rentabilidad
4. Dashboard ejecutivo para visualización y toma de decisiones

## Impacto esperado

- Reducción del food cost mediante auditoría de Caballos de Trabajo
- Aumento de margen potenciando las 4 Estrellas identificadas
- Optimización de staffing basada en mapa de calor hora/día
- Eliminación progresiva de 85 productos Perro que no generan valor