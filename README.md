# lab04
BCD2SSeg

#ESTUDIANTES

luis Eduardo Cardenas Ortiz
cod: 41458 CC:1077087937

Mateo luzardo 
cod:        CC:


#Implementar la vista dinamica en un display de 7 segmentos en forma decimal de 16 bits

Descripcion:

![display 7 segmentos](C:\Users\Alexandra\Desktop\LUIS CARDENAS\UNIVERSIDAD\ARQUITECTURA DE PROCESADORES\display\imagenes\display)

El tipo de valor UInt16 representa enteros sin signo con valores comprendidos entre 0 y 65535.
La estructura UInt16 proporciona m�todos para comparar instancias de este tipo, convertir el valor de una instancia en su representaci�n de cadena y convertir la representaci�n de cadena de un n�mero en una instancia de este tipo.

La visualizaci�n din�mica es en concepto la proyecci�n de una porci�n de la informaci�n visual en diferentes peque�os intervalos de tiempo, en la mayoria de casos los 7 pines de los catodos estan inter-conectados entre cada display como se observa en la figura 
![visualizacion dinamica 4 display](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/conex.png)

teniendo en cuenta lo anterior se debe realizar una multiplexacion para cada display ya que solo un display se encuentra activo
![numeros en display](C:\Users\Alexandra\Desktop\LUIS CARDENAS\UNIVERSIDAD\ARQUITECTURA DE PROCESADORES\display\imagenes\numeros)

# caja negra
El dise�o de la caja negra para la implementacion del ejercicio planteado es el siguiente:
![caja negra](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/display_7segx4.jpg)

En este sentido, se adiciona al HDL de siete segmentos 4 se�ales de control para el LCD, llamadas An. cada bit de la se�al An debe ser modificado en el tiempo, con el fin de activar solo un display.


 
