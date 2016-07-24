
GIT

1)Como instalar GIT:

	Descargar desde https://git-scm.com

	msysgit para Windows. Trae Bash y Git. http://code.google.com/p/msysgit

	GitHub para Windows (requiere .NET, pero es m�s sencillo de instalar). http://windows.github.com

	TortoiseGit 

2) Configuraci�n Inicial:
	Debemos configurar nuestro nombre y nuestro email.
	Desde la consola que nos proporciona git:
	
		git config --global user.name "Pablo"
		git config --global user.email "<pablol9119@gmail.com>"
		
3) Crear un nuevo repositorio:

4) Definir el Directorio de Trabajo

5) Staging Index: es un area temporal, en donde indicaremos alli los archivos que llevaremos a trav�s del commit.
	Los pasos a realizar son:
		1- Modificar archivos dentro del directorio de trabajo.
		2- Seleccionar aquellos archivos cuyos cambios queremos enviar y agregarlos al staging index.
		3- Confirmar ("commit") esos cambios para que se almacenen en el repositorio.
		
	Para a�adir un archivo a la paging index, utilizamos el comando:
	
		git add <nombre del archivo que se quiere a�adir> 
		git add . (en este caso, con el punto a�adimos todos los archivos)
		
	Podemos examinar el estado de los cambios con el comando:
		git status
	
6) Enviando cambios: una vez que se hallan a�adido los archivos a la staging index, es hora de realizar un commit. Este confirma los cambios que se han realizado y los registra en el repositorio.
	git commit
	
	Luego se abrir� el editor de texto donde se podr� ingresar un mensaje para nuestro commit. 
	Estos mensajes dan informaci�n de lo que hace un commit en el proyecto. Debe describir de la mejor manera posible que hace el commit.
		1- �Porqu� has hecho este cambio? 
			(ej: corregir un bug, implementar un caso de uso o una historia de usuario, etc.)
		2- �Qu� cambios has hecho? 
			Y describirlos un poco, mostrando los principales cambios hechos al sistema. (No describir todo, hay formas de ver exactamente cada cambio si se quisiese hacer)
		3- �Qu� consecuencias esperas que tenga tu cambio?
		
	Convenciones importantes para el mensaje:
		Primera l�nea del mensaje: es el resumen del commit. No debe tener m�s de 50 caracteres. Es com�n escribirlo en imperativo (ej: "a�ade X", "corrige Y").
		Segunda l�nea del mensaje: en blanco.
		A partir de la tercera l�nea: cuerpo del mensaje. Pon saltos de l�nea a mano y no dejes que cada l�nea tenga m�s de 72 caracteres.
		
	Cuando se termino de escribir el mensaje, GIT efectivizar� los cambios.
	
7) Eliminando archivos:
	Se realiza con el comando:
		git rm <nombre del archivo>
		
8) Moviendo archivos:
	Al mover un archivo a otra carpeta dentro del proyecto, el status de git determinar� que se ha eliminado el archivo de una carpeta, y se ha agregado el archivo en otra carpeta. Por lo tanto, debemos realizar un "git rm archivo" y luego un "git add archivo" en el nuevo directorio.
	
9) Deshaciendo cambios: 
	Tener en cuenta que eliminar un archivo del staging index no es lo mismo que deshacer un commit.
	
	Suponiendo que se haya a�adido al staging index un archivo que en realidad no se quer�a agregar, entonces para descartarlo debemos hacer:
		git reset HEAD <nombre del archivo>
	De esta manera el archivo ya no estar� marcardo para realizarle el commit.
	
	Ahora si queremos revertir todos los cambios que se realizaron en el archivo despues del �ltimo commit, hacemos:
		git checkout -- <nombre del archivo>
		
10) Examinando el registro:
	Con el comando "git log" se examinan los distintos commit que han realizado.
	Para ver el resumen de cada commit, ejecutamos el comando: "git log --oneline"
	Con el comando "git log --oneline --decorate" 
	
11) Creando Ramas:
	Con el comando "git branch <nombre de la nueva rama>", se crea una nueva rama.
	Para posicionarnos en ella, debemos hacer: "git chechout <nombre de la nueva rama>"
	Con el comando "git branch" veremos las ramas existentes, y la que est� marcada con el "*" ser� en la que estamos posicionados. Siempre existe una rama "master".
	Si queremos crear una nueva rama y en el mismo comando posicionarnos en ella, hacemos: "git checkout -b <nombre de la rama nueva>".
	Para borrar una rama, hacemos: "git branch -d <nombre de la rama>".
	
12) Fusionando Ramas:	
	La forma m�s sencilla, es hacer un checkout a la rama de destino donde se va a fusionar todo, ejecutar el comando "git merge <rama de origen>".
	Una vez que hemos terminado de trabajar con una rama, de forma opcional, podemos eliminarla.
	
	1- Si se hace un merge de una rama en otra sin haber tocado los mismos archivos, entonces los cambios se integran bien.
	2- Si se toca el mismo archivo en ambas ramas pero editando partes separadas, entonces GIT detecta que no se ha tocado la misma regi�n y se suelen integrar bien.
	3- Si se ha editado el mismo archivo en ambas ramas y se ha modificado la misma regi�n del c�digo, entonces GIT genera un conflicto porque no sabe con qu� modificaci�n quedarse. Entonces, se deber� corregir de manera manual el conflicto editando el archivo, y eliminando lo que no corresponda. Luego se vuelve a agregar el archivo, y git autom�ticamente har� los cambios.
	
13) Examinando commits previos:
	
14) Creando Tags:
	Sirven para crear alias a commits concretos. De esta manera, en lugar de ir a commit a trav�s de su c�digo, podemos indicarle un tag con una palabra espec�fica que nos permita acceder a �l de una manera mas legible.
	
15) Push a repositorios remotos:
	Un proyecto puede tener otros repositorios remotos con los que asociarse. Si se trabaja con otras personas en el mismo proyecto, podriamos enviarselo de forma remota. Si los cambios son de muchas personas, lo normal es definir un repositorio central. 
	Si hemos hecho un clone de nuestro repositorio, autom�ticamente ese repositorio se establece como remoto.
	Ejemplo: git remote add origin -/Dropbox/repositorio.git
	Luego podemos enviar a ese remoto, a trav�s del comando: git push origin <rama que se quiere enviar>
	
16) Actualizando repositorios con el comando pull:
	
	