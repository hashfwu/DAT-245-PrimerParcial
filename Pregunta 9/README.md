# Explique cómo se solucionaría mediante Excel el problema del caballo en el tablero de ajedrez con algoritmos genéticos (al menos una generación de 4x4 de las cuales pueden ser 5 posiciones de las 16).

Lo primero que hacemos es generar una semilla aleatoria: 

![alt text](images/image.png)

![alt text](images/image-1.png)

Generaremos un numero entre 1 y 8, ya que tendremos la siguiente definicion

![alt text](images/image-2.png)

![alt text](images/image-3.png)

![alt text](images/image-5.png)

Luego crearemos un macro para que pueda copiar y evaluar los movimientos legales:

![alt text](images/image-6.png)

Donde cada uno de los movimientos legales es coloreado de verde. El código es: 

![alt text](images/image-7.png)

![alt text](images/image-8.png)

Contamos la cantidad de movimientos legales

![alt text](images/image-9.png)

Y normalizamos los resultados en una escala del 0 al 100

![alt text](images/image-10.png)

Definimos unos bits de cruce, estará definido por la siguiente función: 

![alt text](images/image-13.png)

Esta hace el cruce solo a partir del mayor movimiento legal encontrado.

Este son coloreados a partir del siguiente código que genera una gradiente 

![alt text](images/image-12.png)

Luego definimos los bit de mutación, estos solo se mutaran en donde no hay movimientos legales. La coloracion estará acargo de un swicth case

![alt text](images/image-15.png)

![alt text](images/image-16.png)

Se vuelven a guardar lo movimientos legales

![alt text](images/image-18.png)

Y se vuelve a normalizar el resultado 

![alt text](images/image-20.png)

Creamos una función que pueda colorear los resultados

![alt text](images/image-21.png)

![alt text](images/image-22.png)

Se crea una nueva interpolacion de colores entre el celeste y el morado 

![alt text](images/image-23.png)

A cada función se le asigna un peso acorde a su normalización. Lo que tiene 100 tiene mas peso, los que tienen menos, menos peso. Luego, si sumamos todos los pesos dan menos de 12. Asi, los que tiene peso de 6, se copian 6 veces, y los que tienen peso de 0, se copian 0 veces, a menos se necesiten mas. 

![alt text](images/image-24.png)

![alt text](images/image-25.png)

Esta es la función que hace la copia en función del peso

![alt text](images/image-26.png)


En base a dos parámetros se puede llevar a cabo el programa

![alt text](images/image-27.png)

Asi pues, el programa se repite cuantas veces se haya definido en el parámetro de `Max de mutaciones`

![alt text](images/image-28.png)

El video de la prueba se encuentra [aqui](https://youtu.be/E66Pf02NqJw)

Su mejor resultado fue:

![alt text](images/Screenshot%20(200).png)

**Fuentes**:
- [Knight's tour, Wikipedia](https://en.wikipedia.org/wiki/Knight%27s_tour)
- [Knight’s Tour using Genetic Algorithm](https://rayantonius.com/tech/knight-tour-p5/)
- [Getting started with VBA in Office](https://learn.microsoft.com/en-us/office/vba/library-reference/concepts/getting-started-with-vba-in-office)
- [Normalización, IBM](https://www.ibm.com/docs/es/spss-statistics/saas?topic=analysis-normalization)
- [DP: distribución ponderada](https://pospotential.com/glosario-de-business-intelligence-y-gran-consumo/distribucion-ponderada/)