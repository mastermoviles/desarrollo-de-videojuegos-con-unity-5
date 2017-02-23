# El motor Unity

**Unity** es un motor genérico para la creación de videojuegos 2D y 3D enfocado hacia el desarrollo casual. La curva de aprendizaje del motor es bastante suave, especialmente si lo comparamos con motores más complejos como Unreal Engine 4, y nos permitirá realizar un desarrollo rápido de videojuegos. Esta característica hace este motor muy apropiado también para crear rápidamente prototipos de nuestros juegos.

A partir de la versión Unity 5, existen dos ediciones: _Personal_ y _Profesional_. La primera es gratuita e incluye todas las funcionalidades del motor. La segunda incluye funcionalidades adicionales de soporte \(construcción en la nube, herramientas de trabajo en equipo, etc\), y es de pago \(suscripción de $75 o pago único de $1.500\). La versión _Personal_ podrá ser utilizada por cualquier individuo o empresa cuyas ganancias anuales no superen los $100.000.

Uno de los puntos fuertes de Unity es la posibilidad de exportar a gran cantidad de plataformas. Soporta las **plataformas móviles iOS, Android, Windows Phone y Blackberry**, y además también permite exportar a web \(WebGL\), a videoconsolas \(PS4, PS3, PS Vita, Xbox One, Xbox 360, Wii U, etc\) y a ordenadores \(Mac, Windows y Linux\).

## Introducción a Unity

### El editor de Unity

Unity incorpora su propia herramienta integrada para la creación de videojuegos, que nos permite incluso crear algunos videojuegos de forma visual sin la necesidad de programar.

Dentro del entorno del editor de Unity encontramos diferentes paneles, de los cuales destacamos los siguientes:

* **Project**: Encontramos aquí todos los recursos \(_assets_\) que componen nuestro proyecto. Estos recursos pueden ser por ejemplo texturas, _clips_ de audio, _scripts_, o escenas. Destacamos aquí el _asset_ de tipo **escena**, que es el componente que nos permite definir cada estado \(pantalla\) del juego. Al hacer doble _click_ sobre una escena se abrirá para trabajar con ella desde el editor.
* **Hierarchy**: La escena está formada por una serie de nodos \(_game objects_\) organizados de forma jerárquica. En este panel vemos el árbol de objetos que contiene la escena abierta actualmente. Podemos seleccionar en ella cualquier objeto pulsando sobre su nombre.
* **Scene**: En este panel vemos de forma visual los elementos de la escena actual. Podremos movernos libremente por el espacio 3D de la escena para ubicar de forma correcta cada _game object_ y tener una previsualización del escenario del juego.
* **Inspector**: Muestra las propiedades del _game object_ o el _asset_ seleccionado actualmente en el entorno. 

![Editor de Unity](imagenes/unity/unity-editor.png)

### Arquitectura Orientada a Componentes

Como hemos comentado, **todos** los elementos de la escena son objetos de tipo `GameObject` organizados de forma jerárquica. Todos los objetos son del mismo tipo, independientemente de la función que desempeñen en el juego. Lo que diferencia a unos de otros son los _componentes_ que incorporen. Cada objeto podrá contener varios componentes, y estos componentes determinarán las funciones del objeto.

Por ejemplo, un objeto que incorpore un componente `Camera` será capaz de renderizar en pantalla lo que se vea en la escena desde su punto de vista. Si además incorpora un componente `Light`, emitirá luz que se proyectará sobre otros elementos de la escena, y si tiene un componente `Renderer`, tendrá un contenido gráfico que se renderizará dentro de la escena.

Esto es lo que se conoce como **Arquitectura Basada en Componentes**, que nos proporciona la ventaja de que las funcionalidades de los componentes se podrán reutilizar en diferentes tipos de entidades del juego. Es especialmente útil cuando tener un gran número de diferentes entidades en el juego, pero que comparten módulos de funcionalidad.

