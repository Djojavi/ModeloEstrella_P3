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

<img width="1321" height="442" alt="image" src="https://github.com/user-attachments/assets/5cac18cf-3d62-4edd-9936-e27b928a6f46" />

## 3. Configuración de consultas para modelado

Aquí se aplican las transformaciones necesarias para dejar las tablas listas para el modelo estrella.

- Asegurar las claves de las dimensiones:
  - `ProductKey` en `dim_prod`
  - `CustomerKey` en `dim_cliente`
  - `OrderDateKey` en `dim_fechaVenta`
  - `ShipDateKey` en `dim_fechaEnvio`
- Verificar tipos de datos y eliminar columnas innecesarias

<img width="932" height="701" alt="image" src="https://github.com/user-attachments/assets/21e49e5c-d8f5-4999-bbcf-60df8c8aef35" />


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

<img width="972" height="357" alt="image" src="https://github.com/user-attachments/assets/d220c067-0107-43d9-9f16-88bedea602e6" />


## 5. Vista de diagrama completo

En la vista de diagrama de Power Pivot se observan las relaciones entre hechos y dimensiones.

- `dim_prod.ProductKey` → `fact_sales.ProductKey`
- `dim_cliente.CustomerKey` → `fact_sales.CustomerKey`
- `dim_fechaVenta.OrderDateKey` → `fact_sales.OrderDateKey`
- `dim_fechaEnvio.ShipDateKey` → `fact_sales.ShipDateKey`

Esta vista permite validar que el modelo tiene la forma de estrella y que cada dimensión está correctamente conectada a la tabla de hechos.

<img width="1228" height="711" alt="image" src="https://github.com/user-attachments/assets/9bd9fe0e-e44f-4f46-8fc4-b608af8ce488" />


## 6. Respuestas a preguntas clave

A continuación se muestra el espacio para las tablas dinámicas que deben responder las preguntas del modelo.

### 6.1 ¿Cuántas ventas se realizaron por categoría de producto y mes?

- Dimensiones: `Category`, `Nombre del mes`
- Métrica: `SalesAmount` o `Quantity`

<img width="465" height="222" alt="image" src="https://github.com/user-attachments/assets/00a3f804-da2b-4d7d-a04b-b81a7a809d9e" />


### 6.2 ¿Cuál es el ingreso total (ventas) por cliente y género?

- Dimensiones: `CustomerKey` / `Gender`
- Métrica: `SalesAmount`

<img width="338" height="82" alt="image" src="https://github.com/user-attachments/assets/7c240bb6-1cc7-4623-84e3-707e083b8f26" />

### 6.3 ¿Cuál es la cantidad total vendida por producto?

- Dimensión: `Product Name`
- Métrica: `Quantity`

<img width="397" height="167" alt="image" src="https://github.com/user-attachments/assets/713a7ac6-2d92-4943-8840-ab4233b1e76a" />

### 6.4 ¿Cuál fue la cantidad enviada por mes de envío?

- Dimensión: `Nombre del mes` de `dim_fechaEnvio`
- Métrica: `Quantity`

<img width="1138" height="221" alt="image" src="https://github.com/user-attachments/assets/73bed463-07bd-47e4-821d-e344b15e080d" />


### 6.5 ¿Cuánto se vendió por tamaño de producto y por estado civil del cliente?

- Dimensiones: `Size`, `Marital Status`
- Métrica: `SalesAmount`

<img width="497" height="122" alt="image" src="https://github.com/user-attachments/assets/9b22802b-e8c6-496d-97e1-b6ead4114b28" />



