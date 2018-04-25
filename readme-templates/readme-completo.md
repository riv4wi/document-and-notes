# What is this about? #
This excercise is about (de que trata el ejercicio)
Un repositorio que pretende ser la guía para recordar, aprender o retroalimentar información sobre distintas áreas de la Ingeniería Informática.


####Status:#####
Work in progress

# How To #
Como interactuar y probar el codigo.

# Installation guide #

## Dependencies ##
- **Apache**: 2.4.x
    - **rewrite_module**
- 
- **PHP**>= 7.0.0
    - **mcrypt**
- **Composer**: 1.1.3

## Installation ##
- Configure Apache virtual host for directory PATH_TO_PROJECT_IN_SERVER/public
- Copy project file to PATH_TO_PROJECT_IN_SERVER

```bash
cd PATH_TO_PROJECT_IN_SERVER
chmod -R 777 storage
chmod -R 777 bootstrap/cache
composer install
mv -v .env.example .env
php artisan key:generate
```

## Technology stack used ##
- **OS** Linux Mint 18.2 Sonya - Cinnamon 3.4.3
- **Apache** 2.4.18 (Ubuntu)1.5.6
- **PHP** 7.0.22-0ubuntu0.16.04.1 (cli) (NTS)
- **Laravel Framework** 5.5.28
- **Composer** 1.5.6
- **Twitter Bootstrap** 4.0
- **JQuery**
- **Inkscape** 0.91 r13725 (For logo development)


	    public function handle($request, Closure $next)
    {
	        // Obtenemos el api-key que el usuario envia
	        $key = $request->headers->get('api_key');
	        // Si coincide con el valor almacenado en la aplicacion
	        // la aplicacion se sigue ejecutando
	        if (isset($key) == env('API_KEY')) {
	            return $next($request);
	        } else {
	            // Si falla devolvemos el mensaje de error
	            return response()->json(['error' => 'unauthorized' ], 401);
	        }
    }


```php
<?php

use Illuminate\Http\Request;

/*
|--------------------------------------------------------------------------
| API Routes
|--------------------------------------------------------------------------
|
| Here is where you can register API routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| is assigned the "api" middleware group. Enjoy building your API!
|
*/

// Route::middleware('auth:api')->get('/user', function (Request $request) {
//     return $request->user();
// });


Route::get('/', 'API\PassportController@status');
Route::post('login', 'API\PassportController@login');
Route::post('register', 'API\PassportController@register');

Route::group(['middleware' => 'auth:api'], function(){
	Route::get('user-details', 'API\PassportController@getDetails');

	Route::resource('locations', 'API\LocationController');
	Route::get('locations/by-name/{name}', 'API\LocationController@showByName');
});
```