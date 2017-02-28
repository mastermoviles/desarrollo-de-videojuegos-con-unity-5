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

Hay que remarcar que sólo se actualizará y se dibujará la escena actualmente activa. Es decir, funciona como una máquina de estados, en la que cada escena representa un estado. Por ejemplo, podemos tener una escena con nuestra pantalla de título, otra con el menú de selección de nivel y otra para cada nivel del juego. Para pasar de una pantalla a otra podremos cambiar de escena, y en ese momento Unity cargará todos sus _Game Objects_, llamará a sus métodos `Awake` y `Start` para inicializarlos, y tras esto los actualizará en cada iteración del juego llamando a sus métodos `Update` y `LateUpdate` mientras la escena siga activa.

Podemos cambiar a otra escena usando el método `SceneManager.LoadScene`, proporcionando el nombre de la escena a la que queremos cambiar:

```
using UnityEngine;
using UnityEngine.SceneManagement;

public class JugadorScript : MonoBehaviour {
    void Update () {
        ...
        if(muerto) {
            SceneManager.LoadScene ("GameOver");        
        }
    }
}
```

En este caso, por defecto se destruirán todos los objetos de la escena actual y se cargarán los de la nueva que se inicializarán y empezarán a actualizarse. También existe la opción de cargar una escena de forma aditiva, que nos permitirá cargar los objetos de la nueva escena sin destruir los actuales:

```
SceneManager.LoadScene ("Laboratorio", LoadSceneMode.Additive);
```

En cualquiera de los casos anteriores, los objetos que se carguen serán inicializados y comenzarán a actualizarse hasta que se destruyan. Aunque en muchos videojuegos la frecuencia de actualización del ciclo del juego habitualmente es de 60 FPS, en Unity puede variar según la plataforma. En plataformas de sobremesa suele intentar alcanzar los máximos FPS posibles, mientras que en móviles suele limitar a 30 FPS para ahorrar batería. Si no queremos este comportamiento por defecto, podemos especificar los FPS que queremos intentar conseguir con:

```
Application.targetFrameRate = 60;
```

Esto no nos garantiza que podamos conseguir una frecuencia de 60 FPS, ya que según la capacidad de la máquina podría no llegar a conseguir esta frecuencia, pero intentará llegar a ella. Además, tampoco podemos confiar en que la frecuencia se mantenga constante, dependiendo de la carga gráfica y de procesamiento del videojuego, en determinados momentos podría bajar. Por este motivo es importante poder conocer en todo momento cuánto tiempo ha transcurrido desde la anterior actualización hasta la actual. Esto es lo que se conoce como _delta time_, y el motor Unity nos lo proporciona en segundos en la propiedad `Time.deltaTime`:. Un uso habitual de esta propiedad es la actualización de la posición de los objetos en la escena. Si sabemos la velocidad de un objeto, la posición que ocupaba en el fotograma anterior, y tenemos el tiempo transcurrido desde dicho fotograma, podemos calcular la nueva posición con:

```
posicion = posicion + velocidad * Time.deltaTime;
```

### Acceso a los componentes y polimorfismo

Como hemos comentado anteriormente, Unity sigue una arquitectura orientada a componentes. El comportamiento de los objetos lo definen los componentes que incorporan, y hemos visto que los _scripts_ son un tipo de componente más. Por lo tanto, para poder modificar las propiedades de los objetos desde el código de los _scripts_ deberemos ser capaces de acceder a los diferentes componentes que incorpora el objeto. Algunos de los componentes a los que nos puede interesar acceder son:

| Componente | Descripción |
| :--- | :--- |
| Transform | Nos permitirá cambiar la posición, orientación y escala de un objeto. Es un componente básico para mover los objetos en la escena. |
| Renderer | Nos permite cambiar el material y la apariencia de un objeto. |
| AudioSource | Nos permite reproducir _clips_ de audio desde un determinado lugar de la escena. |
| Camera | Nos permite configurar la cámara, como por ejemplo el campo visual de la misma. |
| Light | Nos permite cambiar las propiedades de las luces, como por ejemplo cambiar la intensidad o color de las mismas. |

Uno de los componentes que más utilizaremos será `Transform`, que será el que nos permita cambiar la posición de los objetos en la escena. Podemos obtener el componente de la siguiente forma:

`Transform transform = GetComponent<Transform>();`

El método `GetComponent` nos devolverá el componente que indiquemos del _Game Object_ sobre el que estemos, o `null` si este _Game Object_ no tuviese ningún componente de este tipo. De esta forma podremos comprobar si nuestro objeto \(el objeto sobre el que apliquemos nuestro _script_\) tiene o no un determinado componente. Una vez obtenido el componente, podremos acceder y modificar sus propiedades. Por ejemplo, en el caso del componente `Transform` podríamos modificar su posición, para así mover el objeto:

`transform.position = new Vector3(0,0,5);`

Cuando vayamos a utilizar en repetidas ocasiones un determinado componente, es conveniente que lo guardemos en uno de los campos de nuestra clase, para de esta forma no tener que volver a obtenerlo cada vez. Este es habitualmente el caso de `Transform`, que podríamos guardarlo al inicializar nuestro objeto de la siguiente forma:

```
private Transform m_transform;

void Start () {
    m_transform = GetComponent<Transform>();
}
```

Será recomendable hacer esto para cualquier componente que vayamos a utilizar en repetidas ocasiones.

Si nuestro _script_ requiere que el Game Object sobre el que se aplica tenga un determinado componente para poder funcionar correctamente, podemos añadir la siguiente directiva en la clase del _script_:

```
[RequireComponent(typeof(Renderer))]
public class JugadorScript : MonoBehaviour {
    ...
}
```

En el ejemplo anterior sólo podremos añadir nuestro script `JugadorScript` a _Game Objects_ que tengan un componente `Renderer`. En caso de no tenerlo, el entorno no nos permitirá añadir nuestro _script_ como componente. De esta forma estaremos garantizando que cuando solicitemos dicho componente mediante `GetComponent<Transform>()`, éste existirá, y no nos devolverá `null`.

### Parametrización del script

Para hacer nuestro _script_ reutilizable en diferentes contextos, podemos parametrizarlo de forma que desde el propio entorno de Unity al añadirlo a un objeto podamos modificar desde el inspector las diferentes propiedades que hayamos definido.

Para parametrizar un _script_ simplemente deberemos añadir una propiedad pública a la clase del _script_, como por ejemplo:

```
public Vector3 posicionInicial;

void Start () {
    GetComponent<Transform>().position = posicionInicial;
}
```

Al añadir dicha propiedad posicionInicial y grabar el _script_, cuando pasemos al entorno de Unity veremos que en el bloque destinado al componente de dicho _script_ en el Inspector habrá aparecido un campo para editar el valor de la propiedad.

### 

### Interfaz pública del script

### Búsqueda de objetos

### Creación y destrucción de objetos

### Corrutinas



