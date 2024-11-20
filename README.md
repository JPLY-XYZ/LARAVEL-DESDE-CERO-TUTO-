# LARAVEL-DESDE-CERO (TUTO)
![IMG](https://github.com/user-attachments/assets/c6e02fe6-b96e-409b-a887-3951473eccf4)
CREATED BY JPLY-XYZ FOR DAW 2024/25




# INDICE

## FASE 1: CREACION DEL PROYECTO Y USO DE BASE DE DATOS
###  1.CREACION PROYECTO
###  2.EJECUCION DEL PROYECTO
###  3.MODELOS Y MIGRACIONES
###  4.EDITAR LAS MIGRACIONES
###  5.RELACIONES ENTRE TABLAS
###  6.ORDENAR MIGRACIONES
###  7.USO SEEDER Y FACTORIAS
###  8.ACTUALIZAR DATABASESEEDER.PHP
###  9.EJECUTAR MIGRACIONES Y FACTORIAS
###  10.COMPROBAR DATOS USANDO TINKER O PHPMYADMIN

## FASE 2: AÑADIR FUNCIONALIDAD REAL A LA WEB


# 


# FASE 1: CREACION DEL PROYECTO Y USO DE BASE DE DATOS

## PASO 1: Crear Proyecto
Para crear un proyecto en laravel podemos hacerlo de 2 maneras, usando *composer* o el *comando espcifico de laravel* 

### CREAR PROYECTO CON COMPOSER
Usamos el siguiente comando: 
```bash
composer create-project laravel/laravel nombre-proyecto
```

### CREAR PROYECTO CON EL COMANDO DE LARAVEL
Usamos el comando especifico para crear el proyecto:
```bash
laravel new nombre-proyecto
```
Al usar el comando nos empezara a pedir parametros de configuracion del proyecto:

![LARAVEL 1](https://github.com/user-attachments/assets/13b4cbc4-8d3a-4850-907e-31198f81aab7)

-> KIT DE INICIO

OPT1 [none]
No se instalará ningún kit de inicio, resultando en un proyecto Laravel básico sin configuraciones adicionales.

OPT2 [breeze]
**Laravel Breeze:** Solución ligera para agregar autenticación. Incluye:
- Registro de usuarios
- Inicio de sesión
- Recuperación de contraseñas
- Vistas simples basadas en Blade o componentes como Vue o React.

OPT3 [jetstream]
**Laravel Jetstream:** Kit avanzado para aplicaciones modernas. Incluye todo lo de Breeze, más:
- Gestión de equipos
- Sesiones de usuario
- Soporte para Livewire o Inertia.js.

-> FRAMEWORK DE PRUEBAS

OPT1 [Pest]
- Moderno y minimalista.
- Enfocado en simplicidad y legibilidad.
- Sintaxis limpia y expresiva.
- Compatible con PHPUnit.

OPT2 [PHPUnit]
- Estándar y ampliamente utilizado.
- Sintaxis más detallada y tradicional.
- Ideal para quienes prefieren el enfoque clásico.

![LARAVEL 2](https://github.com/user-attachments/assets/2d4dce59-0fb3-4163-a87a-a4aebf533a4d)

En este paso nos solicita la base de datos que estemos usando, y posteriormente nos pide si queremos hacer una migracion de la base de datos para crear las tablas de usuarios y tal.


## PASO 2: Empezar a trabajar con laravel.
En este paso ya tendriamos creado el proyecto, y podemos empezar a cambiar cosas, para ello debemos abrir la carpeta del proyecto con el editor de texto preferido.

### Lanzar nuestro proyecto
Para iniciar nuestro proyecto y poder acceder desde el navegador debemos ejecutar el comando:

```bash
php artisan serve
```
![LARAVEL3](https://github.com/user-attachments/assets/8da18534-ee64-438f-8f3d-245ea23901fe)

Desde este link entramos en nuestro proyecto.

## PASO 3: Creacion de modelos y migraciones.

### ¿Que es un modelo? *(Generado por IA)*
En Laravel, un modelo es una representación de una tabla en la base de datos que permite interactuar con ella utilizando Eloquent, un ORM que facilita las operaciones CRUD. Los modelos también permiten definir relaciones entre tablas y contener lógica de negocio relacionada con los datos.

### ¿Que es una migracion? *(Generado por IA)*
Una migración en Laravel es una herramienta que permite definir y modificar la estructura de la base de datos de manera programática. Las migraciones facilitan la creación, modificación y eliminación de tablas y columnas, permitiendo mantener un control de versiones de la base de datos y facilitar la colaboración en equipos de desarrollo.


### Creacion de modelos y migraciones
Para crear una modelo y su correspondiente migracion podemos hacerlo de varias maneras, pero la mas comun es hacerlas simultaneamente, para ello usamos el siguiente comando:

```bash
php artisan make:model NombreTabla -m
```
`-m` Indica que se creen las migraciones al mismo tiempo de los modelos.


## PASO 4: Edicion campos de las migraciones.
Como hemos dicho, las migraciones se usan para definir los campos de las tablas de nuestra base de datos, para ello usamos la siguiente estructura:

```php
$table->tipoDato('nombreColumna');
```
![LARAVEL4](https://github.com/user-attachments/assets/07418c96-7f4a-4132-8b14-b545e4b7c13d)

En este ejemplo se ha añadido un campo llamado `name`.

### Tipos de datos en una migración Laravel *(Generado por IA)*


#### Tipos de texto
- `string('nombre_columna', longitud)`: **String** - Cadena de caracteres de longitud variable (por defecto 255 caracteres).
- `text('nombre_columna')`: **Text** - Cadena de caracteres de longitud larga, ideal para textos extensos.

#### Tipos numéricos
- `integer('nombre_columna')`: **Integer** - Número entero (4 bytes).
- `bigInteger('nombre_columna')`: **Big Integer** - Número entero grande (8 bytes).
- `smallInteger('nombre_columna')`: **Small Integer** - Número entero pequeño (2 bytes).
- `tinyInteger('nombre_columna')`: **Tiny Integer** - Número entero muy pequeño (1 byte).
- `float('nombre_columna', precisión, escala)`: **Float** - Número de punto flotante (4 bytes).
- `double('nombre_columna', precisión, escala)`: **Double** - Número de punto flotante de doble precisión (8 bytes).
- `decimal('nombre_columna', precisión, escala)`: **Decimal** - Número decimal con precisión y escala definidas.

#### Tipos de fecha y hora
- `date('nombre_columna')`: **Date** - Fecha (sin hora).
- `dateTime('nombre_columna')`: **DateTime** - Fecha y hora.
- `time('nombre_columna')`: **Time** - Hora (sin fecha).
- `timestamp('nombre_columna')`: **Timestamp** - Marca de tiempo (fecha y hora).

#### Tipos binarios y JSON
- `binary('nombre_columna')`: **Binary** - Datos binarios.
- `json('nombre_columna')`: **JSON** - Almacena datos en formato JSON.
- `uuid('nombre_columna')`: **UUID** - Almacena un identificador único universal.

#### Tipos enumerados
- `enum('nombre_columna', ['valor1', 'valor2', 'valor3'])`: **Enum** - Valor que puede ser uno de los valores enumerados.
- `set('nombre_columna', ['valor1', 'valor2', 'valor3'])`: **Set** - Conjunto de valores, donde se pueden seleccionar múltiples valores de la lista.

## PASO 5: Relaciones entre tablas

### Relacionar Tablas en **Migraciones**
En caso de querer una relacion 1 a N debemos asignar un campo a que sea la clave foranea de otra tabla.

Debemos usar la siquiente estructura:
```php
$table->unsignedBigInteger('id_rol')->nullable();
$table->foreign('id_rol')->references('id')->on('rols');
```
![LARAVEL5](https://github.com/user-attachments/assets/290a3e57-af2d-4a0f-9d3d-65c1ea4c57e1)

En este ejemplo estmos relacionando la tabla users con mi tabla tasks, trayendonos la id del usuario como clave foranea ademas indicando que cuando un usuario se borre se borren las tareas. 

### Relacionar Tablas en **Modelos**
Para hacer una relacion desde el modelo, debemos realizar estos pasos dependiendo del tipo de relacion necesaria.

Relación 1 a Muchos **(hasMany)**:
```php
public function nombreRelacion(): HasMany
{
    return $this->hasMany(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```

![LARAVEL5](https://github.com/user-attachments/assets/55114836-f428-46aa-879f-deb989eef730)


Relación Muchos a Muchos o 1 a 1 **(belongsTo)**:
```php
public function nombreRelacion(): BelongsTo
{
    return $this->belongsTo(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```

![LARAVEL6](https://github.com/user-attachments/assets/d11a5ff0-ba27-4ce0-a573-c81097bb1f6e)


## PASO 6: Modificacion del orden de las migraciones.
Las migraciones se crean segun se encuentren, en caso de que una tabla tenga que ser creada antes que otra, para ello debemos modificar el nombre de nuestra migracion, y añadir algunn numero.

![LARAVEL7](https://github.com/user-attachments/assets/ef8a92df-7180-42ea-a66c-7c2275188f01)

En este caso quiero que la tabla tasks se cree despues de usuarios, para ello he añadido varios 1 al inicio


## PASO 7: Insertar datos en la base de datos mediante Seeders o Factorias

### ¿Que es un seeder? *(Generado por IA)*
Un seeder en Laravel es una clase que permite llenar la base de datos con datos de prueba o iniciales de manera automática. Se utiliza para crear registros en las tablas de la base de datos de forma rápida y sencilla durante el desarrollo.
### ¿Que es una factoria? *(Generado por IA)*
Una factoría en Laravel es una herramienta que permite generar instancias de modelos con datos falsos o de prueba de manera sencilla. Se utiliza junto con el paquete Faker para crear datos aleatorios y realistas, facilitando así la creación de registros en la base de datos durante las pruebas o el desarrollo.

### Creacion de un seeder
Para crear un seeder debemos usar el siguiente comando:
```bash
php artisan make:seeder NombreSeeder
```
Una vez creado el seeder, debemos editarlo para añadir los datos que queramos introduccir usando la siqiuente estructura.
```php
$user = new NombreClase();
$user->atributo = 'valor';
$user->save();
```
`$user` puede ser cambiado por cualquier nombre.

Hay que recordar que si no ponemos `->save();` los datos no se introducciran en la base de datos.

![LARAVEL8](https://github.com/user-attachments/assets/cdf512ff-7c74-411b-b2d5-cb2588a05778)

### Creacion de una factoria
Para crear una factoria debemos usar el siguiente comando:
```bash
php artisan make:factory NombreFactory
```

En las factorias se usa la clase `Faker`, esta es usada para generar datos de manera aleatoria usando la siguiente estructura:
```php
'nombreDato' => $faker->tipoDato,
```
![LARAVEL9](https://github.com/user-attachments/assets/9e48ca7b-17c7-48d4-9a10-675f825eb50f)

#### Tipos de datos en Faker *(Generado por IA)*

<h5> 1. Texto </h5>

- `name()`: Nombre completo.
- `firstName()`: Primer nombre.
- `lastName()`: Apellido.
- `title()`: Título (Sr., Sra., etc.).
- `sentence($nbWords = 6)`: Oración.
- `paragraph($nbSentences = 3)`: Párrafo.
- `word()`: Palabra aleatoria.
- `text($maxNbChars = 200)`: Texto aleatorio.

<h5> 2. Números </h5>

- `randomNumber($nbDigits = null)`: Número aleatorio.
- `randomFloat($nbMaxDecimals = null, $min = 0, $max = null)`: Número de punto flotante aleatorio.
- `numberBetween($min, $max)`: Número aleatorio entre dos valores.
<h5> 3. Fechas </h5>
 
- `date($format = 'Y-m-d', $max = 'now')`: Fecha.
- `dateTime($max = 'now')`: Fecha y hora.
- `dateTimeBetween($startDate = '-1 years', $endDate = 'now')`: Fecha y hora entre dos fechas.
<h5> 4. Direcciones </h5>

- `address()`: Dirección completa.
- `city()`: Ciudad.
- `country()`: País.
- `postcode()`: Código postal.
- `streetName()`: Nombre de la calle.
- `streetAddress()`: Dirección de la calle.
<h5> 5. Contactos </h5>

- `email()`: Correo electrónico.
- `phoneNumber()`: Número de teléfono.
- `userName()`: Nombre de usuario.
<h5> 6. Datos de empresa </h5>

- `company()`: Nombre de la empresa.
- `jobTitle()`: Título de trabajo.
- `catchPhrase()`: Frase publicitaria.
<h5> 7. Datos de productos </h5>

- `productName()`: Nombre de producto.
- `price($min = 0, $max = null)`: Precio.
<h5> 8. Datos booleanos </h5>

- `boolean($chanceOfGettingTrue = 50)`: Valor booleano.
<h5> 9. Datos de texto de tipo específico </h5>

- `text($maxNbChars = 200)`: Texto aleatorio con un número máximo de caracteres.
<h5> 10. Otros </h5>

- `image($directory = 'public/images', $width = 640, $height = 480)`: Genera una imagen.
- `uuid()`: Genera un UUID.


### PASO 8: Añadir el orden de ejecucion de `DatabaseSeeder.php`
Una vez que ya hemos creado nuestros seeder, o factorias dependiendo de nuestras necesidades, tenemos que añadirlo a nuestro DatabaseSeeder para que se ejecuten al hacer un `php artisan migrate:fresh --seed` para ello usamos la siguiente estructura:

-> SEEDER
```php
$this->call(NombreSeeder::class);
```
-> FACTORIA
```php
 NombreClase()->factory(Cantidad)->create();
```

![LARAVEL10](https://github.com/user-attachments/assets/be7125bc-9296-4628-8547-ccd96c5468f5)

En este ejemplo estamos llamando a los seeders de la clase user y task y estamos usando las factorias de ambas para crear 10.

! Si estamos usando factorias debemos añadir a nuestro modelo la linea `use Hasfactory;`

![LARAVEL11](https://github.com/user-attachments/assets/6f8549fe-b1ba-4826-92dc-1ff32acc0bb6)


## PASO 9: Ejecutar Migraciones y o Factorias con Seed
Ahora que ya hemos configuarado el `DatabaseSeeder.php` podemos ejecutar la migracion, esto actualizara los datos en la base de datos.
```bash
php artisan migrate:fresh --seed
```
Con el `migrate:fresh` estariamos generando las tablas de nuevo.
Al añadir `--seed` estariamos ejecutando los seeder y factorias que esten configuradas.

![LARAVEL11](https://github.com/user-attachments/assets/b5a21540-9017-4b80-9beb-1e31dd010979)

## PASO 10: Comprobar Usuarios en Tinker o PhpMyadmin
En caso de querer comprobar si los datos generados por migraciones o factorias se han insertado en la base de datos podemos usar la herramienta **Tinker** o entrar en el gestor de bases de datos favorito.

### Comprobacion desde gestor de BBDD 

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

### Comprobacion desde Tinker

```bash
php artisan tinker
```
```tinker
use App\Models\NombreModelo;
```
```tinker
NombreModelo::all();
```


# FASE 2: AÑADIR FUNCIONALIDAD REAL A LA WEB

## PASO 1: Configuracion de enrutamiento
Antes de empezar a configurar nada, debemos entender para que sirve el directorio `ROUTES` y el archivo `web.php`. 

Este archivo sirve para indicar todos las rutas de nuestra web.

![LARAVEL12](https://github.com/user-attachments/assets/b8a8ba3e-66a4-4e6e-aa8e-f300d928314a)

Para la configuracion de las rutas de nuestra web debemos usar la siguiente estructura:

```php
Route::get('/', [Controlador::class,'Metodo']);
```
`/` se puede modificar por la ruta necesaria esta es la que usaremos en nuestra web.

![LARAVEL13](https://github.com/user-attachments/assets/6e947397-704e-4d22-9bff-8d7e1d393e5b)

Para el uso de esto, debemos tener claro la estructura, y que estamos usando unos controladores para cada pagina. En estos controladores se esta creando un metodo, el cual devuelve una vista, para ello usamos la siguiente estructura:

```php
 public function NombreMetodo()
    {
        return view('NombreVista');
    }   
```
Debemos modificar el nombre del metodo, acorde a lo que queramos hacer.

![LARAVEL14](https://github.com/user-attachments/assets/3508f4cf-15ac-4988-bccd-aef247969446)

Ahora tenemos que crear la vista, para esto usamos los `documentos.blade.php`

En estos documentos definimos la estructura html que monstraremos.

![LARAVEL15](https://github.com/user-attachments/assets/498cfc66-ea79-4a3e-9062-de2a2c3af3ad)

Un ejemplo de un archivo `web.php` en el que estoy definiendo diferentes rutas.

![LARAVEL16](https://github.com/user-attachments/assets/f911249d-c1db-4be9-82cb-9810a63f3662)

## PASO 2: Instalacion de `livewire` o `brezee` para crear componentes

En este paso empezaremos a crear componentes, para ello debemos usar alguna de estas librerias.

Si no hemos creado el proyecto con el comando `laravel new NombreProyecto`, y lo hemos hecho con composer, debemos instalar el livewire con el siguiente comando:

```bash
php artisan jetstream:install livewire
```

En caso de haber usado el proyecto con el comando `laravel new NombreProyecto` ya habriamos seleccionado la libreria a usar.


## PASO 3: Creacion de vistas personalizadas con su correspondiente controlador
En laravel se usa el modelo vista controlador, para separar la logica de lo que se muestra.

### Creacion controlador

Empezamos creando el controlador de la vista usando el siguiente comando: 
```bash
php artisan make:controller NombreController
```
Con esto estariamos creando un archivo en el que podemos meter metodos para dar funcionamiento a nuestra web.

![LARAVEL17](https://github.com/user-attachments/assets/7978b28e-02c6-4fcc-b45a-8f2c91c5e65b)

En este ejemplo se esta creando un metodo que devuelve la vista `home`.

### Creacion vista

Para crear una vista no existe un comando, debemos hacerlo de manera manual, todas las vistas dependen de una ruta, y para ello se usa la carpeta `wiews`, si nuestra ruta esa en `\NombreRuta`, debemos hacerlo en esta misma carpeta.

![LARAVEL18](https://github.com/user-attachments/assets/b19e5fdc-9bd9-4195-845e-4ce345b55fa2)

En este ejemplo estamos creando la vista `home.blade.php`.

Contenido de la vista:

![LARAVEL19](https://github.com/user-attachments/assets/eceaa013-ba8c-4950-a647-4845796964ce)

En esta imagen se muestra una base de una posible vista, para crearlo automaticamente podemos usar el atajo `!` en visual studio code.

![LARAVEL20](https://github.com/user-attachments/assets/3b3afe9a-52df-411a-879f-d57ef33e31c1)


## PASO4: Creacion de componentes 

Para un desarrollo correcto debemos usar componentes para un mejor orden de la web.

### LIVEWIRE

```bash
php artisan make:livewire NombreDelComponente
```
Con este comando se los crearan 2 archivos.

![LARAVEL21](https://github.com/user-attachments/assets/9c0c60ca-dd90-458f-a9ae-7750d1c80a29)

El primero es el controlador, y el segundo la vista.

Debemos configurarlo a nuestro gusto.

![LARAVEL22](https://github.com/user-attachments/assets/247f76ea-2540-40de-b9e2-fa172ffabc2f)

En este ejemplo hemos añadido el campo `name`, el cual sera accesible desde la vista.

![LARAVEL23](https://github.com/user-attachments/assets/3bc1f25f-5dc4-455c-9f55-f6a95c8437ae)

Todos los componentes tienen que tener un componente raiz, puede ser cualquier etiqueta, normalmente se usa un `div`.

Para el uso de variables dentro de nuestra vista debemos usar la sintaxis:

```html
{{$NombreVariable}}
```
En los componentes podemos usar estructuras de control como:

### Estructuras de control que puedes usar en las vistas de Laravel (Generado por IA)

#### Condicionales
- `@if`: Si una condición es verdadera.
- `@else`: Si la condición no es verdadera.
- `@elseif`: Para agregar otra condición.
- `@unless`: Si la condición es falsa.

#### Bucles
- `@foreach`: Para recorrer una lista de elementos.
- `@for`: Para repetir un bloque un número específico de veces.
- `@while`: Mientras una condición sea verdadera.

#### Switch
- `@switch`: Para manejar múltiples condiciones.
-    `@case`: Define un caso específico.
-    `@default`: Código que se ejecuta si no hay coincidencias.

#### Verificaciones
- `@isset`: Verifica si una variable está definida.
- `@empty`: Verifica si una variable está vacía.
- `@auth`: Si el usuario está autenticado.
- `@guest`: Si el usuario no está autenticado.
- `condición ? valor_si_verdadero : valor_si_falso;`: Operador ternario.


Para añadir este componente a nuesta web debemos usar la siguiente sintaxis:

```html
<livewire:NombreComponente />
```

![LARAVEL](https://github.com/user-attachments/assets/eea38089-4705-4320-be40-9d37fd77c8b6)



### COMPONENTES ANONIMOS


AUN NO DESARROLLADO




## PASO 5: Creacion componentes basicos.
En este paso ya tenemos claro que necesitamos. Aqui hay unos ejemplos de algunas cosas simples.

### TABLA CON MODAL BASICO
Vamos a programrs un componente que contenga una tabla, que al dar a un boton se abra un modal( Un modal es un cuadro de formulario que aparece segun se va necesitando ).

#### Paso 1: Creamos el componente livewire usando el siguiente comando:
```bash
php artisan make:livewire TablaTareasComponent
```

Cuando ejecutemos este comando se nos crearan 2 archivos. 

![LARAVEL](https://github.com/user-attachments/assets/2a9cb859-f531-49e6-afd2-1c35473234ef)

El primeo es su controlador, aqui pondremos la logica, y en el segundo pondremos la parte html, este es la vista.


Una vez hecho esto, debemos ver donde queremos usar este componente, en nuestro caso lo vamos a poner en el dasboard.blade, que es la pagina que vemos una vez estamos logeados en la web, para ello debemos poner la linea:
```blade
<livewire:tabla-tareas-component/>
```
![image](https://github.com/user-attachments/assets/b62131ee-24bb-4d17-8c1c-6f76631f92e6)


Empezamos a trabar con su vista, aqui debemos poner lo que queramos que se vea, en este caso vamos a cojer una tabla de la web: https://flowbite.com/ ya que tiene muchos componentes que usan tailwind gratuitos.

![image](https://github.com/user-attachments/assets/8e11c484-8570-48f4-8a78-3bae85c9ea89)

Copiaremos su codigo y lo pegaremos en nuestra vista.

![image](https://github.com/user-attachments/assets/cfd9c8b6-abf9-4994-9ca5-98321a18351e)

asi ya tendriamos una tabla dentro de nuestro componente, para verlo debemos lanzar nuestra web, y acceder con un usuario.

![image](https://github.com/user-attachments/assets/d6ead550-fe41-42f0-8697-42645eede800)

Si nuestra tabla no se ve igual, debemos ejecutar el comando:

```bash
npm install
npm run dev
```

Este comando ejecuta nustro servidor node, y permite el uso de tailwind.

![image](https://github.com/user-attachments/assets/77f9fd66-b518-4137-9b80-450977ee481a)

una vez lanzado, comprobamos que se ve bien.

en este ejemplo tambien vamos a usar un modal para ello tambien usaremos la web [https://flowbite.com/](https://tailwindui.com/), y elegiremos el que nos guste.

![image](https://github.com/user-attachments/assets/4a6bfabc-e15f-4fb9-9ccb-39817997ff1a)

de la misma manera que la tabla copiaremos su codigo en nuestra vista siempre asegurando que esta dentro del elemento div que nos crea por defecto.

![image](https://github.com/user-attachments/assets/2e3dca83-a374-46e6-adec-7c8b30ea7aaf)

Comprobamos que se vea correctamente.
![image](https://github.com/user-attachments/assets/d005d014-de63-4f7f-b0b7-47b89f5f3051)


Ahora es el momento de empezar a programar. para ello podemos hacerlo de varias maneras. Desde la vista(Logica muy simple) o desde el controlador(Pedir datos a bbdd o comportamiento de variables)

Empezaremos desde la vista.

Vamos a hacer un if para controlar que el modal aparezca o no, para ello buscamos nuestro modal en  la vista y añadimos antes de el la linea:

```blade
@if (false)

-- html de nuestro modal --

@endif
```

![image](https://github.com/user-attachments/assets/10ab54ef-c21c-4d0c-835f-f71fd21a1eff)

En este caso con el false estamos indicando que el modal no se muestre, comprobamos que asi sea.

![image](https://github.com/user-attachments/assets/af320a15-4c97-44b5-8d52-8632c1ed206b)

Ahora tenemos que ver como construimos la tabla, en si una tabla se compone de varas partes:

<h5>table</h5>
Esta etiqueta define la tabla y contiene todos sus elementos.

![image](https://github.com/user-attachments/assets/945e8981-fbd9-47de-b60b-ed6d7da34515)


<h5>thead</h5>
Esta etiqueta es la que conforma todos los datos que no cambian, es decir la parte de arriba de la tabla.

![image](https://github.com/user-attachments/assets/29f7080e-6a51-4177-9fab-1ba0da1ee1e9)

![image](https://github.com/user-attachments/assets/c820a21e-7248-4e6b-889d-e6799395faaa)

Debemos tener claro cuales seran los elementos que se muestran en nuestra tabla.

**tr** Estos elementos son las filas de la tabla.

![image](https://github.com/user-attachments/assets/16dd58d7-2c0f-4bd3-bfcb-5af0f0daf3af)

**td** Estos elementos son la columnas de la tabla

![image](https://github.com/user-attachments/assets/f4a8f165-4171-446e-a304-b48dd76b227b)


Debemos tener claro cuantas columnas debe tener la tabla, porque en el thead siempre habra 1 una fila.

En nuestro caso vamos a usar 4 columnas, 1 para el id de la tarea, otra para el nombre de la tarea y otra para la descripcion de la tarea, y la ultima para los botones.

![image](https://github.com/user-attachments/assets/bbe01b10-c7d9-4be0-ab82-ab3f6dba8be0)

![image](https://github.com/user-attachments/assets/2959f4f5-66bd-4a90-9166-ce960c4e891e)

<h5>tbody</h5>
Esta etiqueta es la que define el cuerpo de la tabla, aqui estan todas las entradas de la misma.

![image](https://github.com/user-attachments/assets/f7a7d949-5744-42a6-8ed4-1cfe1e9b53ac)

![image](https://github.com/user-attachments/assets/1b075284-4d7d-4225-ab0a-0fb168d3eb1d)


**tr** Estos elementos son las filas de la tabla.

![image](https://github.com/user-attachments/assets/ff28d02f-c131-4f5c-a310-430159fb3014)


**td** Estos elementos son la columnas de la tabla

![image](https://github.com/user-attachments/assets/c64daf88-6332-4db5-9b41-0546718092ef)

Empezaremos a modificar estos ultimos, ya que la tabla se creara dinamicamente dependiendo de los datos.

Empezamos viendo que campos debemos tener, ya sabemos cuales seran asique empezaremos añadiendo unos datos de ejemplo:

![image](https://github.com/user-attachments/assets/ed77b9bf-fe2f-4d2c-a3b7-e5f184dc38b5)


![image](https://github.com/user-attachments/assets/7557e370-65f7-4bdb-8420-51a27ca094a9)

Una vez que ya hemos construido la tabla, debemos añadir un boton para crear una nueva tarea, en mi caso lo he hecho fuera de la tabla, a la derecha de la pantalla.

![image](https://github.com/user-attachments/assets/2c231b67-f0f5-4255-885f-fbcf417120e7)


Por el momento nuestra tabla ya tendra una forma asi:

![image](https://github.com/user-attachments/assets/03f5fb28-120e-4795-b113-8cf6d5dba593)



Ahora empezaremos a programar nuesto controlador. Iremos a el y empezaremos creando las variables que vallamos necesitando. 

En este caso crearemos un array de tareas, aqui almacenaremos el listado de tareas que obtengamos de la base de datos:

```php
 public $tasks = [];
```

![image](https://github.com/user-attachments/assets/33c4e970-336d-4a59-b1fa-44f9a8fe3848)

Tras esto haremos una funcion para obtener las tareas de la base de datos, esta la llamaremos mount:

![image](https://github.com/user-attachments/assets/69c43569-74ac-4542-8f87-0ed4e1e80789)

dentro de esta funcion añadiremos la linea de la consulta a la base de datos:

```php
 $this->tasks = Task::where('user_id', Auth::id())->get();
```

Con esta linea estamos almacenando la respuesta de la consulta de la base de datos en nuestra variable tarea.

![image](https://github.com/user-attachments/assets/d28eb113-4090-4f31-b90e-e29a6333233a)

Una vez que ya tenemos esto podemos volver a la vista, para añadir la funcionalidad de cargarlo en la tabla.

Para ello buscamos el tr que contiene los td de la primera entrada, y debemos usar un bucle que recorra la variable $tasks que hemos creado.


![image](https://github.com/user-attachments/assets/4b745eb2-638d-45ce-a7d5-35b9bdb0d33c)

En este caso he usado el for each, usando tasks, y definiendo task por el elemento iterado.

Usando {{$dato->dato}}, he sacado el los datos de cada tarea a su parte para que se muestre en la tabla, en este caso tengo 3 tareas, y se nos ha quedado asi.

![image](https://github.com/user-attachments/assets/0f04451c-d379-44a6-b28d-65b3255af349)






















