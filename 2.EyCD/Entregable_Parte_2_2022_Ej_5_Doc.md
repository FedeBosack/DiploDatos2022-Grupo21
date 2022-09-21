# Ejercicio 5: Documentación

## Consigna
Realizar un reporte de las operaciones que realizaron para obtener el conjunto de datos final.
Se debe incluir:
  1. Criterios de exclusión (o inclusión) de filas
  2. Interpretación de las columnas presentes
  3. Todas las transofrmaciones realizadas

Este documento es de uso técnico exclusivamente, y su objetivo es permitir que otres desarrolladores puedan reproducir los mismos pasos y obtener el mismo resultado. Debe ser detallado pero consiso. Por ejemplo:

## Desarrollo
  ### Criterios de exclusión de ejemplos
  1. Se elimina columna *zipcode* por su similitud con *Postcode*

  ### Características seleccionadas
  #### Características categóricas
  1. Se seleccionaron las siguientes variables categoricas:
        - 'Suburb': Son las zonas residenciales en la periferia urbana.
        - 'Regionname': El nombre de la region.
  
  #### Características numéricas
  1. Se seleccionaron las siguientes variables numéricas:
        - 'Postcode': Numero de habitaciones.
        - 'Price': Precio de la vivienda en dolares.
        - 'Distance': Distancia al centro de la ciudad.
        - 'Landsize': Tamaño del terreno.
        - 'Rooms': Cantidad de habitaciones
        - 'Bathroom': Cantidad de baños.
        - 'Car': Cantidad de autos.
        - 'airbnb_price_mean': Se agrega el precio promedio diario de publicaciones de la plataforma AirBnB en el mismo código postal.
        - 'airbnb_record_count': Se agrega el conteo de registros de la plataforma AirBnB en el mismo código postal.
        - 'review_scores_value_mean': Se agrega el promedio de la puntuacion de las revision de la publicacion.
        - 'review_scores_location_mean': Se agrega el promedio de la puntuacion de la locacion de la publicacion.

  ### Transformaciones:
  1. Todas las características categóricas fueron codificadas con un
  método OneHotEncoding
  2. Se codificaron todas las variables numéricas. Esto se hizo por que se sugería en la        consigna, no tiene sentido por lo cual se descarto esta codificacion.
  3. Se verifica las columnas con datos igual a cero  
    - `Bathroom`: Se eleminan estas filas ya que no pueden haber viviendas sin baño.  
    - `Car`: En este caso si pueden haber viviendas sin cochera, no se hace nada.  
  4. Se verifican las valores nulos.  
    - `airbnb_price_mean`, `airbnb_record_count`, `review_scores_value_mean`, `review_scores_location_mean`: comparten las mismas filas con valores nulos y se hace un drop a esas filas.  
    - `Car`: Se imputa los nulos con cero, ya que significa q no tiene cochera.  
  5. Se verifica si alguna variable tiene que ser normalizada:  
    - `Postcode`: Para tomarla como una variable numerica es neseario realizarle una normalizacion.   
  5. Las columnas `YearBuilt` y `BuildingArea` fueron imputadas utilizando la Imputación por KNN.
  6. Se aplico un PCA para reducir la dimensionalidad de la matriz

  ### Datos aumentados
  1. Se agregan las 3 primeras componentes obtenidas a través del
     método de PCA, aplicado sobre el conjunto de datos
     totalmente procesado.
