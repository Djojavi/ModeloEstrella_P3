# Informe Práctica 3: Modelo Estrella para Análisis de Ventas

## 1. Caso de Estudio Grupal

Una empresa desea analizar el rendimiento de sus ventas según productos, clientes y fechas. El objetivo es construir un modelo estrella en Excel/Power Pivot que permita responder preguntas comerciales clave con tablas dinámicas.

## 2. Creación de consultas para modelado

En esta fase se establecen las fuentes de datos y se crean las consultas necesarias para cargar las tablas al libro de Excel.

- Tablas principales del modelo:
  - `fact_sales`
  - `dim_prod`
  - `dim_cliente`
  - `dim_fechaVenta`
  - `dim_fechaEnvio`
- Se recomienda usar Power Query para:
  - cargar datos desde orígenes externos,
  - limpiar columnas,
  - estandarizar nombres y tipos de datos,
  - crear la base del modelo antes de pasarlo a Power Pivot.

![Creación de consultas](ruta_a_imagen_creacion_consultas.png)

## 3. Configuración de consultas para modelado

Aquí se aplican las transformaciones necesarias para dejar las tablas listas para el modelo estrella.

- Asegurar las claves de las dimensiones:
  - `ProductKey` en `dim_prod`
  - `CustomerKey` en `dim_cliente`
  - `OrderDateKey` en `dim_fechaVenta`
  - `ShipDateKey` en `dim_fechaEnvio`
- Verificar tipos de datos:
  - fechas como Date,
  - cantidades y montos como Number,
  - nombres y categorías como Text.
- Eliminar columnas innecesarias y mantener sólo las llaves y atributos relevantes.

![Configuración de consultas](ruta_a_imagen_configuracion_consultas.png)

## 4. Revisión de tablas en modelado

Antes de crear las relaciones, se revisan los datos y la estructura de cada tabla en Power Pivot.

### Tabla de hechos
- `fact_sales`
  - `ProductKey`
  - `CustomerKey`
  - `OrderDateKey`
  - `ShipDateKey`
  - `Quantity`
  - `UnitPrice`
  - `ProductCost`
  - `SalesAmount`

### Dimensiones
- `dim_prod`
  - `ProductKey` (PK)
  - `Product Name`
  - `Size`
  - `Category`
- `dim_cliente`
  - `CustomerKey` (PK)
  - `Birth Date`
  - `Marital Status`
  - `Gender`
  - `Income`
  - `Children`
  - `Home Owner`
  - `Cars`
- `dim_fechaVenta`
  - `OrderDateKey` (PK)
  - `Order Date`
- `dim_fechaEnvio`
  - `ShipDateKey` (PK)
  - `Ship Date`
  - `Nombre del mes`

![Revisión de tablas](ruta_a_imagen_revision_tablas.png)

## 5. Vista de diagrama completo

En la vista de diagrama de Power Pivot se observan las relaciones entre hechos y dimensiones.

- `dim_prod.ProductKey` → `fact_sales.ProductKey`
- `dim_cliente.CustomerKey` → `fact_sales.CustomerKey`
- `dim_fechaVenta.OrderDateKey` → `fact_sales.OrderDateKey`
- `dim_fechaEnvio.ShipDateKey` → `fact_sales.ShipDateKey`

Esta vista permite validar que el modelo tiene la forma de estrella y que cada dimensión está correctamente conectada a la tabla de hechos.

![Vista de diagrama completo](ruta_a_imagen_diagrama_completo.png)

## 6. Respuestas a preguntas clave

A continuación se muestra el espacio para las tablas dinámicas que deben responder las preguntas del modelo.

### 6.1 ¿Cuántas ventas se realizaron por categoría de producto y mes?

- Dimensiones: `Category`, `Nombre del mes`
- Métrica: `SalesAmount` o `Quantity`

![Tabla dinámica categoría y mes](ruta_a_imagen_tabla_dinamica_categoria_mes.png)

### 6.2 ¿Cuál es el ingreso total (ventas) por cliente y género?

- Dimensiones: `CustomerKey` / `Gender`
- Métrica: `SalesAmount`

![Tabla dinámica cliente y género](ruta_a_imagen_tabla_dinamica_cliente_genero.png)

### 6.3 ¿Cuál es la cantidad total vendida por producto?

- Dimensión: `Product Name`
- Métrica: `Quantity`

![Tabla dinámica producto cantidad](ruta_a_imagen_tabla_dinamica_producto_cantidad.png)

### 6.4 ¿Cuál fue la cantidad enviada por mes de envío?

- Dimensión: `Nombre del mes` de `dim_fechaEnvio`
- Métrica: `Quantity`

![Tabla dinámica mes envío](ruta_a_imagen_tabla_dinamica_mes_envio.png)

### 6.5 ¿Cuánto se vendió por tamaño de producto y por estado civil del cliente?

- Dimensiones: `Size`, `Marital Status`
- Métrica: `SalesAmount`

![Tabla dinámica tamaño y estado civil](ruta_a_imagen_tabla_dinamica_tamano_estado_civil.png)

## 7. Conclusión

El informe queda estructurado para que los pasos del modelado y las comprobaciones se documenten junto a las imágenes de soporte. La sección final permite un seguimiento directo de los resultados esperados en cada tabla dinámica.
