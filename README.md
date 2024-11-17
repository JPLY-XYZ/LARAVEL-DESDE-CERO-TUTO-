
# LARAVEL-DESDE-CERO (TUTO)




# Guía de Laravel con Comandos Rápidos

## PASO 1: Crear Proyecto
```bash
sudo composer create-project laravel/laravel nombre-proyecto
```

## PASO 2: Configurar el Entorno
Edita el archivo `.env` para configurar la base de datos y otras variables de entorno.




## PASO 3: Ejecutar el Servidor Laravel
```bash
php artisan serve
```

## PASO 4: Crear Base de Datos con Migraciones
```bash
php artisan migrate
```

## PASO 5: Instalar Jetstream (si es necesario)
```bash
php artisan jetstream:install livewire
```

## PASO 6: Migrar con Seeder
```bash
php artisan migrate:fresh --seed
```

## PASO 7: Proyecto Configurado
El proyecto ya tiene el login funcional.

## PASO 8: Crear Modelos y Migraciones
`-m` Indica que se creen las migraciones al mismo tiempo de los modelos.
```bash
php artisan make:model NombreTabla -m
```

## PASO 9: Cambiar Orden de Migraciones
Edita las migraciones si es necesario en `database/migrations`.

## PASO 10: Modificar Migraciones
Añadir campos necesarios como:
```php
$table->tipoDato('nombreColumna');
```
### Tipos de datos en una migración Laravel

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


## PASO 11: Relacionar Tablas en **Migraciones**
Ejemplo relación 1 a N:
```php
$table->unsignedBigInteger('id_rol')->nullable();
$table->foreign('id_rol')->references('id')->on('rols');
```

## PASO 12: Relacionar Tablas en **Modelos**
Relación 1 a Muchos **(hasMany)**:
```php
public function nombreRelacion(): HasMany
{
    return $this->hasMany(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```
Relación Muchos a Muchos o 1 a 1 **(belongsTo)**:
```php
public function nombreRelacion(): BelongsTo
{
    return $this->belongsTo(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```

## PASO 13: Crear Seeder
```bash
php artisan make:seeder NombreSeeder
```

## PASO 14: Modificar Seeder
Inserta datos manualmente:
```php
$user = new NombreClase();
$user->atributo = 'valor';
$user->save();
```

## PASO 15: Modificar DatabaseSeeder **IMPORTANTE**
En caso de **NO** modificar no se ejecutaran las migraciones
```php
$this->call(NombreSeeder::class);
```

## PASO 16: Crear Factoría
Inserta datos automaticamente:
```bash
php artisan make:factory NombreFactory
```
Define datos en la factoría:
Usar clase Faker para generar datos aleatorios
```php
'nombreDato' => $faker->tipoDato,
```
### Tipos de datos en Faker

#### 1. Texto
- `name()`: Nombre completo.
- `firstName()`: Primer nombre.
- `lastName()`: Apellido.
- `title()`: Título (Sr., Sra., etc.).
- `sentence($nbWords = 6)`: Oración.
- `paragraph($nbSentences = 3)`: Párrafo.
- `word()`: Palabra aleatoria.
- `text($maxNbChars = 200)`: Texto aleatorio.

#### 2. Números
- `randomNumber($nbDigits = null)`: Número aleatorio.
- `randomFloat($nbMaxDecimals = null, $min = 0, $max = null)`: Número de punto flotante aleatorio.
- `numberBetween($min, $max)`: Número aleatorio entre dos valores.

#### 3. Fechas
- `date($format = 'Y-m-d', $max = 'now')`: Fecha.
- `dateTime($max = 'now')`: Fecha y hora.
- `dateTimeBetween($startDate = '-1 years', $endDate = 'now')`: Fecha y hora entre dos fechas.

#### 4. Direcciones
- `address()`: Dirección completa.
- `city()`: Ciudad.
- `country()`: País.
- `postcode()`: Código postal.
- `streetName()`: Nombre de la calle.
- `streetAddress()`: Dirección de la calle.

#### 5. Contactos
- `email()`: Correo electrónico.
- `phoneNumber()`: Número de teléfono.
- `userName()`: Nombre de usuario.

#### 6. Datos de empresa
- `company()`: Nombre de la empresa.
- `jobTitle()`: Título de trabajo.
- `catchPhrase()`: Frase publicitaria.

#### 7. Datos de productos
- `productName()`: Nombre de producto.
- `price($min = 0, $max = null)`: Precio.

#### 8. Datos booleanos
- `boolean($chanceOfGettingTrue = 50)`: Valor booleano.

#### 9. Datos de texto de tipo específico
- `text($maxNbChars = 200)`: Texto aleatorio con un número máximo de caracteres.

#### 10. Otros
- `image($directory = 'public/images', $width = 640, $height = 480)`: Genera una imagen.
- `uuid()`: Genera un UUID.


## PASO 17: Ejecutar Migraciones Fresh con Seed
Con el `migrate:fresh` estariamos generando las tablas de nuevo.
Al añadir `--seed` estariamos ejecutando los seeder y factorias que esten configuradas.
```bash
php artisan migrate:fresh --seed
```

## PASO 18: Comprobar Usuarios en Tinker
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
## PASO 19: Actualmente en desarrollo (17-11-24)

