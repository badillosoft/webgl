# Proyecto Pong en WebGL

__Pong__ es un juego donde dos adversarios compiten
por mantener una pelota dentro de una caja. El primero en dejar
escapar la pelota 3 veces es el perdedor. 

## Pasos para construir el juego

### Parte I - Contrucción de la interfaz básica

1. Crear un cubo en el espacio que llamaremos "salón".
2. Ajustar una cámara en una cara la que llamaremos la cara
frontal del jugador.
3. Crear una esfera en el espacio que será la pelota.
4. Mover la pelota en una dirección dada (un vector unitario)
a velocidad constante.
5. Detectar cuando la pelota choca con alguna cara.
6. Reflejar la pelota sobre la cara.
7. Detectar cuando la pelota colisiona con la cara del jugador
y en dicho caso no hacer la reflexión sobre la cara.
8. Detectar cuando la pelota se ha alejado cierto radio del centro
del _salón_.
9. Crear una caja que será después controlada por el usuario y
colocarla sobre la cara frontal al usuario, la llamaremos "raqueta".
10. Limitar que la _raqueta_ para que se mueva dentro de una caja que serán
los límites de interacción de la raqueta con el salón.
11. Poner un texto justo en medio del salón que indique el puntaje
de la siguiente forma "XX | YY" donde _XX_ es el puntaje propio
y _YY_ el puntaje del otro jugador.

### Parte II - Integración de los controles y comunicación

1. Recibir los datos de posición y ángulo de un teléfono.
2. Mover la _raqueta_ mediante la posición y el ángulo recibido.
3. Crear un servidor basado en websockets que reciba en cada instante
la posición de la _raqueta_ de cada usuario y envíe la posición de
la pelota a cada usuario. En este punto se el cómputo de actualización
de la pelota lo hará el servidor y no los clientes, por lo que los
clientes se limitarán a poner la pelota donde el servidor diga,
esto para evitar efectos de error númerico sobre los cálculos y
cada usuario tenga la pelota en distinta posición.
4. Agregar el sistema de puntación, es decir, cada cliente recibe un mensaje
del servidor para actualizar el marcador.
5. Conectar a dos usuarios en tiempo real para probar
que todo funcione.

### Parte III - Sugerencias para complementar el videojuego

* Agregar un sonido cada que el servidor indique que la pelota ha chocado.
* Poner una canción de fondo.
* Dejar una estela de luz en la pelota.
* Colorear el _salón_ de forma atractiva.
* En lugar de enviar las coordenadas de la pelota en cada instate, puede enviarse
el vector dirección de la pelota cada que está choca. Así el cliente
simula el movimiento de la pelota hasta que el servidor le avisa que la pelota
ha chocado, en este momento, el cliente actualiza la posición de la pelota
y ajusta su nuevo vector dirección.
* Enviar las coordenadas de la _raqueta_ sólo cuando el usuario pase un umbral
de movimiento, es decir cuando se logre detectar que el usuario mueve la _raqueta_
y no se mantiene en _standby_.
* Agregar un entrenador de _pong_ el cual es un círculo sobre la cara opuesta
al usuario que se puede mover sobre toda la cara y hace que rebote la pelota.
El entrenador de _pong_ cuenta con inteligencia artificial para ir por la pelota
pero no de manera lineal, sino basado en los posibles movimientos de un humano.
* Mejorar el entrenador haciendo que utilice una _raqueta_ normal.