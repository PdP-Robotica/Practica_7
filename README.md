# Practica_7

## Integrantes:
- Luis Fernando Duarte Reséndiz.
  
- Mauricio Alberto Gómez Arroyo.

- Diego Brandon Guzmán Sierra.

- Bryan Hiadim Vera Hernández.

## Introducción
En esta práctica, que consiste en realizar una figura utilizando la función "Pallet", el robot es programado para trazar un dibujo con un marcador. Esta función permite definir una matriz de coordenadas, lo que facilita al robot acceder a puntos específicos sin tener que programar manualmente cada ubicación. En lugar de enseñar al robot cada punto individualmente, Pallet organiza el espacio de trabajo en una cuadrícula, simplificando la planificación de movimientos. Gracias a la estructura de la matriz, el robot puede moverse punto por punto de forma automática, siguiendo las coordenadas predefinidas en la paleta y trazando líneas con precisión. Esto no solo ahorra tiempo en la programación, sino que también asegura que los movimientos sean exactos y repetibles. Además, la posición de los puntos se puede ajustar fácilmente al modificar las coordenadas dentro de la matriz, lo que proporciona flexibilidad y eficiencia en el proceso.

## Instrucciones

### 1. Configurar el Home del robot
Establecer las coordenadas que serán el Home del robot, solo poner en -90 grados J5, dando los valores de la imagen.
![image](https://github.com/user-attachments/assets/29dbde91-0399-48a1-a825-0e7c5a4ec34d)

### 2. Uso de la funcion Pallet
La función Pallet necesita algunos parámetros para su correcto funcionamiento. Estos consisten en:

1. El número de Pallet al que se refiere (se pueden guardar hasta 16 palets, del 0 al 15). Para esta práctica será el Pallet 0.

2. Se deben enseñar 3 puntos para establecer el área de trabajo del palet, estos serán los siguientes 3 parámetros de la función Pallet.

El primer punto debe estar en la esquina inferior izquierda, el segundo punto en la esquina inferior derecha, y el tercero en la esquina superior izquierda. En la imagen se visualiza cómo deben ser las posiciones de los puntos.

"Si el palet tiene una forma rectangular bien ordenada, solo se deben especificar los puntos para 3 de las 4 esquinas. Sin embargo, en la mayoría de las situaciones, se recomienda usar los puntos de las 4 esquinas para definir un palet" [1].
   
   ![image](https://github.com/user-attachments/assets/f02e74ff-cef1-4e4c-b617-22f3da9f9e14)

Para esta práctica se usan los puntos E1, E2, E3 para referirse a punto 1, punto 2 y punto 3 respectivamente (para definir los puntos no se puede usar la letra "P", por eso se usa la letra "E"), con las siguientes coordenadas:

   ![image](https://github.com/user-attachments/assets/91a73339-6887-4704-a541-c0c719f560d7)


3. Los siguientes dos parámetros son el número de columnas y el número de filas (para la función Pallet se deben insertar las coordenadas columna, fila). Para esta práctica se usa una matriz de 10 x 10.

La siguientes imágenes muestran cómo se vería una función Pallet correctamente y cómo fue la función Pallet utilizada:
![image](https://github.com/user-attachments/assets/a39a3ba3-7019-4ab0-ad68-b6740b965d3a)

![image](https://github.com/user-attachments/assets/ac5841f5-7212-4255-9f82-28d6b5956812)

### 3. Definir las coordenadas necesarias para realizar la figura
La figura que se desea realizar es un "Pac-Man", como se muestra en la siguiente imagen:

![image](https://github.com/user-attachments/assets/16151652-cc98-4ec2-98ff-280f41858828)

Se emplea la siguiente secuencia, iniciando en el punto 4,1, volviendo a la posición inicial 4,1 pasando por los puntos de la secuencia y llegar al punto 3,2. Luego en la posición inicial, se levanta el brazo 20 mm para que vaya al punto final, el ojo en 6,8 y bajando el brazo 20 mm para que pinte el ojo.

![image](https://github.com/user-attachments/assets/11aa56a9-ccaf-4c22-a36a-bbb8ec2be598)

### 4. Generar el codigo
Ya que se tiene todo planteado, se genera el código en el archivo "Main.prg", donde primero se encienden los motores y se ajustan la velocidad y aceleración del brazo robótico. Después se colocan las coordenadas en la función Pallet y, una vez terminado, se regresa el robot a su posición inicial en Home.

El código implementado fue:

```spel
Function main
	
Motor On
Power Low
Speed 30
Accel 30, 30
SpeedS 800
AccelS 4000, 4000
Home

	Pallet 0, E1, E2, E3, 10, 10
	Go Pallet(0, 4, 1)
	Go Pallet(0, 5, 1)
	Go Pallet(0, 6, 1)
	Go Pallet(0, 7, 1)
	Go Pallet(0, 8, 1)
	Go Pallet(0, 9, 2)
	Go Pallet(0, 9, 3)
	Go Pallet(0, 8, 4)
	Go Pallet(0, 7, 5)
	Go Pallet(0, 8, 6)
	Go Pallet(0, 9, 7)
	Go Pallet(0, 10, 8)
	Go Pallet(0, 9, 9)
	Go Pallet(0, 8, 10)
	Go Pallet(0, 7, 10)
	Go Pallet(0, 6, 10)
	Go Pallet(0, 5, 10)
	Go Pallet(0, 4, 10)
	Go Pallet(0, 3, 9)
	Go Pallet(0, 2, 8)
	Go Pallet(0, 1, 7)
	Go Pallet(0, 1, 6)
	Go Pallet(0, 1, 5)
	Go Pallet(0, 1, 4)
	Go Pallet(0, 2, 3)
	Go Pallet(0, 3, 2)
	Go Pallet(0, 4, 1)
	Go Pallet(0, 4, 1) +Z(20)
	Go Pallet(0, 6, 8) +Z(20)
	Go Pallet(0, 6, 8)
	
	Home
	
	
	
	

Fend
```
## Ejecución

Una vez terminado el código, se compila y carga al brazo para su ejecución obteniendo el siguiente resultado:


https://github.com/user-attachments/assets/d2436e9c-366d-4f11-8350-e1e7bedd14d9

![WhatsApp Image 2024-10-23 at 22 55 47_d55f69ed](https://github.com/user-attachments/assets/3beba439-08b8-47c7-ab21-753abd4cb438)

## Conclusiones
- Luis Fernando Duarte Reséndiz.
  
La función Pallet es una herramienta clave para la programación de robots industriales, ya que organiza el área de trabajo en una cuadrícula de coordenadas predefinidas. Esto permite al robot moverse automáticamente entre puntos específicos dentro de la cuadrícula sin la necesidad de programar manualmente cada uno de ellos. Este método simplifica la programación de movimientos repetitivos y asegura que el robot siga trayectorias preestablecidas con alta precisión y consistencia en cada ciclo de trabajo.



- Mauricio Alberto Gómez Arroyo.
  
Pallet garantiza que el robot siga trayectorias definidas con alta precisión y consistencia en cada ciclo de trabajo. Esto es crucial en aplicaciones que requieren exactitud, como la inspección de productos o el ensamblaje de componentes delicados. Al seguir coordenadas específicas dentro de la matriz, el robot minimiza los errores y asegura que cada tarea se realice de manera uniforme, lo que resulta en una mayor calidad y reducción de desperdicios.



- Diego Brandon Guzmán Sierra.
  
La versatilidad de Pallet se refleja en su aplicación en diversas industrias, desde la manufactura hasta la electrónica y el diseño. La capacidad de definir coordenadas dentro de una matriz permite que el robot se utilice en tareas tan variadas como la colocación de componentes electrónicos o el trazado de figuras. Su flexibilidad permite adaptar el área de trabajo del robot para diferentes tareas sin tener que reprocesar toda la programación, lo que hace que Pallet sea especialmente útil en entornos de producción que requieren cambios frecuentes.


- Bryan Hiadim Vera Hernández.
  
Una de las principales ventajas de Pallet es la facilidad con la que se pueden realizar ajustes en la programación del robot. Si cambia el diseño del producto o el área de trabajo, es posible modificar las coordenadas en la matriz de forma rápida y sin complicaciones, lo que permite una adaptación ágil a nuevas necesidades de producción. Esta capacidad para ajustar y recalibrar el área de trabajo del robot sin grandes esfuerzos lo convierte en una herramienta ideal para procesos que requieren flexibilidad y cambios constantes.

## Referencias

[1] De proyectos, A. y. D. (s/f). Manual del usuario. Epson.com. Recuperado de https://files.support.epson.com/far/docs/epson_rc_pl_70_users_guide_spanish_(v73r2).pdf

Robot Epson C4 de 6 ejes compactos. (s. f.). Productos | Epson México. https://epson.com.mx/Para-el-trabajo/Rob%C3%B3tica/6-Ejes/Robot-Epson-C4-de-6-ejes-compactos/p/RC4-A601ST75







