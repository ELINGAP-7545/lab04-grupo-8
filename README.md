# lab04
BCD2SSeg

## ESTUDIANTES

luis Eduardo Cardenas Ortiz
cod: 41458 CC:1077087937


Mateo luzardo jimenez
cod:61063  CC: 1026296907


### Implementar la vista dinamica en un display de 7 segmentos en forma decimal de 16 bits

Descripcion:

![display 7 segmentos](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/display/300px-7_segment_display_labeled.svg.png)

El tipo de valor UInt16 representa enteros sin signo con valores comprendidos entre 0 y 65535.
La estructura UInt16 proporciona métodos para comparar instancias de este tipo, convertir el valor de una instancia en su representación de cadena y convertir la representación de cadena de un número en una instancia de este tipo.

La visualización dinámica es en concepto la proyección de una porción de la información visual en diferentes pequeños intervalos de tiempo, en la mayoria de casos los 7 pines de los catodos estan inter-conectados entre cada display como se observa en la figura 
![visualizacion dinamica 4 display](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/conex.png)

teniendo en cuenta lo anterior se debe realizar una multiplexacion para cada display ya que solo un display se encuentra activo
![numeros en display](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/numeros/numeros.gif)

#### caja negra
El diseño de la caja negra para la implementacion del ejercicio planteado es el siguiente:
![caja negra](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/display_7segx4.jpg)

En este sentido, se adiciona al HDL de siete segmentos 4 señales de control para el LCD, llamadas An. cada bit de la señal An debe ser modificado en el tiempo, con el fin de activar solo un display.


 
