# ngCordova-ionic
http://ngcordova.com/docs/install/    
https://www.mobomo.com/2015/08/setup-ngcordova-in-ionic/
https://blog.nraboy.com/2014/11/use-sqlite-instead-local-storage-ionic-framework/


ionic setup sass

# Primer Test
// Browser 
ionic serve
// Android Simulator  
ionic platform add android
ionic build android
ionic emulate android --livereload

# Instalamos ngCordova

bower install ngCordova --save-dev 
bower install ng-cordova-ionic -S

> Incluir ng-cordova.js or ng-cordova.min.js en index.html antes de cordova.js 
> y después de AngularJS / Ionic fichero (ngCordova depende de  AngularJS).


````
<script src="lib/ngCordova/dist/ng-cordova.js"></script>
````

# Injectar como Angular depedencia

````
angular.module('myApp', ... ['ngCordova'])

````


# Add the plugin to your project using the Cordova CLI


http://ngcordova.com/docs/plugins/
````
ionic plugin add cordova-plugin-contacts
 ````

# Ejecutar en modo live
````
ionic emulate android -l 
````


# injectar $cordovaContacts servicio en el controlador donde queramos acceder a contactos. 
Account tab, Abrir  www/js/controllers.js, inyectar 

>.controller('AccountCtrl', function($scope, $cordovaContacts) {

# Abrir www/templates/tab-account.html,  y añade 2 botones para cargar un contacto o todos
 
    <button class="button button-positive button-block" ng-click="getContact()">   Get Contact </button>  
    <button class="button button-positive button-block" ng-click="getContacts()">   Get Contacts </button>

#   Finalmente crea las funciones en www/js/controllers.js despues de $scope.settings


````
  $scope.getContact = function() {
     $cordovaContacts.pickContact().then(function(result) {
       console.log(result);
     });
   };
 
   $scope.getContacts = function() {
     $cordovaContacts.find({multiple: true}).then(function(result)     {
       console.log(result);
     });
   };
````  
 
 ERROR:  warn     No Content-Security-Policy meta tag found. Please add one when using the cordova-plugin-whitelist plugin.
