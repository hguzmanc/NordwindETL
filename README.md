# NordwindETL
Process ETL for insert data in BD data-warehouse


Step 1- Restaurar el backup de la base de datos Nordwind
Step 2- Restaurar el backup de la base de datos NordwindBD (Se realizaron ajustes en esta base de datos por lo que es necesario volver a restaurarla)
Step 3- Levantar el Proceso de carga de tablas ETL en integration service (La tabla de hechos es cargada desde un package y las tablas dim se encuentran en otro package)

El modelo del diagrama NordwinDW fue modificado 1 vez, se quitó la tabla dim_geography ya que la relación aplicada en esta tabla no correspondía con la tabla de hechos order, esta tabla corresponde 
a una relación con la tabla employee y se quitó el campo id de cada una de las tablas ya que se toma como pk de la tabla la misma id que viene desde la tabla transaccional y este campo sirve para relacionar 
cada dim con la tabla de hechos

Nota: En la carga de cada dim se valida existencia de datos nuevos para cargarlos, y en la tabla de hechos se hace uso de un parámetro para ingresar la fecha desde, esta variable nos sirve para poder ejecutar 
	  la carga de datos desde una fecha específica.
	  
También se carga 2 variables con scripts 1 para borrar los datos existentes en la fecha seleccionada para volver a cargarla y de esta manera no tengamos datos repetidos y la otra variable es la query que realizará la carga de datos en la fecha seleccionada