En Unity esta arquitectura se implementa mediante agregación. Si bien en todos los objetos de la escena son objetos que heredan de `GameObject`, éstos podrán contener un conjunto de componentes de distintos tipos \(`Light`, `Camera`, `Renderer`, etc\) que determinarán el comportamiento del objeto.

En el inspector podremos ver la lista de componentes que incorpora el objeto seleccionado actualmente, y modificar sus propiedades:

![Componentes de la cámara](imagenes/unity/unity-componentes-camera.png)

En esta figura anterior podemos observar que el objeto \(`GameObject`\) que contiene la cámara del juego contiene los siguientes componentes:

* `Transform`: Le da a la cámara una posición y orientación en la escena.
* `Camara`: Hace que se comporte como cámara. Capta lo que se ve en la escena desde su posición y lo renderiza en pantalla o en una textura.
* `GUILayer`: Permite introducir sobre la imagen renderizada elementos de la GUI \(etiquetas de texto, botones, etc\).
* `FlareLayer`: Permite crear sobre la imagen renderizada un efecto de _destello_.
* `AudioListener`: Escucha lo que se oye en la escena desde la posición de la cámara y lo reproduce a través de los altavoces.

Podemos modificar los componentes, añadiendo o eliminando según nos convenga. Podemos **eliminar** un componente pulsando sobre su cabecera en el inspector con el botón derecho y seleccionando _Remove Component_. También podemos añadir componentes pulsando sobre el botón _Add Component_ que encontramos en la parte inferior del inspector. Por ejemplo, podríamos añadir a la cámara un componente que haga que podamos moverla por el escenario pulsando determinadas teclas, o podríamos eliminar el componente _Audio Listener_ para no escuchar por los altavoces lo que se oiga en el lugar de la cámara \(en su lugar podríamos optar por ponerle este componente a nuestro personaje, para reproducir lo que se oiga desde su posición en la escena\).

## La escena 3D

El el editor de Unity veremos la escena con la que estemos trabajando actualmente, tanto de forma visual \(_Scene_\) como de forma jerárquica \(_Hierarchy_\). Nos podremos mover por ella y podremos añadir diferentes tipos de objetos.

### Añadir _game objects_ a la escena

Podemos añadir a la escena nuevos _game objects_ seleccionando en el menú la opción _GameObject &gt; Create Empty_, lo cual creará un nuevo objeto vacío con un único componente `Transform`, al que le deberíamos añadir los componentes que necesitásemos, o bien podemos crear objetos ya predefinidos mediante _GameObject &gt; Create Other_.

Entre los tipos de objetos predefinidos que nos permite crear, encontramos diferentes formas geométricas como _Cube_, _Sphere_, _Capsule_ o _Plane_ entre otras. Estas figuras pueden resultarnos de utilidad como objetos _impostores_ en primeras versiones del juego en las que todavía no contamos con nuestros propios modelos gráficos. Por ejemplo, podríamos utilizar un cubo que de momento haga el papel de nuestro personaje hasta que contemos con su modelo 3D.

![Menú de creación de un nuevo GameObject](imagenes/unity/unity-create-gameobject.png)

Si añadimos por ejemplo un _GameObject_ de tipo _Cube_ al seleccionarlo veremos sus propiedades en el inspector:

![Creación de un cubo](imagenes/unity/unity-cube.png)

Como podemos ver, este tipo de objetos geométricos tienen los siguientes componentes:

* `Transform`: Posición, rotación y escalado del objeto en la escena 3D.
* `Renderer`: Hace que el objeto se renderice en pantalla como una maya 3D. Con este componente conseguimos que el objeto tenga una representación gráfica dentro de la escena. En este caso se representa con la forma de un cubo, tal como podemos ver indicado en el componente _Mesh Filter_, pero podría ser otra forma geométrica, o cualquier maya que hayamos creado con alguna herramienta de modelado como Autodesk Maya, 3DS Max o Blender. También vemos que el _Renderer_ lleva asociado un material, que se le aplicará a la maya al renderizarse. Podremos crear materiales e incluirlos como _assets_ del proyecto, para así poderlos aplicar a las mayas.
* `Collider`: Hace que el objeto tenga una geometría de colisión, que nos permita detectar cuando colisiona con otros objetos de la escena. En este caso la geometría de colisión es de tipo caja \(_Box Collider_\), para así ajustarse a la forma de la geometría de su representación gráfica. 

