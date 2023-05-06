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
	- Al crear el    /message   y el       `version.php`       moodle ya nos solicita la instalacion
		- Q mas q nada es el upgrade de la moodle db
			- Esto se puede hacer desde el CLI:     `php admin/cli/upgrade.php`


	- -- Creamos el     `lib.php`
		- Moodle nos provee hooks o callbacks que podemos usar
			- Los      `output callback`    
			- Entonces en este    lib.php    se colocan callbacks
			- Para agregar Notificaciones podemos hacerlo aqui ya q desde ese lib podemos acceder al  _before_footer()
				- Este tipo de notificaciones son aquellas q No obedecen a las q normalmente se usan en la redireccion
					- Simplemente son notificaciones

		-- Creamos el      `local_message_before_footer`    q nos permitira usar ese hook para agregarlo antes del footer
			- Este hook se Ejecutara cada vez q Moodle Renderice la Pagina
  			- Para probarlo podemos crear 1    alert   y veremos q al hacer refresh, este aparece
  			- Y esto se ejecutara previo a renderizar la page

		-- Esto funciona xq este hook llama al     outputrenderers.php    y de ese file invoca al  footer()	
			- Y antes de renderizar el    footer    busca todos los     lib.php    de los plugins q contengan una function q termine con     before_footer
  			- Y cuando la encuentra, la llama
			



	- -- Ahora vamos a crear 1 FORM en donde el admin pueda crear notificaciones
		- Vamos a guardar esa notificacion en 1 nueva Table propia de nuestro plugin
			- Esta notificacion sera almacenada en 1 tabla
			- Y cuando el user la vea, almacenaremos ese visto en otra tablae in DB para no volversela a mostrar


		- -- El     `install.xml`     se pasa a inserta en Moodle cuando se instala el plugin, lo creamos en el    /db    del plugin
			- Como vamos a agregarlo luego de haberlo instalado, lo q deberemos hacer es volverlo a instalar luego d haber agregado el     install.xml
			- Este     install.xml     tiene la definicion de la(s) tabla(s) para este plugin en `XMLBD`
			
			- -- Para crear el      `install.xml`    nos basamos en otro existente, q ya tenga el xml basico
				- En este caso nos basamos en el   de   /mod/folder/db/install.xml   y a este lo modificamos
				- La modificamos a conveniencia
				- Una vez terminemos este archivo, Moodle no se entera de q debe crear estas tablas
  				- Asi q debemos indicarselo instalando el Plugin
    				- X eso es importante q si se va a W con tablas, se defina este     install.xml    antes de instalar el plugin

				- -- Dado q se creo mal el name de las tablas, debemos corregirlo	
					- Desisnstalando e instalando
  					- Linea de comandos:  	`php admin/cli/uninstall_plugins.php --plugins=local_message --run`
						 	- En mi instancia en    Docker    NOOOO funca, se va a la shit   >:V
  					- Interfaz grafica




		-- URL
			- local plugins:		https://moodledev.io/docs/apis/plugintypes/local
													https://docs.moodle.org/dev/Local_plugins
			- lib.php:					https://moodledev.io/docs/apis/commonfiles#libphp
			- callback:					https://docs.moodle.org/dev/Callbacks
				- OUTPUT callbacks:		https://docs.moodle.org/dev/Output_callbacks
					- before_footer:		https://docs.moodle.org/dev/Output_callbacks#before_footer
			- Notificaciones:			https://docs.moodle.org/dev/Notifications#Notifications
			- XMLDB:							https://docs.moodle.org/dev/Using_XMLDB#Create_install.xml

		https://moodledev.io/docs/apis/plugintypes/local#adding-site-wide-settings-for-your-local-plugin












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










