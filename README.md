# OpenMultiPowerMeter_SecRandom_con_cortes-
# OpenMultiPowerMeter_seq

Muestras secuenciales de 5 electrodomesticos más el agregado usando el OMPM  (equipo de medida propio  basados en un bus RS485 con modulos PZEM004) .El conjunto de datos se crea para 6 mediciones: nº1-02/24 14:47-20:03, nº2 05/03 14:49-18:07,nº3 05/11 14:49-18:07 ,nº4 05/14 17:22-23:43 ,nº5 5/16 09:52 -17:56 ,nº6 5/17 9:34-18:37, necesito los tres intervalos para entrenamiento,validación y prueba para NILMTK

Aquí tres posibles intervalos para entrenamiento, validación y prueba para tu conjunto de datos:

Entrenamiento: mediciones 1, 2, 3 y 4
Validación: medida 5
Pruebas: medida 6 Esta división le dará un conjunto de entrenamiento con el 75% de los datos, un conjunto de validación con el 16,67% de los datos y un conjunto de prueba con el 8,33% de los datos.



# Resultados Metricas  con algoritmo CO, metodo Median  y 10"

## Datos anteriores con secuencia fija y tiempo de encendido fijo de 2 minutos

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.420   | 0.789    | 0.756            | 0.453           | 0.741   | 0.632            |
| EAE            | 0.002   | 0.001    | 0.011            | 0.002           | 0.012   | 0.006            |
| MNEAP       | 1.138   | 0.349    | 0.484            | 1.150           | 0.502   | 0.725            |
| RMSE        | 17.417 | 7.339     | 22.688         | 13.816         | 12.651 | 14.382           |



## Datos con muestras aleatorias 

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
| F1              | 0.591   | 0.158    | 0.752            | 0.349           | 0.577   | 0.485            |
| EAE            | 0.000 | 0.005   | 0.005             | 0.003          | 0.001  | 0.002             |
| MNEAP       | 0.726   | 1.596     | 0.443            | 1.212           | 0.823   | 0.960            |
| RMSE        | 11.169 | 9.259     | 18.718          | 8.170           | 15.660 | 12.995           |



## Datos  en secuencia fija con programador  y tiempo de encendido seudoaleatorio entre 10 y 60 segundos

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
|F1|	0.638	|0.364|	0.858|	0.381|	0.682	|0.5846|
|EAE|	0.000|	0.000	|0.000|	0.000|	0.000|	0.0000|
|MNEAP|	0.678	|1.391|	0.342|	1.343|	0.761|	0.9030|
|RMSE	|11.315|	9.334	|15.782|	8.833|	15.806|	12.2146|

## Datos  en secuencia fija con programador, tiempo de encendido seudoaleatorio entre 10 y 60 segundos y corte de red que afecta a LED Lamp y Laptop Computer

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
|F1|	0.997|	0.0|	0.993|	0.00|	0.993| 0.596|
|EAE|	0.000	|0.0|	0.000|	0.001|	0.000|0|
|MNEAP|	0.019|	inf|	0.020|	409.51|	0.039|81.9176|
|RMSE|	0.559	|1.0|	1.976|	9.971|	1.477|2.996|



## Resultados de unir  todos los datos

| Metrica          | Fryer   | LED Lamp | Incandescent lamp | Laptop Computer | Fan     | Media Aritmética |
|-----------------|---------|----------|------------------|----------------|---------|------------------|
|F1	|0.889	|0.009|	0.917|	0.382|	0.635  |0.5664|
|EAE|	0.000|	0.000|	0.000|	0.000|	0.000|0 |
|MNEAP|	0.494|	18.688|	0.139|	1.887|	0.701|4.381|
|RMSE	|10.090	|15.255|	11.476|	7.264	|18.354|12.4878|






## INTERPRETACION DE LOS RESULTADOS

Las cuatro tablas presentan los resultados de aplicar diferentes métricas en distintos escenarios utilizando la herramienta NILMTK. A continuación, te proporciono una interpretación de cada tabla:

**Tabla 1: Datos anteriores con secuencia fija y tiempo de encendido fijo de 2 minutos**

- F1: La métrica F1 representa la precisión general del desagregador y varía de 0 a 1. Los valores más cercanos a 1 indican una mayor precisión. En este caso, la precisión varía entre 0.420 (Fryer) y 0.789 (LED Lamp).
- EAE: La métrica EAE (Error Absoluto Medio) mide la diferencia promedio entre el consumo real y el estimado. Los valores más bajos indican una mejor estimación. En este caso, los valores están en el rango de 0.001 a 0.012.
- MNEAP: La métrica MNEAP (Error Absoluto Medio Normalizado por Consumo de Energía Promedio) calcula el error promedio normalizado en relación al consumo promedio de energía. Los valores más bajos indican una mejor estimación. En este caso, los valores varían entre 0.349 y 1.150.
- RMSE: La métrica RMSE (Raíz del Error Cuadrático Medio) representa la raíz cuadrada del promedio de los errores al cuadrado. Valores más bajos indican una mejor estimación. En este caso, los valores oscilan entre 7.339 y 22.688.

