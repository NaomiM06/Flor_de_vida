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
------------
<img width="1557" height="930" alt="image" src="https://github.com/user-attachments/assets/188262ba-1142-4fa4-ad31-3d9297a1384f" />

Explicación de la imagen

La captura muestra la interfaz de Blender con un script de Python ejecutado desde el editor de texto. A la izquierda se observa la vista 3D con una figura formada por muchos círculos superpuestos, y a la derecha el código que genera esa geometría de manera automática.

Descripción general de lo que ocurre

El script crea un círculo central y luego utiliza un ciclo while para ir agregando más círculos alrededor. Cada nuevo círculo se coloca en una posición calculada con funciones trigonométricas (seno y coseno), lo que hace que todos queden distribuidos sobre una circunferencia imaginaria alrededor del origen.

Por qué aparecen tantos círculos

La razón principal es el valor del paso angular que se observa en el código.

En la primera versión el paso era 60 grados, lo que produce solo 6 círculos porque 360 / 60 = 6.

En esta imagen el paso angular es 9 grados.
Eso significa que el ciclo se ejecuta muchas más veces:

360 / 9 = 40 iteraciones

En cada iteración el programa añade un nuevo círculo sin eliminar el anterior. Como resultado, se generan aproximadamente 40 círculos alrededor del centro, todos con el mismo radio y parcialmente superpuestos.

Efecto visual que se produce

Debido a que los círculos están muy cerca unos de otros, las líneas se cruzan y forman un patrón denso que parece una especie de malla o roseta. No es un solo objeto complejo, sino muchos círculos independientes colocados en posiciones consecutivas a lo largo de la circunferencia.

Relación entre el parámetro y la densidad

El parámetro paso_angular controla directamente cuántos círculos se crean:

Un paso grande → pocas iteraciones → figura simple
Un paso pequeño → muchas iteraciones → figura más densa

En esta imagen, al usar 9 grados, el ángulo avanza en incrementos pequeños, por eso el patrón se ve casi como un disco lleno de curvas.

Conclusión
La imagen muestra el resultado de un patrón radial generado por programación. La gran cantidad de círculos no se debe a un error, sino a que el ciclo se repite muchas veces porque el incremento angular es pequeño. Esto produce un patrón más complejo y visualmente más cargado, ya que cada iteración añade un círculo adicional alrededor del centro.
-----------------------
<img width="1573" height="797" alt="image" src="https://github.com/user-attachments/assets/370650fd-455d-4dfc-afa7-304db9464392" />

Explicación de la imagen

La captura muestra nuevamente la interfaz de Blender con un script de Python que genera un patrón radial de círculos. A la izquierda se observa la vista 3D con la figura resultante y a la derecha el código que controla su creación. En comparación con la imagen anterior, aquí el patrón es menos denso y se distinguen claramente los círculos individuales.

Descripción de lo que ocurre en el script

El código realiza el mismo procedimiento general:

1. Limpia la escena eliminando los objetos existentes.
2. Define el radio de los círculos en 3 unidades.
3. Crea un círculo central en el origen (0, 0, 0).
4. Ejecuta un ciclo while que va colocando nuevos círculos alrededor del centro usando coordenadas calculadas con seno y coseno.

Por qué en esta imagen hay menos círculos

La diferencia principal está en el valor del paso angular:

paso_angular = 50

Esto significa que en cada iteración el ángulo aumenta 50 grados. Como el ciclo termina cuando el ángulo alcanza 360 grados, el número de iteraciones es aproximadamente:

360 / 50 ≈ 7.2

En la práctica, el ciclo genera 7 círculos periféricos porque el ángulo va tomando valores 0, 50, 100, 150, 200, 250 y 300. Cuando llega a 350 + 50 supera 360 y el ciclo termina.

Por esa razón se observan solo unos pocos círculos alrededor del centro, formando una especie de flor con pétalos amplios, en lugar de la malla densa de la imagen anterior.

Efecto visual del paso angular de 50 grados

Al ser un incremento grande:

Los círculos quedan más separados entre sí.
Las intersecciones son menores.
La figura es más simple y fácil de distinguir.

El patrón ya no parece un disco lleno, sino una composición radial clara donde cada círculo ocupa una posición bien definida.

Interpretación geométrica

Cada círculo se coloca sobre una circunferencia imaginaria de radio 3 centrada en el origen. El ángulo determina la posición sobre esa circunferencia. Como el incremento no divide exactamente 360, la distribución no es perfectamente simétrica como cuando se usan divisores exactos (por ejemplo 60, 45, 30). Aun así, el patrón mantiene una estructura radial.

