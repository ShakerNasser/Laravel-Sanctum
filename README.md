# Laravel-Sanctum

sanctum
logga in i adminer skapa databas
skapa en användare med alla privileger
ändra env till databassens nya databas

Detta är en Guard!
nu måste vi skapa en guard och vad en guard är, jo det är att den säger den vill skydda ett antal routs med ett vist middleware
t.ex. 
inuti web.php
Route::middleware(['auth:sanctum'])->group(function () {
	Route::get('/welcome', function(){
		return view('welcome');
)};

)};
 
middleware är en sorts funktion som tar in ett request gör ngt speciellet som t.ex. kolla om man är inloggad. om man är det skickas man vidare till routesen som middlewaret skyddar. middleware är en mellan personon som kollar om man får gå vidare till nästa steg.

middleware('detta däger vilken slags middleware vi vill använda/gå igenom innan vi når routes')

auth = att man måste vara inloggad innan man får komma åt routsen 

group = betyder på alla routes som finns där inne, det kan även användas för att göra ett prefix innan flera routes 
t.ex.
	Route::get('/welcome', function(){
		return view('welcome');
)};
	Route::get('/landing', function(){
		return view('welcome');
)};

cd in på din map
php artisan migrate 
php artisan serve
composer require laravel/breeze --dev    detta laddar ner ett breeze paket 
php artisan breeze:install
välj blade with Alpine (det som är mest likt det vi håller på med)
darkmode 
phpunit
php artisan migrate
npm install
npm run dev

i web.php så kommer man bara komma åt /dashboard om man är inloggad
men också måste man vara authensiarad om man vill komma åt sin profil detta är gjort via en group för att kunna få flera funktioner 

inuti route/auth.php så kan man välja vilka sidor man kommer åt som t.ex. 'guest'

för att kunna göra flera roller så kan man lässa på mera eller skapa en själv för att vara mer flexibel
själv:
php artisan make:migration
name: add_role_to_users

inuti up funktion
$table->integer('role');

inuti down funktion
if(schema::hasColumn('users', 'role'))
Schema::table('users', function (Blueprint $table) {
$table->dropColumn('role');
});

php artisan migrate 

gå in i app/http/controllers/auth/registeredusercontroller
lägg till under User::create([
'role'=> 1,

gå in på dashboard.blade.php
under 
<div class="p-6 text-gray-900 dark:text-gray-100">
                    {{ __("You're logged in!") }}
                </div>
lägg till
<div class="p-6 text-gray-900 dark:text-gray-100">
                    {{ __("You're logged in as ") }} {{ Auth::user()->role ? {{ __("user") : {{ __("admin") }} **__ betyder att du vill skriva ut en exakt string
? betyder att den tittar om den är true eller false. om den är 1 user 0 admin
                </div>