**Tabla 2: Datos con muestras aleatorias**

Esta tabla muestra los resultados de aplicar las métricas en un escenario donde los datos se obtienen con muestras aleatorias.
Los valores de las métricas son diferentes en comparación con la tabla anterior, lo cual indica que la precisión y el error varían en este caso específico.

**Tabla 3: Datos en secuencia fija con programador y tiempo de encendido seudoaleatorio entre 10 y 60 segundos**

Esta tabla presenta los resultados de aplicar las métricas en un escenario donde los datos se generan utilizando una secuencia fija con programador y tiempos de encendido seudoaleatorios entre 10 y 60 segundos.
Los valores de las métricas difieren de los dos escenarios anteriores, lo cual indica que los resultados pueden variar según las condiciones y características específicas de los datos.

**Tabla 4: Datos en secuencia fija con programador, tiempo de encendido seudoaleatorio entre 10 y 60 segundos y corte de red que afecta a LED Lamp y Laptop Computer**

Esta tabla muestra los resultados de aplicar las métricas en un escenario similar al anterior, pero con la adición de un corte de red que afecta a las lámparas LED y la computadora portátil.
Los resultados reflejan el impacto del corte de red en la precisión y el error de las estimaciones, como se observa en los valores de la métrica LED Lamp y Laptop Computer.
Además, la métrica MNEAP para Laptop Computer muestra un valor de "inf" (infinito), lo cual indica que el error es extremadamente alto debido al corte de red y el consumo desproporcionado en ese período.



## RESUMEN

Para determinar cuál es la mejor tabla en este caso, debemos analizar las métricas y considerar cuál es más relevante para tus necesidades y objetivos específicos. A continuación, proporcionaré una interpretación de las tablas:

**Tabla 1**: Datos anteriores con secuencia fija y tiempo de encendido fijo de 2 minutos.Esta tabla muestra los resultados cuando se utilizó una secuencia fija y un tiempo de encendido fijo de 2 minutos. En general, las métricas tienen valores moderados, pero no son los más altos ni los más bajos en comparación con las otras tablas.

**Tabla 2**: Datos con muestras aleatorias.Esta tabla presenta los resultados de aplicar el algoritmo CO, método Mediana y tiempo de muestreo de 10 segundos en datos con muestras aleatorias. En comparación con las otras tablas, esta tabla muestra valores más altos en las métricas F1 y MNEAP para Fryer y LED Lamp.

**Tabla 3**: Datos en secuencia fija con programador y tiempo de encendido seudoaleatorio entre 10 y 60 segundos.Esta tabla muestra los resultados cuando se utilizó una secuencia fija con programador y tiempos de encendido seudoaleatorios entre 10 y 60 segundos.Las métricas tienen valores moderados y, en general, son similares a los de la tabla anterior.

**Tabla 4**: Datos en secuencia fija con programador, tiempo de encendido seudoaleatorio entre 10 y 60 segundos y corte de red que afecta a LED Lamp y Laptop Computer. Esta tabla presenta los resultados cuando se aplicó el algoritmo CO, método Mediana y un tiempo de muestreo de 10 segundos en datos con una secuencia fija con programador, tiempos de encendido seudoaleatorios y un corte de red que afecta a LED Lamp y Laptop Computer. Las métricas F1 y MNEAP para Fryer y Incandescent lamp tienen valores altos en comparación con las otras tablas. Sin embargo, la métrica MNEAP para Laptop Computer muestra un valor de "inf" (infinito), lo cual indica que el error es extremadamente alto debido al corte de red.

En cuanto a determinar la mejor tabla, debemos considerar cuáles son las métricas más importantes para nuestros objetivos. Si valoramos la precisión general, la tabla 4 tiene valores más altos en la métrica F1 para algunos dispositivos. Sin embargo, el corte de red en LED Lamp y Laptop Computer afecta negativamente las métricas en esos dispositivos po rlo que quizas deberiamos repetir las medidas.

Si nos preocupa el error absoluto medio (EAE) o el error cuadrático medio (RMSE), la tabla 4 tiene valores más bajos en general.

En resumen, la mejor tabla depende de nuestras prioridades y objetivos específicos. Tendriamos que evaluar cuáles son las métricas más importantes  elegir la tabla que mejor se ajuste a nuestras necesidades en términos de precisión y error.
