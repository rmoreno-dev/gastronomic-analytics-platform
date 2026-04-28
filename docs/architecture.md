# Decisiones de Arquitectura

## Por qué AWS S3 como almacenamiento central

S3 fue elegido como capa de almacenamiento por tres razones:

**Costo:** el volumen de datos de la cafetería (~50MB) cabe
completamente dentro del Free Tier de 5GB. Costo real: $0.

**Escalabilidad:** si el negocio crece a múltiples sucursales,
S3 escala sin cambiar la arquitectura.

**Compatibilidad:** S3 es compatible nativamente con Glue,
Athena, y cualquier herramienta de BI — no hay vendor lock-in.

## Por qué arquitectura de 3 capas en S3

La arquitectura Raw → Staging → Processed sigue el patrón
estándar de la industria (Medallion Architecture simplificada):

**Raw:** preserva los datos originales del ERP sin modificar.
Permite auditoría y reproducibilidad completa.

**Staging:** datos validados y limpios en CSV. Permite
inspección visual antes de transformar.

**Processed:** datos enriquecidos en formato Parquet columnar.
Reduce el costo de queries en Athena hasta 90%.

## Por qué Parquet como formato de almacenamiento

Parquet es un formato columnar que permite a Athena leer
solo las columnas necesarias en cada query, en lugar de
escanear el archivo completo. Con los datos de la cafetería
esto reduce el costo por query de ~$0.0002 a ~$0.00002.

## Por qué AWS Glue como catálogo

Glue actúa como el diccionario de datos — define el esquema
de cada tabla Parquet en S3 para que Athena pueda consultarla
con SQL estándar sin necesidad de cargar los datos en memoria.

## Por qué Power BI Desktop y no Tableau o Looker

Power BI Desktop es gratuito y es el estándar en el mercado
corporativo chileno y latinoamericano. Tableau requiere
licencia (~$70 USD/mes). Looker está orientado a empresas
con infraestructura Google. Para una PYME gastronómica
en Chile, Power BI es la elección correcta.

## Por qué Ingeniería de Menú de Kasavana & Smith

El framework de Kasavana & Smith (1982) es el estándar
académico y profesional en gestión gastronómica. Clasifica
productos en 4 cuadrantes según popularidad y margen de
contribución, permitiendo decisiones específicas y accionables
para cada producto del menú.

## Limitaciones conocidas

**Food cost parcial:** el flujo de caja del ERP registra
solo algunos egresos (~$3.9M CLP). El costo real de
ingredientes no está disponible en el sistema, por lo que
el food cost calculado (5.2%) es una subestimación.
Este es un problema que ya se tenía en cuenta debido a 
la falencia operacional del ERP.

**Período de análisis:** los datos cubren abril-diciembre 2024
(267 días). No hay datos de enero-marzo por ser el período
de apertura del negocio.