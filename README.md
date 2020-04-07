# lab04
BCD2SSeg

## ESTUDIANTES

Luis Eduardo Cardenas Ortiz
cod: 41458 CC:1077087937


Mateo luzardo jimenez
cod: 61063  CC: 1026296907


### Implementar la vista dinámica en un display de 7 segmentos en forma decimal de 16 bits

Descripción:
El tipo de valor UInt16 representa enteros sin signo con valores comprendidos entre 0 y 65535.
La estructura UInt16 proporciona métodos para comparar instancias de este tipo, convertir el valor de una instancia en su representación de cadena y convertir la representación de cadena de un número en una instancia de este tipo.

![display 7 segmentos](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/display/300px-7_segment_display_labeled.svg.png)

## Ánodo común:
La mejor definición de ánodo es el electrodo que pierde electrones en una reacción de oxidación. Normalmente se vincula al polo positivo del tránsito de la corriente eléctrica, pero no siempre es así. Normalmente se define el sentido de la corriente eléctrica, apreciándolo como un sentido de las cargas libres, pero si el conductor no es metálico, las cargas positivas que se producen se trasladan al conductor externo.

## Cátodo común:
El cátodo es el electrodo con carga negativa, que en la reacción química sufre una reacción de reducción, donde su estado de oxidación se reduce cuando recibe electrones, Dentro de las celdas electrolíticas, el medio de traspaso de la energía, al no ser en un metal sino en un electrolito, pueden coexistir iones negativos y positivos que se mueven en sentidos opuestos. Pero por convenio, se dice que la corriente va desde el ánodo hacia el cátodo.

![tabla de verdad](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/simulacion%204%207%20segmentos/catodo%20comun.jpg)




La visualización dinámica es en concepto la proyección de una porción de la información visual en diferentes pequeños intervalos de tiempo, en la mayoria de casos los 7 pines de los cátodos estan inter-conectados entre cada display como se observa en la figura 
![visualizacion dinamica 4 display](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/conex.png)

Teniendo en cuenta lo anterior se debe realizar una multiplexación para cada display ya que sólo un display se encuentra activo
![numeros en display](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/numeros/numeros.gif)

## Caja negra
El diseño de la caja negra para la implementación del ejercicio planteado es el siguiente:
![caja negra](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab04_display_7segx4/doc/display_7segx4.jpg)

En este sentido, se adiciona al HDL de siete segmentos 4 señales de control para el LCD, llamadas An. cada bit de la señal An debe ser modificado en el tiempo, con el fin de activar solo un display.

## Descripción funcional: 
En esta tabla mostramos la tabla de verdad del número decimal al BCD y al 7 segmentos
![tabla de verdad](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/TABLA/TABLA%201.jpg)

## Simulación Quartus prime 
Se presenta en el simulador Quartus prime 
![simulacion](https://github.com/ELINGAP-7545/lab04-grupo-8/blob/master/simulacion%204%207%20segmentos/simulacion%204%20%207segmentos.jpg)

## Código Verilog para 4x7segmentos

```verilog
`timescale 1ns / 1ps //se utiliza para especificar unidad de tiempo en la simulación.  
		     //Duración de tiempo de 1ns de los delay y 1ps para el 
		     //análisis de recolección de datos. 
module display(
    input [15:0] num, //Registro que se encarga de llevar el número a mostrar en los display
    input clk,
    output [0:6] sseg,
    output reg [3:0] an,
	 input rst,
	 output led
    );



reg [3:0]bcd=0; 
//wire [15:0] num=16'h4321;
 
BCDtoSSeg bcdtosseg(.BCD(bcd), .SSeg(sseg)); //Instanciación del programa BCDtoSSeg básico para un 7 segmentos.

reg [26:0] cfreq=0; 			//Registro de 27b inicializado en 0
wire enable;

// Divisor de frecuecia

assign enable = cfreq[16];  //A través de enable se va a llevar la información de qué parte del display debe encender. Cfreq es 16 porque son 4 7seg de 4b c/u.
assign led =enable;			 //led que va a enceder.
always @(posedge clk) begin  //funcionamiento con flancos de subida
  if(rst==1) begin          //Si rst es 1 cfreq va ser 0
		cfreq <= 0;				 
	end else begin				 //De lo contrario cfreq va a sumar 1 para asignar la frecuencia al display correspondiente
		cfreq <=cfreq+1;		
	end
end

reg [1:0] count =0;         //Resgistro de 2b
always @(posedge enable) begin
		if(rst==1) begin   //Si rst es 1, count es 0 y an(ánodo) inhibe el funcionamiento de todos los display
			count<= 0;
			an<=4'b1111; 
		end else begin 
			count<= count+1; //De lo contrario, a count se le suma 1 para poder ingresar al case del display correspondiente
			an<=4'b1101;	  // y an permite funcionar a los display    
			case (count) 
				2'h0: begin bcd <= num[3:0];   an<=4'b1110; end  //Cada display tiene asignados 4b para la representación numérica, 0-F
				2'h1: begin bcd <= num[7:4];   an<=4'b1101; end 
				2'h2: begin bcd <= num[11:8];  an<=4'b1011; end 
				2'h3: begin bcd <= num[15:12]; an<=4'b0111; end 
			endcase
		end
end

endmodule

```

## Testbench


```verilog
`timescale 1ns / 1ps


module testbench;

	// Inputs
	reg [15:0] num;
	reg clk2;
	reg rst;

	// Outputs
	wire [0:6] sseg;
	wire [3:0] an;

	// Instantiate the Unit Under Test (UUT)
	display uut (
		.num(num),			//Instanciación de los registros que se van a utilizar del projecto  
		.clk(clk2), 
		.sseg(sseg), 
		.an(an), 
		.rst(rst)
	);                            

	initial begin
		// Initialize Inputs
		clk2= 0;			
		rst = 1;
		#10 rst =0;
		
		num = 16'h4321;  //Número que se muestra en los 4 7segmentos
        

	end
      

	always #1 clk2 = ~clk2;
	
endmodule



```
# conclusiones 
* Para enteder el archivo debemos saber identificar los valores numéricos que se nos están presentando en el display, debemos tener en cuenta los números que nos aparecen en el display y si es necesario podemos y/o debemos cambiar la configuración para que nos dé el valor asignado que debe aparecer en el display.





 
