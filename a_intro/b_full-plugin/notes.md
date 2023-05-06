# Moodle developer tutorial - full plugin

## Intro
- --- Lo q se curbira
	- Creating db tables
	- building pages in moodle using templates
	- creating and handling forms to get user input
	- how to write custom SQL to query moodle
	- display dynamic notifications and callback fn

	- w con formularios
	- w con notificaciones
	- Se va a crear 1 plugin local



## create database tables
- --- Crearemos 1     local plugin
	- Al crear el    /dir   y el       `version.php`       moodle ya nos solicita la instalacion
		- Q mas q nada es el upgrade de la moodle db
			- Esto se puede hacer desde el CLI:     `php admin/cli/upgrade.php`


	- -- Creamos el     `lib.php`
		- Moodle nos provee hooks o callbacks que podemos usar
			- Los los     `output callback`    
			- Entonces en este    lib.php    se colocan callbacks
			- Para agregar Notificaciones podemos hacerlo aqui:
				- Este tipo de notificaciones son aquellas q No obedecen a las q normalmente se usan en la redireccion
					- Simplemente son notificacione


	- -- Ahora vamos a crear 1 form en donde el admin pueda crear notificaciones
		- Vamos a guardar eso en 1 nueva tabla en nuestro complemento
			- Esta notificacion sera almacenada en 1 tabla
			- Y cuando el user la vea, almacenaremos ese visto en DB para no volversela a mostrar

		-- El     `install.xml`     se pasa e inserta en Moodle cuando se instala el plugin, lo instalamos en el    /db    del plugin
			- Como vamos a agregarlo luego de haberlo instalado, lo q deberemos hacer es volverlo a instalar luego d haber agregado el     install.xml
			- Este     install.xml     tiene la definicion de las tabla(s) para este plugin
			- Una






		-- URL
			- lib.php:			https://moodledev.io/docs/apis/commonfiles#libphp
			- callback:			https://docs.moodle.org/dev/Callbacks
				- OUTPUT callbacks:		https://docs.moodle.org/dev/Output_callbacks
					- before_footer
			- Notificaciones:			https://docs.moodle.org/dev/Notifications#Notifications
			- XMLDB:							https://docs.moodle.org/dev/Using_XMLDB#Create_install.xml
				- 
			-


















- --- Project de la sig semana
	- -- Store videos en filesysten con node.js		<--  multer
		- Vanilla JS
		- Socket.io
			- Pensar como ver q estan copiando y en base a ello enviar 1 evento q lo desconecte
		- Sequalize ORM
		- Multer
			- Validar el tipo de archivo como tal, los binarios
		- Ver como transformar el video a una version mas libiana con Node.js
			-	Esto lo suelen hacer con Python
				- Podriamos exponer 1 api q haga esta reduccion de calidad en Python xq es + eficiente
		- 










