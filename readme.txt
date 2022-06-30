clase 13 SASS
---------
descargar
https://nodejs.org/es/

crear carpeta nueva

abrirla con visual

abrir la consola ctrlñ

tipear comando:
npm install nodemon node-sass

despues tipear npm init (a continuacion, la metralla de enter)

despues enter hasta que te dice is this OK? (yes)            hay q volver a dar enter

a la izquierda, clic en package.json 

UBICAR  la linea 11 y agregarle una coma al final. Después, agregar estas dos líneas de codigo debajo de "test" y a la misma altura que la 11:

"build-css": "node-sass --include-path scss scss/main.scss css/style.css",
"watch-css": "nodemon -e scss -x \"npm run build-css\""

ahora creamos las 2 carpetas (arriba de todo, a la misma altura que node.modules): 

una es la scss y dentro creamos el archivo main.scss
la otra es la clasica de css con el archivo style.css dentro

este es el paso a paso que nos pasó johana
-------
1. Abrir la consola en esta carpeta con ctrl+ñ. npm install nodemon node-sassb. 
esperar y después: tipear npm init

2. Abrir el archivo package.json y editarlo. A continuación de && exit 1" colocar una coma (,) presionar enter y pegar el siguiente texto:"build-css": "node-sass --include-path scss scss/main.scss css/style.css","watch-css": "nodemon -e scss -x \"npm run build-css\""

3. Crear las carpetas con sus respectivos archivos: 
scss/main.scss 
css/style.css
------------------------

ahora hay que volver a la consola

primero tipear npm run build-css
enter y esperar

despues tipear npm run watch-css
enter y esperar  

hacer el archivo readme.txt

IMPORTANTE: si cierro visual, al reabrirlo (desde la carpeta, con abrir con visual, DEBO volver a escribir en la consola: 
npm run watch-css

------
readme.txt

//COMO EMPEZAR A COMPILAR SASS//

1. Abrir la consola en esta carpeta con ctrl+ña. npm install nodemon node-sassb. npm init

2. Abrir el archivo package.json y editarloa. A continuación de && exit 1" colocar una , presionar enter y pegar el siguiente texto:"build-css": "node-sass --include-path scss scss/main.scss css/style.css","watch-css": "nodemon -e scss -x \"npm run build-css\""

3. Crear las carpetas con sus respectivos archivosa. scss/main.scssb. css/style.css

4. En la consola correr estos 2 comandos: 
npm run build-css enter (Por unica vez) 
npm run watch-css enter

5. Cada vez que se quiera seguir compilando en SASSa. abrir la consola con ctrl+ñb. npm run watch-css

//FIN
-----------------

crear archivo index.html (asegurarse que sea fuera de las carpetas que creamos)

linkear el index.html al css como lo hacemos siempre

hacer el reseteo clasico

crear las diferentes carpetas para estilo DENTRO de la carpeta scss

por ejemplo: creamos una carpeta "secciones". y dentro de ella, creamos un archivo _index.scss (exclusivo para el estilo de la seccion index). usar siempre el guion bajo adelante del nombre

ahora debo VINCULAR cada hoja de estilo particular a la hoja MAIN de nuestro scss: 

como?

tipeando debajo del reseteo: 
@import './secciones/index';

ahora ya puedo pasar todo el codigo que ya venia manejando en css a cada seccion scss particular. directamente con control+c y control+v

(la comilla simple es con alt 39)

---------
.gitignore:

abrir con el + una segunda ventana de consola bash. renombrarla

me quedan dos ventanas opcionales de consola. git y scss

me voy a la git y hago git init enter

a la izq genero un archivo suelto .gitignore 

lo abro a la derecha y en la primer linea tipeo node_modules/
-----------------------

SCSS
cómo hacer que el estilo que elegí para una seccion no se me copie en el resto de las secciones (aún habiendo separado el estilo en distintos archivos scss (uno por sección, con guion bajo delante))?
Respuesta: se hace en el html correspondiente, colocando un id en cada body 

<body id="contacto">

que los diferencie unos de otros. y en cada archivo scss de estilo, empezar con 

#index{

TAMBIEN se puede usar una class="ejemplo" (en vez de un id). en el html se agrega la class al body; y en el scss en vez de #index{ se pone:

.ejemplo{ 

de esa forma, CADA estilo queda para cada sección, y si quiero REUTILIZAR puedo copiar lo que quiera. 

----
&:hover


lo que es asi en CSS:

li{
	color: blue
	}
li:hover{
	color: red;
	}


en SCSS es así:
li{
	color: blue;
		&:hover{
			color: red;
		}
	}

-----------
@import

importante: 
los @import van en el main
no llevan ahi el _
no hay que olvidar el ; al final
la sintaxis es: @import (espacio) '(comilla simple) + nombre' (comilla simple) 

mas info: https://latteandcode.medium.com/c%C3%B3mo-organizar-los-archivos-sass-de-tu-proyecto-c8b02242d95

----------------
Variables
Las variables se importan en el main scss ARRIBA DE TODO (debajo del reseteo). Antes, debo crear una carpeta que se llame variables (depende de la carpeta scss) y dentro creamos un archivo _colores.scss
Cuando vamos a la importación de esa carpeta, hacemos @import './' y nos trae "variables". debemos seguir para que nos traiga "colores".
Cuando queremos usar esta variable hacemos asi: dentro de colores.scss, codeamos
$textoPrincipal: blue;   

Y dentro de index.scss (x ej):

.segundaSeccion{
	font-family: sans-serif;
	color: $textoPrincipal
