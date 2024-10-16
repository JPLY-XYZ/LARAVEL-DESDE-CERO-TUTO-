
# LARAVEL-DESDE-CERO (TUTO)




**PASO 1 -- CREAR PROYECTO**

    sudo composer create-project laravel/laravel nombre-proyecto  //crear el proyecto en htdocks con el xamp encendidosudo

 

**PASO 2 -- DAR PERMISOS AL PROYECTO *(SOLO LINUX)***

`sudo chmod -R 777 nombre-proyecto //damos todos los permisos`

**PASO 3 -- CAMBIAR DATOS DE ACCESO A LA BASE DE DATOS** 

> Entramos al visual studio a nustro proyecto y editamos el arhcivo .env para poner el puerto y el nombre de la base de datos necesario.

**PASO 4 -- INSTALAR DEPENDENCIAS DEL JETSTREAM AL PROYECTO CON COMPOSER**

`sudo composer require laravel/jetstream` 

**PASO 5 -- EJECUTAR EL SERVICIO DEL LARAVEL PARA PODER ACCEDER DESDE UN NAVEGADOR Y USAR EL TINKER**

> Esto debe estar siempre ejecutansode con lo cual debemos ponerlo en otro terminal

`php artisan serve`

**PASO 6 -- CREAMOS LA BASE DE DATOS HACIENDO UNA MIGRACION SIN SEEDER**
//cremos la base de datos

    php artisan migrate

**PASO 7 -- INSTALAMOS EL JETSTREAM A NUESTRO PROYECTO**

 `php artisan jetstream:install livewire`

**PASO 8 -- AHORA TENEMOS QUE HACER UNA MIGRACION CON LOS SEEDER Y NUEVAS TABLAS A LA BASE DE DATOS**

     php artisan migrate:fresh --seed

**PASO 9 --- YA HEMOS INSTALADO TODO LO NECESARIO**

> Aqui ya tenemos el proyecto funcando y con el login funcionando

**PASO 10 -- CREAMOS LOS MODELOS Y MIGRACIONES  -> TODOS LOS MODELOS TIENEN QUE ESTAR CON LA PRIMERA LETRA EN MAYUSCULA -> *Ejemplo***

> Una migracion sirve para crear la estructura de una base de datos y un modelo define relaciones con otras tablas y los datos que se van a extraer de la base de datos

 php artisan make:model nombreTabla -m

**PASO 11 -- CAMBIAMOS ORDEN SI ES NECESARIO DE LAS MIGRACIONES**

> Esto se va a realizar en caso de necesitarlo ya que depende de las relaciones de nustra base de datos

*Vamos a nuestra carpeta migraciones y cambiamos el orden necesario.*

**PASO 12 -- EMPEZAMOS A MODIFICAR LAS MIGRACIONES QUE ACABAMOS DE HACER**

> Aqui vamos a añadir los campos que necesesitemos a nuestras tablas

 

*Para añadir cualquier campo debemos poner un* `$table = tipoDato('nombreDelDato');`

**PASO 13 -- EMPEZAMOS A MODIFICAR LAS MIGRACIONES EXISTENTES**

> Aqui vamos a añadir mas campos a la base de datos depende de cada caso lo que necesitemos

*En un caso en el que queramos setear una relacion con otra base de datos añadimos:*

    $table->unsignedBigInteger('id_rol')->nullable();
    $table->foreign('id_rol')->references('id')->on('rols');

**PASO 14 -- MODIFICAMOS LOS MODELOS PARA AÑADIR LAS RELACIONES**

> Nos vamos al modelo creado y añadimos los campos hidden para que se oculten los atributos, normalmente se suelen poner solo contraseñas o tiempos de creacion.

 

    protected $hidden = ['atributo', 'atributo'];

> Ahora vamos a poner las relaciones entre una tabla y otra, debemos poner el nobre de las funciones en plural, acabado en s

**HASMANY** *-> Es una relacion uno a muchos usada para cuando un modelo tiene relacion con otros muchos modelos*
   

public function nombreTablaDeLaRelacion(): HasMany
    {
        return $this->hasMany(objetoTablaRelacion::class, 'claveForanea', 'claveForaneaReferencia');
    }

**BELONGSTO** *-> Es una relacion muchos a uno usada cuando uno o muchos modelo tiene relacion con otro modelo*

    public function nombreTablaDeLaRelacion(): BelongsTo
    {
        return $this->belongsTo(objetoTablaRelacion::class, 'claveForanea', 'claveForaneaReferencia');
    }


**PASO 15 -- HACER LOS SEDDERS  -> TODOS LOS SEEDER TIENE QUE EMPEZAR EN MAYUSCULA Y EL SEEDER EN EL PALABRA -> *EjemploSeeder***

> Desde un seeder vamos a introduccir datos a una tabla

 `php artisan make:seeder NombreSeeder`

**PASO 16 -- MODIFICAR SEEDER**

> Vamos a ir creando objetos en estos seeders, para meter datos a mano, o podemos usar la funcion `NombreModelo::factory(10)->create();` para hacer automaticamente aleatoriamente el numero indicado

*Añadir datos de manera manual:*

    $user = new nombreClase();
    $user => atributoAModificar = 'informacion';
    $user->save();


**PASO 17 -- MODIFICAMOS EL DATABASESEEDER**

> Aqui tenemos que modificar el seeder de la base de datos, aqui tenemos que poner el orden en el que se ejecutan los serders creados

     $this->call(nombreDelSeeder::class);

**PASO 18 -- CREAMOS UNA FACTORIA -> TODOS LAS FACTORIAS TIENE QUE SER EN MAYUSCULAS LA PRIMAERA LETRA Y QUE PONGA FACTORY EN EL NOMBRE -> *EjemploFactory***

> Creamos una factoria para insertar los datos de manera aleatorios


    php artisan make:factory NombreFactory

*Añadimos las lineas que generan aleatoriamente los datos*

    'nombreDato'=>faker->tipoDato


**PASO 19 -- EJECUTAMOS UNA MIGRACON CON FRESH**

     php artisan migrate:fresh --seed

**PASO 20 -- AHORA COMPROBAMOS QUE SE HAN CREADO LOS USUARIOS**

    php artisan tinker

    use App\Models\NombreModelo
    
    NombreModelo::all();
