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

## anodo comun:
La mejor definición de ánodo es el electrodo que pierde electrones en una reacción de oxidación. Normalmente se vincula al polo positivo del tránsito de la corriente eléctrica, pero no siempre es así. Normalmente se define el sentido de la corriente eléctrica, apreciándolo como un sentido de las cargas libres, pero si el conductor no es metálico, las cargas positivas que se producen se trasladan al conductor externo.

## catodo comun:
El cátodo es el electrodo con carga negativa, que en la reacción química sufre una reacción de reducción, donde su estado de oxidación se reduce cuando recibe electrones, Dentro de las celdas electrolíticas, el medio de traspaso de la energía, al no ser en un metal sino en un electrolito, pueden coexistir iones negativos y positivos que se mueven en sentidos opuestos. Pero por convenio, se dice que la corriente va desde el ánodo hacia el cátodo.

![tabla de verdad](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/simulacion%204%207%20segmentos/catodo%20comun.jpg)


El tipo de valor UInt16 representa enteros sin signo con valores comprendidos entre 0 y 65535.
La estructura UInt16 proporciona métodos para comparar instancias de este tipo, convertir el valor de una instancia en su representación de cadena y convertir la representación de cadena de un número en una instancia de este tipo.

La visualización dinámica es en concepto la proyección de una porción de la información visual en diferentes pequeños intervalos de tiempo, en la mayoria de casos los 7 pines de los catodos estan inter-conectados entre cada display como se observa en la figura 
![visualizacion dinamica 4 display](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/conex.png)

teniendo en cuenta lo anterior se debe realizar una multiplexacion para cada display ya que solo un display se encuentra activo
![numeros en display](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/numeros/numeros.gif)

## caja negra
El diseño de la caja negra para la implementacion del ejercicio planteado es el siguiente:
![caja negra](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/display_7segx4.jpg)

En este sentido, se adiciona al HDL de siete segmentos 4 señales de control para el LCD, llamadas An. cada bit de la señal An debe ser modificado en el tiempo, con el fin de activar solo un display.

## simulacion quartus prime 
se presenta en el simulador quartus prime 
![simulacion](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/simulacion%204%207%20segmentos/simulacion%204%20%207segmentos.jpg)

# conclusiones 
* para enteder el archivo debemos saber identificar los valores numericos que se nos estan presentando en el display, debemos tener en cuenta los numeros que nos aparecen en el display y si es necesario podemos y/o debemos cambiar la configuracion para que nos de el valor asignado que debe aparecer en el display

* en el proceso a la hora de simular el programa no nos daba la simulacion ya que el error que teniamos era que el testbench que estabamos utilizando no era el que debia ser por que no estabamos utilizando la direccion de la carpeta correspondiente 



 
