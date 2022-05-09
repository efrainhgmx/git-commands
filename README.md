# Git comandos básicos a avanzados.

Git es el sistema de control de versiones creado por Linus Torvals, este software permite a los desarrolladores trabajar en un solo proyecto sin afectar el flujo de trabajo. Trabaja mediante ramas y **GIT nunca olvida** nada lo cual nos permite regresar a ver versiones anteriores en caso de que algo falle.

Puedes parcticar los comandos aqui: http://onlywei.github.io/explain-git-with-d3/#fetch


### CONFIGURAR GIT
----------------
`$ git config` // Nos permite ver los comandos que podemos usar para configurar.

`$ git config --list `  //Ver la configuración actual de git.

`$ git config --global  user.email "tu@email.com"` //Configurar tu email

`$ git config --global user.name "Tu Nombre"` //Configura tu nombre de usuario

### Comandos básicos de git
`$ git init`  //Inicia Git dentro de la carpeta raíz de nuestro proyecto

`$ git code` // Abre Vscode en Windows

`$ git status` //Muestra el estado acual de la base de datos 

`$ git add _myfile.txt _` //Agrega el archivo en Staging

`$ git add .  `// Añade todos los archivos de la carpeta actual

`$ git add -A ` //  Añade todos los archivos al igual que **git add .**

`$ git rm -- cached _myfile.txt_`  // Elimina el archivo de la RAM sin eliminarlo de la carpeta

`$ git commit -m "Primer commit de este archivo"` //Sube el archivo al repositorio con un mensaje.

`$ git log _my file.txt_`  //Puede ver todas las modificaciones del archivo asi como ver quien las hizo

`$ git show "file.txt"` //Muestra las modificaciones del archivo desde el ultimo commit o la version más reciente del archivo

### Editor VIM
Podemos abrir un editor en la terminal usando.
`$ vim miArchivo.html`

- ESC, i //Para escribir en VIM.

- ESC, shift + zz // Salir
- :wq // Guardar y salir.
- :q //Salir sin guardar.
- :q! //Salir sin guardar cambios de forma hard.

#### PARA COMPARAR VERSIONES:

`$ git diff` Numeros de comit a comparar otro commit a comparar

### REGRESAR EN EL TIEMPO
** EN CASO DE GIT RESET...** Este comando nos ayuda a volver en el tiempo. Pero no como git checkout que nos deja ir, mirar, pasear y volver. 
Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás.
Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones:
Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre).
O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.

`$ git reset Numeros de comit al cual regresar --soft` // --hard este segundo borra todas las versiones despues de la version hecha.

`$ git log -- stat`  // Muestra los cambioes especificos hechos SALIMOS CON "Q"

`$ git checkout master myfile.txt` // Volvemos a la ultimaversion que se ha hecho commit

`$ git branch rama` //crea una rama haciendo una copia del ultimo commit en master

`$ git checkout nombre-de-la-rama` // sirve para movernos entre ramas.

`$ git commit -am "mensaje"` // hace commit de un archivo sin necesidad de hacer git add SOLO FUNCIONA CON ARCHIVOS QUE NOS SON NUEVOS


`$ git clone url_del_servidor_remoto:` // Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git.

`$ git push origin main:` Luego de hacer git add y git commit debemos ejecutar este comando para mandar los cambios al servidor remoto.

`$ git fetch origin main` Lo usamos para traer actualizaciones del servidor remoto y guardarlas en nuestro repositorio local (en caso de que hayan, por supuesto).

`$ git merge ` También usamos el comando git fetch con servidores remotos. Lo necesitamos para combinar los últimos cambios del servidor remoto y nuestro directorio de trabajo.
--> git checkout rama a donde se hace quiere hacer el merge. Ejemplo la rama principal.
    git merge rama donde estan  los cambios. Ejemplo la rama de desarrollo.
	
	`$git chekout main`
	`$git merge prueba`
	

`$ git pull` Básicamente, git fetch y git merge al mismo tiempo.

`$ git branch` Muestra cuantas ramas hay y en cual estas actualmente

`$ git branch -r` Muestra las ramas remotas del servidor de GitHub

`$ git show-branch --all`  Muestra la historia de esas ramas

`$ git branch -a` Muestra todas las ramas tanto locales como remotas y cuales no se le han hecho push

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AGREGAMOS CODIGO AL REPOSITORIO DE GITHUB
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`$ git remote add URL: `Guarda la URL del repositorio de GitHub con elnombre origin.

`$ git remote`

`$ git remote -v :` Verifica que la URL se haya guardado correctamente

`$ git pull origin master --allow-unrelated-histories : `Trae la version del repositorio remoto y hacer merge para crear
un commit con los archivos  de ambas partes. Podemos usar un git fetch y git merge o solo el git pull con el flag 