### Posicionamiento de los objetos en la escena

Todos los _game objects_ incorporan al menos un componente `Transform` que nos permite situarlo en la escena, indicando su traslación, orientación y escala. Podremos introducir esta información en el editor, para así poder ajustar la posición del objeto de forma precisa.

También podemos mover un objeto de forma visual desde la vista _Scene_. Al seleccionar un objeto, bien en _Scene_ o en _Hierarchy_, veremos sobre él en _Scene_ una serie de ejes que nos indicarán que podemos moverlo. El tipo de ejes que se mostrarán dependerá del tipo de transformación que tengamos activa en la barra superior:

![Modos de transformación de objetos](imagenes/unity/unity-transform.png)

Las posibles transformaciones son:

* **Traslación**: Los ejes aparecerán como flechas y nos permitirán cambiar la posición del objeto.
* **Rotación**: Veremos tres círculos alrededor del objeto que nos pemtirán rotarlo alrededor de sus ejes _x_, _y_, _z_. 
* **Escalado**: Veremos los ejes acabando en cajas, indicando que podemos escalar el objeto en _x_, _y_, _z_.

Si pinchamos sobre uno de los ejes y arrastramos, trasladaremos, rotaremos, o escalaremos el objeto sólo en dicha eje. Si pinchamos sobre el objeto, pero no sobre ninguno de los ejes, podremos trasladarlo, rotarlo y escalarlo en todos los ejes al mismo tiempo.

### Jerarquía de objetos

Podremos **organizar de forma jerárquica** los objetos de la escena mediante la vista _Hierarchy_. Si arrastramos un _game object_ sobre otro en esta vista, haremos que pase a ser su hijo en el árbol de la escena. Los objetos vacíos con un único componente `Transform` pueden sernos de gran utilidad para agrupar dentro de él varios objetos. De esta forma, moviendo el objeto padre podremos mover de forma conjunta todos los objetos que contiene. De esta forma estaremos creando objetos compuestos.

También resulta de utilidad **dar nombre** a los objetos de la escena, para poder identificarlos fácilmente. Si hacemos _click_ sobre el nombre de un objeto en la vista _Hierarchy_ podremos editarlo y darle un nombre significativo \(por ejemplo _Suelo_, _Pared_, _Enemigo_, etc\).

![Cambiar el nombre de un GameObject](imagenes/unity/unity-object-name.png)

### Navegación en la escena

Además de podemos añadir objetos a la escena y moverlos a diferentes posiciones, deberemos poder movernos por la escena para posicionarnos en los puntos de vista que nos interesen para crear el contenido. Será importante conocer una serie de atajos de teclado para poder movernos con fluidez a través de la escena.

Encontramos tres tipos de movimientos básicos para movernos por la escena en el editor:

* **Traslación lateral**: Hacemos _click_ sobre la escena y arrastramos el ratón.
* **Giro**: Pulsamos _Alt + click_ y arrastramos el ratón para girar nuestro punto de vista.
* **Avance**: Pultamos _Ctrl + click_ y arrastramos el ratón, o bien movemos la rueda del ratón para avanzar hacia delante o hace atrás en la dirección en la que estamos mirando.

Con los comandos anteriores podremos desplazarnos libremente sobre la escena, pero también es importante conocer otras forma más directas de movernos a la posición que nos interese:

