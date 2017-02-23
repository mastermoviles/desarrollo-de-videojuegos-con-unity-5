## Realidad Aumentada

Realidad aumentada es la expresión que usamos para referirnos a las tecnologías que nos permiten superponer modelos virtuales en el mundo real. La mayor diferencia con el término realidad virtual es que la realidad aumentada mezcla el mundo virtual y el real, mientras que en la realidad virtual no percibimos el mundo real y estamos immersos en un mundo virtual \(no hay percepción del entorno en el que estamos\).

Si pensamos en la expresión "realidad aumentada" aplicada a dispositivos móviles, se traduce a la capacidad de superponer contenido en el mundo real a través de la cámara del dispositivo. Esto nos permite "mejorar" el mundo real superponiendo información o contenido multimedia. Por ejemplo, apuntar con la cámara de nuestro teléfono a una foto y que nos muestre una ventana 3D a través de la pantalla de nuestro teléfono donde podemos reproducir un vídeo. Cientos de aplicaciones relacionadas se estan utilizando en museos de todo el mundo para mostrar información tridimensional y aportar información adicional de objetos que se exhiben en los museos. Gracias a las pantallas táctiles de nuestros teléfonos, la realidad aumentada también nos proporciona cierta capaz de interacción entre el contenido virtual y el mundo real.

Actualmente la mayoría de tecnologías que permiten "aumentar la realidad" utilizan marcadores con una forma conocida a priori, plano, cubo, cilindro, etcétera, de forma que el software utilizado es capaz de detectar dicho marcador y mostrar el contenido alrededor del mismo. Pese a que la mayoría utilizan marcadores, cabe destacar que en los últimos años con la aparición de sensores 3D como el dispositivo Kinect de Microsoft, la utilización de marcadores se ha reducido, ya que tenemos información geométrica del entorno \(mundo real\) y por lo tanto podemos superponer información 3D de forma precisa. Debido a que la mayoría de dispositivos móviles no disponen de sensores 3D, la mayoría de tecnologías para "aumentar la realidad" en estos dispositivos se basan en la utilización de marcadores. En él ultimo año, han aparecido varios dispositivos móviles con capacidad de aumentar la realidad, el primero de ellos es un proyecto de la empresa Google, conocido como project Tango, el cual propone un disposito móvil con cámara 3D capaz de mapear el entorno y superponer contenido. El otro proyecto a destacar ha sido desarrollado por la empresa Microsoft y se llama HoloLens. Este es un casco de realidad aumentada o realidad mixta como ellos lo denominan. Este dispositivo móvil es capaz de mapear el entorno y visualizar contenido tridimensional en nuestro entorno como si de verdad estuviera ahí.

Por último mencionar que existen otras tecnologías de realidad virtual basadas en posicionamiento GPS, de forma que utilizando las coordenadas proporcionadas por un sistema GPS habilitan en ciertos lugares la visualización de cierta información adicional utilizando la cámara del dispositivo móvil.

![Ejemplo de realidad aumentada](imagenes/realidad_aumentada/ra_ejemplo_00.jpg)

### Librerías de realidad aumentada

Actualmente existen varias librerías de realidad aumentada que nos permiten desarrollar aplicaciones para smartphones, tablets e incluso gafas de realidad aumentada. A continuación vamos a revisar las características de algunas de estas librerías.

#### DroidAR

