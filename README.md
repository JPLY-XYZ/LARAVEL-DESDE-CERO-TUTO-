
# LARAVEL-DESDE-CERO (TUTO)




# Guía de Laravel con Comandos Rápidos

## PASO 1: Crear Proyecto
```bash
sudo composer create-project laravel/laravel nombre-proyecto
```

## PASO 2: Configurar el Entorno
Edita el archivo `.env` para configurar la base de datos y otras variables de entorno.

## PASO 3: Generar Clave de Aplicación
```bash
php artisan key:generate
```

## PASO 4: Instalar Dependencias
```bash
composer install
```

## PASO 5: Ejecutar el Servidor Laravel
```bash
php artisan serve
```

## PASO 6: Crear Base de Datos con Migraciones
```bash
php artisan migrate
```

## PASO 7: Instalar Jetstream
```bash
php artisan jetstream:install livewire
```

## PASO 8: Migrar con Seeder
```bash
php artisan migrate:fresh --seed
```

## PASO 9: Proyecto Configurado
El proyecto ya tiene el login funcional.

## PASO 10: Crear Modelos y Migraciones
```bash
php artisan make:model NombreTabla -m
```

## PASO 11: Cambiar Orden de Migraciones
Edita las migraciones si es necesario en `database/migrations`.

## PASO 12: Modificar Migraciones
Añade campos necesarios como:
```php
$table->tipoDato('nombreColumna');
```

## PASO 13: Relacionar Tablas en Migraciones
Ejemplo relación 1 a N:
```php
$table->unsignedBigInteger('id_rol')->nullable();
$table->foreign('id_rol')->references('id')->on('rols');
```

## PASO 14: Modificar Modelos para Relaciones
Relación 1 a Muchos (hasMany):
```php
public function nombreRelacion(): HasMany
{
    return $this->hasMany(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```
Relación Muchos a Uno (belongsTo):
```php
public function nombreRelacion(): BelongsTo
{
    return $this->belongsTo(ModeloRelacion::class, 'claveForanea', 'claveReferencia');
}
```

## PASO 15: Crear Seeder
```bash
php artisan make:seeder NombreSeeder
```

## PASO 16: Modificar Seeder
Inserta datos manualmente:
```php
$user = new NombreClase();
$user->atributo = 'valor';
$user->save();
```

## PASO 17: Modificar DatabaseSeeder
```php
$this->call(NombreSeeder::class);
```

## PASO 18: Crear Factoría
```bash
php artisan make:factory NombreFactory
```
Define datos en la factoría:
```php
'nombreDato' => $faker->tipoDato,
```

## PASO 19: Ejecutar Migraciones Fresh con Seed
```bash
php artisan migrate:fresh --seed
```

## PASO 20: Comprobar Usuarios en Tinker
```bash
php artisan tinker
use App\Models\NombreModelo;
NombreModelo::all();
```
