# Flor de vida
-------------
Reporte de explicación del código

1. Importación de librerías
   El script comienza importando dos módulos.

* bpy: es la API de Python de Blender, permite crear, modificar y eliminar objetos dentro de la escena mediante código.
* math: proporciona funciones matemáticas necesarias para realizar cálculos trigonométricos, como seno, coseno y conversión de grados a radianes.

2. Limpieza de la escena
   En este bloque se prepara el entorno de trabajo eliminando cualquier objeto existente.
   Primero se seleccionan todos los objetos de la escena con la instrucción de selección global.
   Posteriormente se ejecuta la operación de borrado, dejando la escena vacía.
   El objetivo es garantizar que el patrón que se generará no se mezcle con elementos previos.

3. Definición de parámetros de la figura
   Aquí se establecen las variables que controlan la geometría del patrón.

* radio = 3: define el tamaño de cada círculo que se creará.
* angulo_actual = 0: representa el ángulo inicial desde el cual comenzará el patrón.
* paso_angular = 60: determina cuánto aumentará el ángulo en cada iteración. Este valor permite distribuir los círculos cada 60 grados, lo que genera seis posiciones alrededor del centro.

4. Creación del círculo central
   Se agrega un círculo en la coordenada (0, 0, 0), es decir, en el origen del sistema.
   Se usa el mismo radio definido previamente y se especifica la cantidad de vértices (64) para que la figura tenga una apariencia más suave y redondeada.
   Este círculo funciona como referencia y punto central del patrón.

5. Inicio del patrón repetitivo con estructura while
   Se utiliza un ciclo while para repetir la creación de círculos hasta completar una vuelta completa de 360 grados.
   La condición del ciclo establece que se ejecutará mientras el ángulo actual sea menor que 360.

6. Cálculo de la posición de cada círculo
   Dentro del ciclo se calculan las coordenadas x y y donde se colocará cada nuevo círculo.
   Se aplican las funciones coseno y seno usando el ángulo actual convertido a radianes.
   Las fórmulas:
   x = radio × cos(ángulo)
   y = radio × sin(ángulo)
   Estas ecuaciones corresponden a la parametrización de una circunferencia, lo que permite ubicar los círculos equidistantemente alrededor del centro.

7. Creación de los círculos periféricos
   Con las coordenadas calculadas se llama nuevamente a la función que agrega un círculo.
   Cada uno se posiciona en (x, y, 0), manteniendo el mismo radio y número de vértices que el círculo central.
   Esto produce el patrón radial.

8. Actualización del estado del ciclo
   Después de crear cada círculo, el ángulo actual se incrementa en el valor del paso angular.
   Este incremento es esencial para avanzar en la circunferencia y evitar un bucle infinito.

9. Mensaje final de confirmación
   Una vez que el ciclo termina (cuando el ángulo alcanza o supera 360 grados), se imprime un mensaje en la consola indicando que el patrón se generó correctamente.
   Este mensaje no afecta la escena, solo sirve como retroalimentación para el usuario.
------------------
Conclusión
El código automatiza la creación de un patrón circular en Blender mediante programación. Primero limpia la escena, luego genera un círculo central y finalmente coloca seis círculos adicionales alrededor, distribuidos uniformemente gracias al uso de funciones trigonométricas y un ciclo iterativo controlado por el ángulo.
El resultado es una figura simétrica basada en una circunferencia, útil como ejercicio de scripting y geometría procedural.
