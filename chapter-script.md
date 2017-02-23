## Scripting

Uno de los tipos de _assets_ más importantes de Unity son los _scripts_. Éstos nos permiten, mediante código, programar el comportamiento que tendrán nuestros objetos en el juego. Estos _scripts_ pueden describirse en diferentes lenguajes, como C\#, Javascript, y Boo, pero nos centraremos en C\# por ser el más potente y versátil.

Para la edición de estos _scripts_ contamos con la herramienta MonoDevelop, aunque a partir de la versión 5.2 de Unity en Windows se integra también con Visual Studio. La herramienta de desarrollo a utilizar puede ser configurada en _Preferences ... &gt; External tools_.

### Creación de scripts

Crearemos un _script_ como cualquier otro _asset_, con la opción del menú _Assets &gt; Create &gt; C\# Script_. Una vez creado, podremos añadirlo como componente a cualquier _Game Object_, pudiendo de esta forma personalizar su comportamiento. Los \_scripts \_se comportarán como un tipo de componente más.

Veremos el _script_ creado entre los _assets_ del proyecto. Haciendo doble _click_ sobre él se abrirá en el editor de código que tengamos configurado, pudiendo así editarlo.

### Estructura de un script

Cuando abramos con el editor un _script_ recién creado, veremos un esqueleto como se muestra a continuación:

```
public class EsferaScript : MonoBehaviour {
    void Start () {

    }

    void Update () {

    }
}
```

Esta es la estructura básica de un _script_. Encontramos los siguientes métodos:

* `Start`: Se ejecutará cuando se cree el _Game Object_ sobre el que esté aplicado el _script_ \(como componente del mismo\).
* `Update`: Se ejecutará en cada iteración del juego, para actualizar el estado del _Game Object_ sobre el que esté aplicado. Por ejemplo, si nuestro juego se ejecuta a una frecuencia de 60 FPS \(fotogramas por segundo\), cada segundo se llamará 60 veces a los métodos `Update` de todos los componentes de los objetos para actualizarlos.

Estos son los métodos principales que encontraremos en la plantilla, aunque también podríamos definir otros métodos como:

* `Awake`: Se ejecuta antes de todos los `Start`, y será útil si tenemos que inicializar elementos de los que dependa la inicialización de otros objetos. Podemos inicializar lo básico en `Awake`, y dejar en `Start` toda aquella inicialización que dependa de que se haya realizado la inicialización básica de todos los objetos.
* `LateUpdate`: Se ejecuta después de haber ejecutado los `Update` de todos los objetos. Al igual que el caso anterior, también será útil para el caso de tener dependencias. Podemos dejar para `LateUpdate` todas las actualizaciones que dependan de haber actualizado todo lo que realiza `Update`.

### Ciclo del juego

El elemento principal del motor de un videojuego es el ciclo del juego. Se trata de un bucle infinito que se ejecuta a una determinada frecuencia \(es habitual que se ejecute a 60 FPS, 60 veces por segundo\), y en cada iteración lo que hace es:

* Leer la entrada del usuario \(mandos, teclado, ratón, pantalla táctil, etc\).
* Actualizar los elementos de la escena \(_Game Objects_\).
* Dibujar los gráficos de la escena actual.



### Acceso a los componentes y polimorfismo

### Interfaz pública del script

### Búsqueda de objetos

### Creación y destrucción de objetos

### Corrutinas