`$ git push origin master :` Push para guardar los cambios de nuestro repositorio local en GitHub.

--------------------------------------------------------------------------------------------------------------------------------
CREAR TU SSH PRIVADA
--------------------------------------------------------------------------------------------------------------------------------
SIEMPRE DESDE EL HOME ~ O CON cd

`$ ssh-keygen -t rsa -b 4096 -C "tu@email.com"`

//Terminar de configurar nuestro sistema, se escribe tal cual con comillas.

`$ eval "(ssh-agent -s)"`

**Nota: Revisa la sintaxis del comando anterior en caso de que te de un error al teclearlo**

//Añadir tu llave SSH a este servidor
`$ ssh-add ruta-donde-guardaste-tu-llave-privada`

**Ejemplo:** `$ ssh-add ~/.ssh/id_rsa`

Aquí debes configurar tu llave privada no la publica .pub

SSH DE GITHUB
`$git remote set-url origin url-ssh-del-repositorio`

----------------
CREAR TAGS
----------------
ver los cambios hechos en git:
`$ git log`

`$ git log --all`

`$ git log --all --graph --decorate --oneline`

##### ALIAS
`$ alias arbolito="git log --all --graph --decorate --oneline"`

Tag:
`$ git tag -a v0.1 -m "mensaje"  id-del-commit`

`$ git tag ` muestra los tags que existen

`$ git show-ref --tags ` muestra el tag y su referencia 

#### Publicar los tags en el repositorio remoto:
`$ git push origin --tags`

#### Borrar un tag del repositorio remoto:
`$ git tag -d nombre-del-tag`

`$ git push origin :ref/tags/nombre-del-tag`

`$ gitk `: Abre un entorno visual de la historia de las ramas

`$ git stash` : Guarda los cambios de manera temporal si esque no queremos hacer commit a esos cambios

`$ git stash list`: Muestra los cambios guardados en stash

`$ git stash pop` : aplica los cambios guardados.

`$ git stash branch nombre-de-la-rama `: manda esos cambios a esa nueva rama

`$ git stash drop` : borra el cambio guardado en stash

`$ git clean --dry-run` : "Simula" los archivos que va a borrar o nos muestra los archivos que va a borrar.

`$ git clean -f` : Borra todos los archivos  listados QUE NO SEAN CARPETAS

`$ git cherry-pick #No de commit` :  Trae commits especificos de otra rama 

`$ git log --oneline` : Muestra el arbolito de cambios en una sola linea

`$ git commit --amend` Agrega los cambios que no habiamos hecho al ultimo commit de esa rama

------------------------------------------------------------
RECUPERAR ARCHIVOS
------------------------------------------------------------
`$ git reflog` Muestra TODO

`$ git reset --HARD #hash `: Resetea todo al punto anterior en caso de que se rompa todo

`$ git reset --soft` Resetea todo pero mantiene los cambios en staging que no hayan tenido un commit

------------------------------------------------------------
DESHACER O ABORTAR UN MERGE
------------------------------------------------------------

`$ git merge --abort` deshace el ultimo merge realizado y te posiciona en el ultimo commit.
`$ git checkout -- .` Te lleva al ultimo commit hecho de la rama.

**NOTA: git merge --abort, no deshace el cambio hecho por un git pull o git fetch**


BUSCAR PALABRAS DENTRO DE LOS ARCHIVOS
----------------------------------------------------------------
`$ git grep la-palabra:` Muestra en que documentos se encuentra esa palabra

`$ git grep -n la-palabra:` Muestra en que linea y en que archivos se encuentra

`$ git grep -c la-palabra:` Muestra cuantas veces se ha usado.

`$ git log -S "la palabra":` Muestra la palabra dentro de la historia de los commits



VER RECURSOS COLABORATIVOS
----------------------------------------------------------------------------------
`$ git shortlog` : Muestra cuantos commits han hecho los miembros del equipo

`$ git shortog -sn:`  Muestra el numero de commits y quien ha hecho más commits

`$ git shortlog -sn --all --no-merges:` Muestra commits pero sin los merges

`$ git blame archivo.txt:` Muestra quien hizo que, linea por linea

`$ git blame -c archivo.txt`: Muestra de mejor manera el comando anterior

`$ git blame archivo.txt -L35,50`: Muestra solo los cambios desde la linea 35 hasta la 50 y muestra quien hizo que.

`$ git blame archivo.txt -L35,50 -c`: Muestra mejor lo anterior

##### CREA TU COMANDO:
`$ git config --global alias.nuevocomando "El comando a reemplazar"`

ejem: **$ git config --global alias.stats "shortlog -sn --all --no-merge"**

`$ git stats`  (Muestra el comando anterior)

----------------------------------------------------------------
EDITOR DE README
----------------------------------------------------------------
https://pandao.github.io/editor.md/en.html
