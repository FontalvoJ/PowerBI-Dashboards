# 📊 Visualización Segura de Datos Sensibles del Hotel

## 📝 Contexto

Este dashboard fue desarrollado como parte de una prueba técnica para la empresa **Cepobia**, con el objetivo de mostrar y analizar datos relacionados con un hotel.

### 📁 Fuente de Datos

- **Documento Utilizado**: `Script Base de Datos Hotel.sql`

### ✅ Requerimientos Implementados

El dashboard cumple con los siguientes requerimientos:

1. **📅 Cantidad de reservas realizadas.**
2. **👥 Cantidad de clientes que han hecho reservas.**
3. **💰 Valor total de reservas**, con la siguiente colorimetría:
   - 🔴 **Rojo**: Valor es 0.
   - 🟡 **Amarillo**: Valor comprendido entre 1 y 5.
   - 🟢 **Verde**: Valor mayor a 5.
4. **📊 Promedio del precio de las habitaciones** utilizando el lenguaje DAX.
5. **📈 Gráfico de líneas** que representa el valor de las reservas por tipo de temporada.

### 🎛️ Filtros del Dashboard

El dashboard incluye dos filtros:
- **🌍 Filtro por País**.
- **🧑‍💼 Filtro por Nombre**.

### 🔢 Métricas Utilizadas

Se implementaron las siguientes métricas en el dashboard:

1. **ReservaClientes**: 
   ```DAX
   ReservaClientes = IF(ISBLANK(DISTINCTCOUNT(Reserva_Habitacion[CodCliente])), 0, DISTINCTCOUNT(Reserva_Habitacion[CodCliente]))
  
2. **Reservas**: 
   ```DAX
   Reservas = IF(ISBLANK(COUNTROWS(Reserva_Habitacion)), 0, COUNTROWS(Reserva_Habitacion))
    
3. **PromedioPrecioHabitaciones**: 
   ```DAX
   PromedioPrecioHabitaciones = AVERAGE(Precio_Habitacion[Precio])
    
4. **ValorTotalReservas**: 

Utilizando en el eje X el Tipo de Temporada y en el eje Y la métrica:
   ```DAX
   ValorTotalReservas = SUM(Precio_Habitacion[Precio])
```

### 📁 Modelo de Datos

El modelo de datos se diseñó utilizando un esquema estrella. La tabla de hechos principal es Reserva_Habitacion, que se conecta directamente con varias tablas de dimensión:

- **👥 Clientes**.
- **🏨 Habitaciones**.
- **💵 Gastos**.

Además, estas tablas de dimensión tienen subdimensiones adicionales conectadas para mejorar la granularidad y el análisis de los datos.