Conclusión
La imagen muestra el mismo algoritmo de generación procedural, pero con un incremento angular mayor. Esto reduce la cantidad de iteraciones del ciclo y, por lo tanto, el número de círculos creados. El resultado es un patrón más simple, con menos superposición y una apariencia similar a una flor de pocos pétalos.
---------------
--------------
# Poligono
-----------------
Reporte de explicación del código

Introducción
El script mostrado en la imagen corresponde a un programa en Python ejecutado dentro de Blender cuyo objetivo es crear de manera procedural un polígono 2D regular. En el caso específico de la ejecución observada, el resultado es un hexágono. El código no utiliza primitivas predefinidas, sino que construye la geometría manualmente mediante la creación de vértices y aristas, lo que permite comprender el proceso interno de generación de mallas.

1. Importación de módulos

El programa inicia con la importación de dos bibliotecas:

bpy
Es la API oficial de Blender para Python. Permite crear y manipular objetos, mallas y elementos de la escena.

math
Proporciona funciones matemáticas necesarias para los cálculos trigonométricos, indispensables para posicionar los vértices del polígono usando coordenadas polares.

2. Definición de la función crear_poligono_2d

Se define una función que encapsula toda la lógica de construcción del polígono. Esta función recibe tres parámetros:

nombre
Nombre que tendrá la malla y el objeto en la escena.

lados
Cantidad de lados del polígono. Determina cuántos vértices se generarán.

radio
Distancia desde el centro hasta cada vértice, es decir, el tamaño del polígono.

El uso de una función permite reutilizar el procedimiento para crear cualquier polígono regular simplemente cambiando estos valores.

3. Creación de la malla y del objeto

Dentro de la función se crean dos estructuras fundamentales:

Una nueva malla mediante bpy.data.meshes.new
Un nuevo objeto que contiene esa malla mediante bpy.data.objects.new

Posteriormente el objeto se vincula a la colección activa de la escena para que sea visible y forme parte del entorno de trabajo.

4. Inicialización de estructuras de datos

Se crean dos listas vacías:

vertices
Almacenará las coordenadas tridimensionales de cada punto del polígono.

aristas
Guardará las conexiones entre los vértices, definiendo la forma del contorno.

Estas listas se llenarán en los siguientes bloques del código.

5. Cálculo de vértices usando coordenadas polares

Se utiliza un ciclo for que recorre el número total de lados del polígono. En cada iteración se calcula el ángulo correspondiente al vértice actual mediante la fórmula:

ángulo = 2π × i / lados

Esta expresión divide la circunferencia completa en partes iguales, garantizando que el polígono sea regular.

Luego se convierten las coordenadas polares a cartesianas:

x = radio × cos(ángulo)
y = radio × sin(ángulo)
z = 0

El valor de z se fija en cero para mantener la figura en un plano bidimensional.

Cada coordenada calculada se agrega a la lista de vértices.

6. Definición de las aristas

Una vez creados los vértices, se establece la conectividad entre ellos. Se recorre nuevamente la cantidad de lados y se crea una arista que conecta cada vértice con el siguiente.

La expresión (i + 1) % lados se utiliza para cerrar la figura, conectando el último vértice con el primero mediante la operación de módulo.

Esto asegura que el contorno del polígono quede completamente cerrado.

7. Construcción de la malla

Los datos almacenados en las listas se cargan en la malla mediante el método from_pydata, que recibe:

la lista de vértices
la lista de aristas
una lista de caras (vacía en este caso)

Luego se llama a update para que Blender actualice la geometría y la muestre correctamente en la vista 3D.

8. Limpieza de la escena

Antes de crear el polígono, el script elimina todos los objetos existentes en la escena. Esto evita superposiciones y asegura que el resultado sea el único elemento visible.

9. Llamada a la función

Finalmente se invoca la función con los parámetros:

nombre: Poligono2D
lados: 6
radio: 5

Esto produce un polígono regular de seis lados, es decir, un hexágono, centrado en el origen y con tamaño definido por el radio.

Resultado observado en la imagen

En la vista 3D se aprecia un hexágono plano dibujado únicamente con sus aristas, sin caras rellenas. Esto se debe a que la lista de caras se dejó vacía, por lo que la malla contiene solo el contorno.
-------------------------
Conclusión
El código demuestra cómo construir geometría en Blender desde un nivel fundamental, generando manualmente los vértices y sus conexiones. Este enfoque permite comprender la relación entre matemáticas, programación y modelado procedural. Además, la estructura modular mediante una función hace que el script sea reutilizable para crear polígonos regulares de cualquier número de lados y tamaño.
<img width="1563" height="900" alt="image" src="https://github.com/user-attachments/assets/66d12ec8-aec8-4709-8c16-cdd24db00c75" />