* **Ver un objeto**: Si nos interesa ir rápidamente a un punto donde veamos de cerca un objeto concreto de la escena, podemos hacer doble _click_ sobre dicho objeto en la vista _Hierarchy_.
* **Alineación con un objeto**: Alinea la vista de la escena con el objeto seleccionado. Es especialmente útil cuando se utiliza con la cámara, ya que veremos la escena tal como se estaría bien desde la camara. Para hacer esto, seleccionaremos el _game object_ con el que nos queramos alinear y seleccionaremos la opción del menú _GameObject &gt; Align View To Selected_.

## Assets

Los Assets en Unity hacen referencia a cualquiero item que podemos utilizar en nuestro juego/aplicación. Un asset puede ser un fichero creado fuera de la plataforma Unity, por ejemplo un modelo 3D, un fichero de audio, o cualquier otro tipo de fichero que este soportado. También existen algunos tipos de assets que pueden ser creados desde Unity, por ejemplo el controlador de una animación, controlador de un jugador, mezclador de audio o el render de una textura.

### Prefabs

Los prefabs son una colección de GameObjects y componentes predefinidos que se pueden reutilizar en nuestra aplicación. De esta forma, podemos crear un GameObject, añadir componentes y configurarlo con una serie de valores y posteriormente reutilizarlo en nuestra escena varias veces. Un prefab almcenará toda esta información y además a diferencia de copiar y pegar un GameObject existente en nuestra aplicación, si modificamos un prefab, el resto de prefabs en la escena también se modificarán propagando estos cambios. Al copiar y pegar un GameObject, los cambios que hagamos en el original no se propagan a la copia, por lo que cada instancia tiene sus propia configuración.

En el inspector de un prefab tenemos 3 botones que no estan presentes en un objeto normal: Select, Revert y Apply.  
El botón "Select" selecciona el prefab original del cual esta instancia fue creada y por lo tanto nos permite modificar todas las instancias que existan en la escena. Sin embargo, también podemos sobreescribir estos cambios en una determinada instancia de un prefab utilizando el botón "Apply". Finalmente, podemos usar el botón "Revert" para revertir la configuración del prefab a los valores default \(valores del prefab original, antes de sobreescribir los cambios\).

Los prefabs son la forma en que normalmente las librerías y SDKs tienen de ofrecer funcionalidades para Unity, por ejemplo ya veremos en la sección de realidad virtual o aumentada que utilizando Prefabs ya existentes podemos añadir estas funcionalidades a nuestra aplicación.

### Paquetes de assets

Los paquetes de Assets nos permiten en unity fácilmente reutilizar projectos y colecciones de assets. De hecho como ya veremos, los `Standard assets` y los items que encontramos en la `Asset store` se descargan en forma de pquetes. Podemos importar estos paquetes bien haciendo doble click en el fichero que se genera o bien desde el menu Assets &gt; Import package. Encontramos dos tipos de paquetes, los standard, que son colecciones ya disponibles por defecto al instalar Unity, y los paquetes personalizados que pueden ser creados por usuarios y descargarse online. De igual forma podemos exportar un paquete desde nuestro proyecto. Elige Assets &gt; Export package... y nos aparecerá un diálogo para seleccionar los assets que queremos incluir en nuestro paquete. Deja marcado la casilla `include dependencies` para añadir automáticamente los assets utilizados por losque has seleccionado. Al hacer click en `Export` podremos seleccionar donde almacenar el paquete que contiene los assets previamente seleccionados.

### Asset Store

Unity ha creado una tienda desde la que podemos descargar assets ya existentes. Estos assets pueden ser libres o comerciales, creados por la compañia Unity technologies o bien miembros de la comunidad. Podemos encontrar una gama muy variada de assets, que van desde texturas, modelos, animaciones, hasta proyectos completos, tutoriales y extensiones para el editor Unity. La tienda se puede acceder desde el propio entorno de Unity y los assets son descargados e instalados directamente en el proyecto que tengamos abierto. Los usuarios de Unity pueden publicar assets en la `Asset Store` y vender contenido que hayan creado.

## 