[DroidAR](https://github.com/bitstars/droidar) es una librería open-source para Android que nos ofrece funcionalidades de realidad aumentada mediante la detección de puntos de interés \(basada en localización GPS\) así como la detección de marcadores. Mediante el uso de la librería [**libGLX**](https://github.com/libgdx/libgdx/) además permite cargar modelos 3D y animaciones para visualizar mediante marcadores o la localización del dispositivo. Destacar que la documentación de esta librería no es demasiado extensa y no aporta mucha información útil. En los últimos dos años no se ha actualizado mucho, de hecho basado en DroidAR ha aparecido la librería DroidAR 2 de código cerrado que ofrece nuevas y mejoradas funcionalidades respecto al proyecto original.

#### Vuforia

[Vuforia](https://www.vuforia.com/) es otra librería de realidad aumentada desarrollada por la empresa Qualcomm. En 2015 Qualcomm vendió la plataforma a otra empresa estadounidense que ha continuado desarrollando la misma. Vuforia proporciona múltiples formas de ofrecer realidad aumentada a través de marcadores 2D/3D, múltiple detección de marcadores de forma simultánea, posicionamiento, etcétera. Vuforia ofrece soporte para las plataformas iOS y Android de forma nativa, a su vez ofrece un plugin para Unity de forma que podemos desarrollar nuestra aplicación de realidad aumentada en Unity y posteriormente desplegarla en aplicaciones de Escritorio, MACOSX, Windows 10, Android e iOS. Además ofrece soporte para otros dispositivos móviles, como las gafas de realidad aumentada de EPSON \(Epson Moverio BT-200\), gafas de realidad virtual Samsung GearVR e incluso recientemente han dado soporte para el dispositivo de realidad aumentada Microsoft HoloLens. Vuforia ofrece licencias para desarrollar proyectos personales sin fines comerciales, de forma que podemos crear facilmente apps con funcionalidades de realidad aumentada. Si queremos comercializar nuestra app tendremos que adquirir una licencia.

#### Wikitude AR

[Wikitude AR](http://www.wikitude.com/products/wikitude-sdk/) es una librería comercial \(ofrece período de prueba\) de realidad aumentada. Permite el reconocimiento de imagenes y seguimiento de las mismas, así como visualización de modelos 3D y animaciones. También ofrece detección basada en la geolocalización del dispositivo. Wikitude AR SDK esta disponible para Android, iOS, Unity, Google Glass, Epson Moverio, Vuzix M-100, plugin para la librería PhoneGap y también un componente de Xamarin.

### Desarrollando una aplicación de Realidad aumentada con Vuforia

En este curso vamos a centrarnos en la librería Vuforia, ya que además de ofrecer compatibilidad con múltiples plataformas, su integración con Unity es muy sencilla y nos permite facilmente crear aplicaciones de realidad aumentada. Además, dispone de licencias personales que podemos utilizar sin restricciones para el desarrollo de nuestras aplicaciones.

Lo primero que tenemos que hacer para empezar el desarrollo de una aplicación de realidad aumenta con Vuforia es registrarnos en su [página web](https://developer.vuforia.com/) \([https://developer.vuforia.com/](https://developer.vuforia.com/)\).

![](imagenes/realidad_aumentada/ra_registro_vuforia_00.png)

Una vez registrados recibiremos un correo electrónico para confirmar la cuenta que acabamos de crear. Al identificarnos en el portal de la plataforma veremos varias secciones. Primero debemos ir a la sección "Downloads" para descargar el SDK. En esta sección podemos ver una descripción de las distintas características que el SDK de Vuforia nos ofrece, así como las distintas version para múltiples plataformas. En nuestro caso vamos a descargar la versión para Unity. Al descargar el SDK para Unity nos encontramos un paquete que podemos importar en nuestro proyecto mediante la opción de Unity "import package" o bien simplemente hacer doble click sobre el fichero y se importara en el proyecto que tengamos abierto en ese momento. A continuación mostramos las características que ofrece el SDK de Vuforia.

* **Image Targets**: Detección y seguimiento de marcadores 2D.
* **VuMark**: VuMark es un marcador propio de Vuforia al estilo de códigos QR o similares. La ventaja es que el tracking es más robusto y estable en comparación a utilizar Image Targets.
* **Object Recognition**: Utilización de marcadores 3D: cubos, esferas, cilindros, como objeto a detectar para superponer contenido.
* **Multi Targets**: Detección de múltiples marcadores de forma simultáena permitiendo detectar y seguir varios modelos de forma independiente.
* **User Defined Targets**: Permite crear marcadores 2D personalizados basados en imágenes que el usuario puede subir a la plataforma.
* **Smart Terrain \(Unity only\)**: Permite crear fácilmente escenarios con múltiples marcadores para ofrecer experiencias de realidad aumentada muy vistosas. Esta enfocado a la creación de videojuegos y permite crear fácilmente distintos niveles dentro de nuestro juego o aplicación.
* **Cloud Recognition**: Permite almacenar los marcadores en la nube de forma que no tienen que almacenarse en el dispositivo móvil.
* **Text Recognition**: Utilización de texto como marcador.
* **Frame Markers**: Utilización de marcadores 2D convencionales también conocidos como marcadores fiduciales. Cada marcador codifica un patrón binario que corresponde a un identificador único.

Una vez descargado el SDK e importado en Unity, podemos añadir una cámara de Realidad Aumentada a la escena, de forma que cuando usemos este objeto nos va a permitir detectar y hacer el seguimiento de los marcadores.

Creamos un nuevo proyecto, hacemos doble click sobre el SDK que hemos descargado previamente y a continuación aceptamos que se importe el SDK en el proyecto que acabamos de crear.

![](imagenes/realidad_aumentada/ra_nuevo_proyecto_unity.jpg)

![](imagenes/realidad_aumentada/ra_importar_sdk_vuforia_unity.jpg)

Una vez importamos el SDK dispondremos de una carpeta con el nombre "Vuforia" dentro de los Assets de nuestro proyecto. Esta carpeta contiene una serie de objetos que podemos añadir a nuestra escena. Entre estos objetos encontramos la cámara de realidad virtual que mencionamos anteriormente. Lo primero que tenemos que hacer para habilitar la funcionalidad de realidad aumentada en nuestra aplicación es eliminar la cámara principal que se crea en la escena por defecto al crear un proyecto. Una vez eliminada, hacemos click sobre la carpeta "Vuforia" y nos digirimos a la subcarpeta "Prefabs". Esta carpeta contiene el objeto "ARCamera" que podemos arrastar en nuestra escena. Una vez disponemos de este objeto en nuestra escena  vamos a ver que componentes tiene, para ello hacemos click sobre el objeto en la vista que nos muestra de forma jerárquica los objetos en la escena.

![](imagenes/realidad_aumentada/ra_componentes_ar_camera.jpg)

Vamos a ver los distintos componentes que tiene asociados el objeto "ARCamera" y sobretodo vamos a ver las distintas opciones que nos ofrece el componente "Vuforia Behaviour". Podemos ver que por defecto, la mayoría de componentes se encuentran activados, permitiendo la inicialización del objeto, cargar una base de datos con marcadores, mostrar vídeo de fondo obtenido a través de la cámara del dispositivo o habilitar la característica "Smart terrain" de la librería Vuforia.

Por ahora vamos a centrarnos en el componente "Vuforia Behaviour", podemos ver que en el primer campo o propiedad tiene un campo para introducir una licencia de aplicación. De hecho, si intentamos ejecutar la aplicación sin introducir esta licencia, obtendremos un mensaje de aviso alertándonos de la necesidad de introducir una licencia válida para poder utilizar la cámara de realidad aumentada en nuestra escena. Por ello, antes de continuar tendremos que ir a la plataforma online de Vuforia y obtener una clave para nuestra aplicación.

![](imagenes/realidad_aumentada/ra_license_manager.jpg)

En la pestaña developer de la plataforma online veremos que tenemos disponible una subsección llamada "License Manager", desde esta podemos crear una nueva licencia para nuestra aplicación, tan solo deberemos seguir los siguientes pasos:

* **Elige un tipo de proyecto:** Dependiendo del tipo de aplicación: Development, Consumer o Enterprise tendremos que pagar por nuestra licencia o no. En nuestro caso seleccionaremos el tipo "Development"

* **Definimos un nombre para nuestra app:** como la plataforma nos permite crear múltiples apps es importante poner un nombre identificativo de forma que más tarde podamos relacionar las licencias con las apps que estamos desarrollando.

* **Seleccionamos el tipo de dispositivo:** en este caso tan solo tendremos que diferenciar entre disposito móvil o "eyewear". Dentro de "eyewear" engloban dispositivos como las Microsoft Hololens, EPSON moverio, etcétera.

* **Obtenemos nuestra licencia**: En el caso de que se trate de una licencia comercial tendremos que proveer con un medio de pago para costear la misma, en caso contrario veremos que nuestra licencia se acaba de crear. La licencia de desarrollar tiene algunas restricciones, por ejemplo el número máximo de veces por mes que un marcador puede ser detectado usando nuestra aplicación móvil. Para saltarnos esta restricción tendremos que obtener una licencia comercial.

Una vez creada, nos aparecerá en el gestor de licencias de la plataforma online y podemos hacer click sobre la misma para ver la cadena de texto que representa la licencia de nuestra aplicación. Esta cadena se debe de introducir en el campos que vimos anteriormente del componente "Vuforia Behaviour" en objeto "ARCamera".

![](imagenes/realidad_aumentada/ra_license_vuforia.jpg)

Trás introducir la licencia veremos que podemos ejecutar nuestra aplicación en Unity y si nuestro ordenador dispone de una cámara compatible podremos ver video en directo en la escena Unity.

Lo siguiente que tenemos que hacer es habilitar el uso de marcadores y definir el marcador que vamos a reconocer en nuestra aplicación para suponer contenido.

Si es la primera vez que creamos una aplicación, tendremos que irnos a la plataforma online y crear un nuevo "Target" que va a ser reconocido en nuestra aplicación. Si por el contrario ya dispusieramos de algún marcador creado previamente para otro proyecto usando la librería Vuforia, podríamos copiarlo y reutilizarlo en este nuevo proyecto. En nuestro caso vamos a la pestaña "Develop" de la plataforma online y hacemos click sobre la sección "Target Manager". Una vez dentro el sistema nos ofrecela posibilidad de crear una nueva base de datos con marcadores para nuestra aplicación. Al pinchar en añadir nos preguntará donde va a residir el marcador: Device, Cloud o VuMark. Seleccionaremos Device ya que queremos almacenar los marcadores en el propio dispositivo. Una vez creada la base de datos podemos crear distintos marcadores que posteriormente usaremos en nuestra aplicación.

Al añadir un marcador tendremos que seleccionar una serie de opciones, primero de todo el tipo de marcador, una imagen, cubo 3D,  cilindro incluso nos permite utilizar un objeto. En todos los casos  es importante además que el tipo de marcador tenga una textura o patrón que permita que los algoritmos de visión por computador para seguimiento de características visuales puedan detectar y hacer el seguimiento de forma correcta. A continuación seleccionaremos el fichero de la imagen a utilizar y el ancho en unidades unity que queremos que nuestro marcador tenga en la escena. Este parámetro deberá estar en la misma escala que el contenido que vamos a visualizar sobre el marcador. El alto se computará a partir del ancho introducido. Por último le daremos un nombre a este marcador ya que podremos reutilizarlo para otras aplicaciones.

![](imagenes/realidad_aumentada/ra_nuevo_marcador_vuforia.jpg)

Al crearlo, la plataforma online procesará la imagen que hemos subido y nos dará una valoración sobre la calidad de la imagen para ser utilizada como marcador. Como podemos imaginar, si la imagen utilizada no tiene suficientes características visuales \(textura\) el sistema le dará una calificación baja y como consecuencia la detección y el seguimiento del marcador no serán muy estables. La tecnología Vuforia se basa en la utilización del algoritmo SURF, ampliamente conocido en la comunidad de visión por computador, para detectar una determinada textura en la escena. En nuestro caso, hemos subido una textura sugerida por la librería Vuforia, la podemos encontrar en su página web y ofrece buenas características visuales para un correcto funcionamiento. Más adelante, probaremos a subir nuestras propias imágenes y ver qué tal funcionan. Si vamos al listado de marcadores que hemos subido y hacemos click sobre el que acabamos de crear, podemos ver además de la valoración que nos ofrece la plataforma, las características visuales que ha detectado.

![](imagenes/realidad_aumentada/ra_caracteristicas_visuales_marcador.jpg)

En el siguiente enlace encontramos algunos ejemplos de imágenes que Vuforia recomienda: [https://developer.vuforia.com/sites/default/files/sample-apps/targets/imagetargets\_targets.pdf](https://developer.vuforia.com/sites/default/files/sample-apps/targets/imagetargets_targets.pdf)

El siguiente paso para utilizar este marcador en el proyecto Unity que creamos previamente es descargarlo desde la plataforma online e importarlo de igual forma que hicimos con el SDK de Vuforia. Deberemos seleccionar la opción de descarga para la plataforma Unity.

![](imagenes/realidad_aumentada/ra_descargar_bd_marcador.jpg)

Una vez importados ambos paquetes en Unity vamos a repasar la estructura de Assets que tenemos en nuestro proyecto relacionados con el SDK de Vuforia:

* **Editor:** Contiene los scripts que necesitemos para interactuar de forma dinámica con los marcadores que tengamos en nuestra aplicación.
* **Plugins:** Contiene los binarios Java y otros binarios nativos que integran el SDK de Vuforia con las aplicaciones de Unity para Android o iOS.
* **Vuforia:** Contiene los scripts y prefabs requeridos para implementar funcionalidades de realidad aumentada en tu aplicación Unity.
* **Streaming Assets/QCAR** \* Contiene la base de datos y su configuración, de marcadores para nuestro dispositivo en formato XML y DAT \(fichero importado de la plataforma online para gestionar marcadores\).

Volviendo al proyecto Unity que hemos creado, como ya disponemos de una cámara de realidad aumentada en nuestra escena, tan solo nos quedaría incluir un objeto "ImageTarget" en nuestra escena y configurar algunos valores en los scripts de estos objetos. Por lo tanto, arrastramos un objeto "ImageTarget" a la escena. Este objeto lo encontramos dentro de la carpeta Vuforia/prefabs dentro del explorador del proyecto en Unity.

Una vez añadido deberemos configurar algunos de los componentes de este objeto. El componente "Mesh Renderer" nos permite cambiar algunos efectos gráficos sobre los modelos que vamos a visualizar sobre el marcador. Por ejemplo, si los modelos que cuelguen de este objeto proyectan sombras o si podemos proyectar sombras sobre el modelo en sí.

![](imagenes/realidad_aumentada/ra_componentes_image_target.jpg)

Para que el marcador funcione en nuestra aplicación y sea detectado debemos seleccionarlo en el componente "Image Target Behaviour". Este script nos permite seleccionar el marcador que previamente creamos e importamos en nuestro proyecto, así como configurar algunas opciones del mismo. Por ahora, simplemente seleccionaremos nuestro marcador de la lista despegable "Database". Con esto ya tenemos nuestra aplicación lista para detectar el marcador definido. Para probarla, añadimos en la escena un modelo 3D, por ejemplo una esfera, y la posicionamos en la escena cerca del marcador que hemos puesto anteriormente.

![](imagenes/realidad_aumentada/ra_escena_unity_marcador_esfera.jpg)

Unity nos permite crear aplicaciones multiplataforma, por lo que podremos generar aplicaciónes para los siguientes sistemas: Windows, OSX, Android, iOS, tvOS, Tizen, webGL, Xbox One, PS3, PS4, etcetera. Si tenemos una cámara compatible en el ordenador donde estamos desarrollando la aplicación, podremos probar nuestra aplicación de realidad aumentada simplemente pulsando el botón de "Play" en la parte superior.

A continuación vamos a ver como generar la aplicación para Android o iOS.

#### Desplegando aplicación Unity en Android

Accedemos al diálogo: "File -&gt; Build Settings". Desde aquí  podemos especificar y configurar la plataforma para la cual queremos generar nuestra aplicación. En el caso de Android, además, primero tendremos que especificar el directorio donde se encuentra el SDK Android y el Java Development Kit \(JDK\). En "Unity -&gt; Preferences -&gt; External tools" deberemos configurar estos directorios.

![](imagenes/realidad_aumentada/ra_unity_external_tools.jpg)

A la hora de desplegar la aplicación en Android, tenemos varias opciones, bien generamos directamente la aplicación en formato .apk o también podemos generar un proyecto para Android Studio y modificarlo posteriormente allí. De esta forma podremos ver código fuentes para la integración de Vuforia en la app Android y hacer modificaciones en la lógica de la aplicación. Para generar el proyecto para Android Studio tendríamos que marcar la casilla "Google Android Project" en "Build Settings".

Además, si pulsamos sobre "Player Settings" podremos definir toda una serie de opciones para la generación de la aplicación en Android. Entre estas opciones encontramos, nombre de la aplicación, icono, opciones de rendering, optimización de codigo GPU, mínima versión de API requerida, lugar de instalación para la app, acceso a Internet, permisos de escritura, etcétera.

![](imagenes/realidad_aumentada/ra_player_settings_android.jpg)

Al pulsar el botón "Build" nos generará el fichero .apk compatible para Android con las opciones marcadas y si pulsamos "Build and Run" buscará un dispositivo Android conectado e instalará y ejecutará la aplicación en el dispositivo.

#### Desplegando aplicación Unity en iOS

Para desplegar la aplicación en iOS, seleccionaremos esa opción en el diálogo "Build Settings". En este caso, en lugar de ejecutar directamente, nos creará un proyecto en para Xcode que utilizaremos para desplegar la aplicación en nuestro dispositivo iOS. Si tratamos de compilar el proyecto que nos acaba de generar Unity, obtendremos un error indicándonos que la aplicación no ha sido firmada y requiere especificar un "Equipo".

![](imagenes/realidad_aumentada/ra_firmar_proyecto_unity_para_ios_xcode.jpg)

Por último, antes de compilar la aplicación y desplegarla en nuestro dispositivo iOS, tendremos que añadir una entrada en la configuración del proyecto con la descripción del uso de la cámara. Por políticas de seguridad con el acceso a la cámara,  los desarrolladores tienen que detallas el uso de la cámara en la aplicación. Cuando la aplicación intente acceder a la cámara el usuario, iOS nos lo informará con un diálogo y nos permira permiso para que la aplicación acceda a la cámara. Por ello en la sección "Info" de la configuración del proyecto, creamos la clave "Privacy - Camera Usage Description" y ponemos una descripción del uso de la cámara en nuestra app: "detección marcadores realidad aumentada".

![](imagenes/realidad_aumentada/ra_project_info_keys_camera_usage_description.jpg)

Ahora podemos compilar y desplegar la aplicación en nuestro dispositivo iOS pulsando el botón "Play" de la parte superior.

### Ejercicio realidad aumentada

Para poner en práctica lo que hemos visto os proponemos el siguiente ejercicio: Vamos a crear una applicación de realidad aumentada para promocionar el máster en desarrollo de software para dispositivos móviles. Utiliza el tríptico del máster para visualizar una serie de modelos 3D sobre este. Además, para poner en práctica lo que hemos aprendido de Unity sobre interfaces 2D en las secciones anteriores, añadiremos una simple interfaz de usuario para poder salir de la aplicación. Añadiremos varios modelos 3D utilizando distintos formatos \(.3ds, .obj, .off, ...\) Los modelos 3D se pueden descargar desde la plataforma Moodle `(assets_ejercicio_realidad_aumentada.zip)`. Utilizando la portada y la parte interior del tríptico crearemos dos marcadores. La detección de cada marcador visualizará un contenido distinto en nuestra aplicación. Por ejemplo, al detectar la portada del tríptico podemos invitar al usuario a abrirlo mostrando texto 3D sobre el marcador y entonces detectar la parte interior del trípico y mostrar un contenido distinto.

Por último, habilitaremos la interacción con los modelos 3D cargados en la escena. Al pulsar sobre cada uno de los modelos, Android, iMac, logotipo curso, visualizaremos una imágen distinta sobre el monitor iMac, por ejemplo, al pulsar sobre Android mostraremos una imagen de Android, al pulsar sobre el monitor visualizaremos una imágen sobre iOS, etcétera. Podemos utilizar un diálogo o simplemente un plano 3D con una textura que se posicionará encima de la pantalla del iMac.

![](imagenes/realidad_aumentada/ra_ejemplo_01.jpg)

### Realidad mixta

Realidad mixta es un término que se utiliza para la combinación de técnicas de realidad virtual y aumentada en tiempo real. Consiste en visualizar el mundo real usando técnicas de realidad virtual. Para ello, normalmente se visualiza el mundo real a través de la utilización de una cámara, o através de pantallas transparentes, cuyo flujo de vídeo se renderiza en entornos de realidad virtual añadiendo contenido virtual y renderizándolo todo usando un par de imágenes estereoscópicas. Utilizando marcadores como los vistos anteriormente, podemos facilmente, usando la cámara, añadir contenido virtual sobre el flujo de vídeo de la cámara y visualizarlo todo a la vez como si estuviera en el mundo real.

También se ha acuñado el término de realidad mixta, a tecnologías como las desarrolladas por Microsoft, Meta, Google o Epson. Estas compañias han desarrollado unos cascos que incorporan pantallas transparentes muy cercanas a los ojos. De esta forma podemos seguir viendo el mundo real, pero a su vez nos permiten visualizar objetos virtuales que son proyectados sobre el mundo real. Ejemplos de productos actuales que implementan esta tecnología son Microsoft Hololens, Meta2 o las Epson Moverio BT-200.

La tecnología Vuforia también es compatible con tecnologías de realidad virtual permitiéndonos crear aplicaciones aplicaciones de realidad mixta. De esta forma, la librería Vuforia permite generar un par de imágenes estereoscópicas que podemos visualizar sobre distintos visores de realidad virtual como el Google Cardboard. De esta forma nuestra aplicación puede alternar entre el mundo real y el mundo virtual.

Utilizando el proyecto que hemos desarrollado anteriormente, podemos fácilmente configurarlo para que genere un par de imágenes estereoscópicas para el Google cardboard y visualizarlo en un entorno más ceracano a la realidad virtual. El flujo de vídeo de la cámara nos permitirá ver lo que hay a nuestro alrededor y detectar el marcador sobre el cual visualizaremos el contenido 3D que hemos posicionado anteriormente. Podemos observar que existe una pequeña latencia entre nuestros movimientos y el flujo de vídeo debido al procesamiento de la imagen antes de ser visualizado en la pantalla de nuestro móvil.

Para configurar el proyecto anterior y que nos permita renderizar un par de imágenes estereoscópicas para el Google Cardboard u otros cascos de realidad virtual, tan solo tenemos que hacer click sobre la cámara de nuestra escena `ARCamera` y modificar las siguientes opciones en el script `DigitalEyeWearBehaviour`:

* **Eyewear Type** = Video See-Through
* **Stereo Camera Config** = Vuforia
* **Viewer Type = Generic Cardboard** \(Vuforia\) or Cardboard v1 \(Google\)

Si desplegamos de nuevo la aplicación en el dispositivo móvil y lo insertamos en el casco de realidad virtual, podremos visualizar la aplicación de realida aumentada que anteriormente desarrollamos de forma más immersiva.

