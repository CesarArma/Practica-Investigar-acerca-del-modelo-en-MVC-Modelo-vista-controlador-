
## ¿Qué es el Modelo Vista Controlador (MVC)?

![Modelo Vista Controlador](https://www.precognis.com/wp-content/uploads/2022/08/Modelo-Vista-Controlador.png)


El **Modelo Vista Controlador (MVC)** es un patrón de arquitectura de software utilizado en la programación de aplicaciones de software. En el modelo vista controlador, la lógica de la aplicación se divide en tres componentes principales:

-   El modelo: representa los datos y la lógica empresarial de la aplicación. El modelo se utiliza para recuperar, actualizar y almacenar los datos de la aplicación.
-   La vista: se encarga de la presentación de los datos al usuario y proporciona la interfaz de usuario.
-   El controlador: es el componente que maneja las solicitudes del usuario, interactúa con el modelo y actualiza la vista según sea necesario.

## Modelo de representación de los datos en el Modelo Vista Controlador

El modelo es responsable de representar los datos en la aplicación MVC. Esto significa que el modelo debe definir una estructura de datos para representar los objetos en la aplicación. Por ejemplo, si estamos construyendo una aplicación de gestión de tareas, el modelo puede definir una estructura de datos para representar una tarea que incluya campos como título, descripción, fecha de vencimiento, prioridad, etc.

## Funcionalidades comunes de una aplicación MVC

Las funcionalidades de una aplicación MVC pueden variar según la naturaleza de la aplicación, pero algunas de las funcionalidades comunes incluyen:

-   Registro y autenticación de usuarios.
-   Creación, edición y eliminación de datos.
-   Búsqueda y filtrado de datos.
-   Administración de roles de usuario y permisos.
-   Integración con servicios externos como redes sociales o servicios de pago.

## Infraestructura para el almacenamiento y recuperación de datos en una aplicación MVC

Para definir la infraestructura de almacenamiento y recuperación de datos en una aplicación MVC, es común utilizar una base de datos relacional como MySQL o PostgreSQL. En este enfoque, el modelo se encarga de interactuar con la base de datos para recuperar, actualizar y almacenar los datos de la aplicación. Los datos se pueden representar como tablas en la base de datos, y el modelo utiliza consultas SQL para interactuar con los datos en la base de datos. También es común utilizar un sistema de mapeo objeto-relacional (ORM) como Doctrine o Eloquent para simplificar el proceso de interactuar con la base de datos desde el modelo.

El código Markdown resultante se puede usar para crear documentos de texto formateados de manera clara y fácil de leer sobre el Modelo Vista Controlador y su infraestructura de datos en una aplicación MVC.
##Ejemplos con el MVC dentro de PHP

##### 1. Ejemplo básico de MVC en PHP

Este ejemplo básico de MVC en PHP demuestra cómo se puede implementar el patrón utilizando funciones de PHP para cada componente (modelo, vista y controlador) y una matriz para almacenar los datos del modelo.


~~~// modelo.php
function get_data() {
  return array('nombre' => 'Juan', 'edad' => '30');
}

// vista.php
function render($datos) {
  echo 'Nombre: ' . $datos['nombre'] . '<br>';
  echo 'Edad: ' . $datos['edad'] . '<br>';
}

// controlador.php
$datos = get_data();
render($datos);
~~~

##### 2. Ejemplo de MVC utilizando clases en PHP

Este ejemplo de MVC en PHP utiliza clases para cada componente y una base de datos MySQL para almacenar los datos del modelo.


~~~// modelo.php
class Modelo {
  private $conexion;
  
  function __construct() {
    $this->conexion = new PDO('mysql:host=localhost;dbname=mi_base_de_datos', 'usuario', 'contraseña');
  }
  
  function get_datos() {
    $query = $this->conexion->prepare('SELECT * FROM mi_tabla');
    $query->execute();
    return $query->fetchAll();
  }
}

// vista.php
class Vista {
  function render($datos) {
    foreach ($datos as $fila) {
      echo 'Nombre: ' . $fila['nombre'] . '<br>';
      echo 'Edad: ' . $fila['edad'] . '<br>';
    }
  }
}

// controlador.php
$modelo = new Modelo();
$datos = $modelo->get_datos();
$vista = new Vista();
$vista->render($datos);
~~~

##### 3. Ejemplo de MVC utilizando un framework en PHP

Este ejemplo de MVC en PHP utiliza el framework Laravel para implementar el patrón MVC en una aplicación web.

~~~
// app/Models/Persona.php
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Persona extends Model {
  protected $fillable = ['nombre', 'edad'];
}

// app/Http/Controllers/PersonaController.php
namespace App\Http\Controllers;

use App\Models\Persona;
use Illuminate\Http\Request;

class PersonaController extends Controller {
  function index() {
    $personas = Persona::all();
    return view('personas.index', compact('personas'));
  }
}

// resources/views/personas/index.blade.php
@foreach ($personas as $persona)
  Nombre: {{ $persona->nombre }}<br>
  Edad: {{ $persona->edad }}<br>
@endforeach
~~~

##Vista en el modelo vista, controlador

En las vistas, se reciben los datos del modelo a través del controlador, el cual se encarga de obtener los datos del modelo y enviarlos a la vista correspondiente. A su vez, las vistas envían las acciones del usuario al controlador para que este procese la información y actualice el modelo correspondiente.

Las vistas pueden ser de diferentes tipos, dependiendo de la tecnología utilizada para su implementación. Algunos ejemplos de vistas son:

Páginas web HTML: Las vistas pueden estar implementadas como archivos HTML que se generan dinámicamente con el servidor. En este caso, la vista recibe los datos del modelo y los muestra en la página web.

Interfaces gráficas de usuario (GUI): Las vistas pueden ser implementadas como ventanas o diálogos en una aplicación de escritorio. En este caso, la vista recibe los datos del modelo y los muestra en la GUI correspondiente.

Aplicaciones móviles: Las vistas pueden ser implementadas como pantallas en una aplicación móvil. En este caso, la vista recibe los datos del modelo y los muestra en la pantalla correspondiente.

En resumen, la vista en la arquitectura MVC es la capa encargada de presentar los datos del modelo al usuario y recibir las acciones del usuario para enviarlas al controlador. Las vistas pueden ser implementadas de diferentes formas, dependiendo de la tecnología utilizada para su desarrollo.