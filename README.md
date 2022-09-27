<center><h1>Git</h1></center>

<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/e0/Git-logo.svg">
</div>

Sistema de controlamiento de versiones local en el equipo, integrado con plataformas como git hub

## Configurando Git por primera vez

- `git --version` **Saber version de git**
- `git help`
- `git config --global -e ` **Lista las variables globales del pc**
- `git config --global pull.ff only` **Configura el pull para fast forward**
- `git config pull.rebase true` **LOCAL,permite hacer pull.rebase(punto de conflicto)**
- `git config --global init.defaultBranch main` **cambio global, por defecto se creara rama principal con el nombre main**

**Identidad usada en los commits**
Personalizar tu entorno de git, solo se requiere hacerlo una vez aunque siempre puedes modificarlos.

- `git config --global user.name "nameUser"`
- `git config --global user.email "EmailUser"`

 <details>
 <summary><b>bandera</b></summary>
 
1. **Archivo `/etc/gitconfig`:** Contiene valores para todos los usuarios del sistema y todos sus repositorios. Si pasas la opción `git config --system`, lee y escribe especificamente en este archivo.
2. **Archivo `~/.gitconfig`:** Archivo especifico del usuario puedes hacer que git lea y escriba en este archivo  `git config --global`.
3. **Archivo `config`:** En el directorio de git es decir **.git/config** especifico del repositorio que estas usando actualmente.

> Cada nivel sobrescribe los valores del nivel anterior, por lo que los valores de **./gitconfig** tienen preferencia sobre los de **/etc/gitconfig**

 </details>

- `git config --list` **Mostrar propiedades de configuración**

<details>
<summary><b>Configurar alias</b></summary>

 <details>
 <summary><b>Alias en git</b></summary>

Estableces alias para personalizar o simplicar tus comandos de git.

1. `git config --global alias.nameAlias "comando que quieres simplificar"`

### EJ:

- `git config --global alias.s "status --short" `
  > Forma abreviada de git status <br> > **??:** Archivos no rastreados<br> > **A:** Archivos preparados<br> > **M:** Archivos modificados<br>
  > Contiene dos columnas Izquierda preparado y derecha sin preparar.
- `git config --global alias.co "checkout" `
- `git config --global alias.br "branch" `
- `git config --global alias.ci "commit" `
- `git config --global alias.last "log -1 HEAD"` **Ver ultimo commit**
- `git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"` **checkout-hace cuanto-commit-persona-posicion de rama**

- `git config --global alias.ll "log --pretty=format:'%C(bold green)%h%Cred%d %Creset%s%Cblue %cn' --decorate --numstat"` **Ver archivos subidos en los ultimos commit**

- `git config --global alias.like "!git ls-files | grep -i"` **Buscar ficheros con nombre como ----**

- `git config --global alias.alias "!git config -l | grep alias | cut -c 7-"` **Listar alias**
  > <b>! :</b> Este caracter hace referencia a que no es un subcomando de git, sino un comando externo que se ejecutara en la shell

### Editar alias:

- `git config --global -e` **Entrar modo de edición.**

  > Se abre el menu, se desplaza al alias interesado en editar, se da **a** para editar, cambias el codigo,se presion la tecla <b>ESC</b> despues tecla <b>:</b> se escribe wq!(w = escribir,q=salir,!=realizar cambios ahora).

     </details>

     <details>
     <summary><b>Alias en git bash(linux)</b></summary>
     
     #### Editar alias:

  - `vim ~/.bashrc`

  ```
   alias aliasE='vim ~/.bashrc'
   alias br='git branch'
   alias buscar='git grep'
   alias buscarlg='lg -S'
   alias ci='git commit -m'
   alias co='git checkout'
   alias contar='git grep -c'
   alias cursos='cd E/Cursos/Apuntes'
   alias last='git log -1 HEAD --oneline --decorate'
   alias lg='git log --graph --abbrev-commit --decorate --format=format:'\''%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'\'' --all'
   alias ll='git log --pretty=format:'\''%C(bold green)%h%Cred%d %Creset%s%Cblue %cn'\'' --decorate --numstat'
   alias ls='ls -F --color=auto --show-control-chars'
   alias node='winpty node.exe'
   alias s='git status --short'

  ```

  </details>

  </details>

---

<center><h2>Repositorio</h2></center>

- `git init` **crear repositorio LOCAL**
  ![.git](./imgBook/repoGit.png ".git")
- `git log` **explorar el historial de repositorio**
- `git status` **Informacion de commits, rama,seguimiento, modificación de archivos**
- `git add nombreArchivo.extension` **nombre del archivo al que git le hará seguiiento**
- `git add nameCarpeta/` **Le hará seguimiento a la carpeta y a todos los archivos internos**
- `git add .` **git le hara seguimiento a todos los archivos**
- `git reset nombreArchivo.extension` **nombre del archivo al que git dejara de hacer seguimiento**
- `git commit -m "comentario"` **Fotografia de codigo,es un registro histórico del proyecto**
- `git commit -am "comentario"` **Hace comado add y commit al tiempo (Solo si ya se le esta haciendo seguimiento al archivo)**

<center><h2>Ramas</h2></center>
  
  ## git branch
- `git branch` **Devuelve el nombre de la rama en la que se esta trabajando**
- `git branch -m master main` **Cambiar nombre de rama de master a main**
- `git branch nombreRama` **Crear una rama**
- `git branch nombreRama` **Crear una rama**
- `git branch -v` **rama cheksum comentarioCommit**
- `git branch --merged` **Devuelve nombre de las ramas que han sido fusionadas**
- `git branch --no-merged` **Devuelve nombre de las ramas que NO han sido fusionadas**
- `git branch -d nombreRama` **Eliminar rama, git verifica si falta unir cambios en la rama**
- `git branch -D nombreRama` **Eliminar rama forzado, se pierde trabajo en ella**
  
---
## git checkout

- `git checkout nombreRama` **Moverse a la rama deseada**
- `git checkout -b nombreRama` **Crear una rama y moverse automáticamente a la rama creada**
- `git checkout .` **Recostruye el Proyecto al ultimo commit**
- `git checkout hash` **Recostruye el Proyecto al commit especificado**
- `git checkout hash nombreArchivo.extension` **Recostruye solo el archivo a como estaba en el commit especificado**

## ![checkoutArchivo](img/gitCheckout.png)

## Actualizar commit y revertir commits

- `git commit --amend` **Abrir menu para enmendar(A=inserter ,: =opciones,wq!=guardar y hacer cambio inmediatamente )**
- `git commit --amend -m "Instalaciones update" `**Enmendar nombre de commit**
- `git reset --soft HEAD^n` **Devolverse al n commit anterior**
- `git reset sha` **Viaja al commit con el sha correspondiente**

  > **Banderas:**<br> > **--soft** devuelve sin destruir datos y los deja en el stage <br> > **--mixed** igual que soft pero saca los cambios del stage<br> > **--hard** Destructivo,dejare el repositorio como estaba en ese punto (elimina cambios), aunque se pueden ver con git reflog.

- `git reflog` **Historial de log, podemos devolvernos a estados después de hard**

<details>

<summary><b>Stashes</b></summary>

- `git stash` **Guardar archivos actualmente trabajados para no perder info ni hacer commit**
- `git stash save "descripcion del stash"` **Almacena el stach con la descripcion, mucho facil de trabajar**
- `git stash list` **Lista los stash actuales (recomendable trabajar con uno o con ramas)**
- `git stash branch nuevaRama` **Lleva los cambios del stash a la nuevaRama**
- `git stash list --stat` **Lista con parametro de los stash**
- `git stash apply "stash@{n}"` **Para elegir una stash especifico cuando hay varios lista**
- `git stash drop "stash@{n}"` **Para eliminar stash especifico cuando hay varios en lista**
- `git stash pop` **Devuelve el ultimo stash a los cambios en el archivo**
- `git stash clear` **Elimina todo los stash (se pueden recuperar con reflog)**
</details>
<details>
<summary><b>Tags</b></summary>
Referencia a un commit y a todo el estado del proyecto en ese punto enespecifico.
Etiquetas para puntos específicos del historial, se usa tipicamente para marcar versiones delanzamiento. Git usa <b>dos tipos</b> principales de etiquetas <b>ligeras</b> y <b>anotadas</b>.

### Creacion de etiquetas

- `git tag nombreTag `**Agregar tag, se recomienda [versionamiento semántico](https://semverorg/lang/es/)**

<h3><b>Las Etiquetas Ligeras</b></h3> son muy parecidas a una rama que no cambia,simplemente es un puntero a un commit en especifico.

- `git tag v1.4`

<h3><b>Las Etiquetas anotadas</b></h3> se guardan en la base de datos de Git como enteros.Tienen un <b>cheksum</b>, contiene le nombre del etiquetador,email, fecha y mensajeasociado; pudiendo ser firmadas y verificadas.

- `git tag -a v1.0.0 -m “Versión 1.0.0 lista”` **Crear tag con mensaje**
- `git tag -a v1.0.0 checksumCommit -m “Versión 1.0.0 lista” `**Crear tag con mensaje acommit especificado**
- `git show nameTag` **muestra mas info del tag especificado**
- `git tag` **Muestra tags de la app**

- `git tag -d nombreTag` **Eliminar tag**
</details>

<center><h1>Reorganización</h1></center>
  
<details>
<summary><b>Merge</b></summary>
  
- `git merge nombreRama` **Se unirá nombreRama a la rama donde se encuentra actualmente**
    > La rama donde se encuentra posicionado sera quien reciba los cambios de la rama descrita despues del merge
  
<center><h2>Merge con conflicto</h2></center>
Cuando el proceso de fusion no suele ser fluido,porque se tiene modificaciones dispares el mismo archivo Git no podra unirlo directamente y tendriamos que hacer un merge manual.no crea automaticamente la fusion sino que espera a que tú resuelvas el conflicto para los archivos que permaneceran sin fusionar.
Todo aquello que sea conflictivo y no se haya podido fusionar se marcara como <b>Unmerged</b>
  
  > Rama HEAD la que espera el cambio
  
- ## En visual studio code

![mergeConflicto](img/mergeConflicto.png "merge conflicto")

- ## En cosola

![mergeConflicto](img/mergeConflictoBash.png "merge conflicto")

> El archivo se ve literalmente como en la imagen en el momento del conflicto del merge

- Se resuelve el conflicto, eligiendo manualmente cual estado de archivos conservar o optar por editarlo agregando parte de ambos archivos.
- Se agregan los archivos al stage. `git add .` .
- Se hace un commit. `git commit -m "comentario"` .
- Conflicto solucionado !!

![mergeConflicto](img/mergeExitoso.png "merge exitoso")

</details>
  
<details>
<summary><b>Rebase</b></summary>
  
- Ordenar commits
- Corregir mensajes de los commits
- Unir commits
- Separar commits
  > Tratar de usar solo con cambios locales para no generar conflicto en repositorios remotos, ya que esto cambia la historia de los commits.
  
- `git rebase master `
- `git rebase -i HEAD~ncommits` **menu de rebase interactivo para los ncomits**

![rebase](img/rebase.png "rebase")

![rebaseEjemplo](img/rebaseEj.png "rebaseEjemplo")

> - Crea un área temporal donde se guardan los commits de la rama a mover.
> - Mueve el puntero de la rama alterna a la rama master.
> - Regresa los commits del áre temporal y los posiciona en el puntero actual.

<center><h2>Squash</h2></center>
Unir commits

Ej:

### Estado antes del squash

![antesSquashRebase](img/antesSquashRebase.png "antesSquashRebase")

1. Se usa el comando `git rebase -i HEAD~5`
2. Modo de edicion: se cambian los commits deseados por s excepto el 4

   ![squashRebase](img/squashRebase.png "squashRebase")

3. Se abre esta ventana donde se puede editar comentario del commit

   ![squashRebase2](img/squashRebase2.png "squashRebase2")

4. Después de squash commit

   ![despuessquashRebase](img/despuessquashRebase.png "despuessquashRebase")

</details>



<details>
<summary><b>Archivos</b></summary>

- **.gitkeep:** Git por defecto ignora carpetas vacías, con este archivo dentro de la carpeta podemos decirle que tenga observación sobre ellas.
  `.gitkeep`
- **.gitignore:** Esta en la raíz del proyecto, sin embargo se puede optar por definir varios archivos `.git ignore` en distintos directorios del repositorio, aquí se ponen los nombres de los archivos,carpetas que se quiere ignorar

Reglas sobre los patrones:

- Ignorar las líneas en blanco y aquellas que comiencen con **#**
- Emplear patrones glob estándar que se aplicara recursivamente a todo el directorio del repositorio local.
- **\*** : Corresponde a 0 o mas caracteres, todos. Tambien se puede usar para indicar directorios anidados.
- **[abc]** : Cualquier caracter dentro de los corchetes (en este caso a,b,o c).
- **[0-9]** : Cualquier caracter entre ellos, en este caso todos los numeros del 0 al 9.
- **?** : Corresponde a un carracter cualquiera
- Los patrones pueden empezar con **/** para evitar recursividad.
- Los patrones pueden terminar con **/** para epecificar directorio.
- Los patrones pueden negarse si se añade al principio el signo de exclamación **!** .

![gitIgnore](img/gitIgnore.png "Gi")

</details>

<center><h1>Git Hub</h1></center>

<div align="center">
  <img src="https://revistabyte.es/wp-content/uploads/2018/06/github-octocat.jpg">
</div>

### **Respositorios remotos:**

Son versiones de tu proyecto que estan hospedadas en internet o en cualquier otra red. Puedes tener varios de ellos, y en cada uno de ellos tendras permiso de solo lectura o de lectura y escritura.Gestionar repositorios remotos incluye saber cómo añadir un repositorio remoto, eliminar los remotos que ya no son válidos, gestionar ramas remotas, definir si deben rastrearse o no.

<center><h1>ramas remotas</h1></center>
Las ramas remotas son referencias al estado de las ramas en tus repositorios remotos. Son ramas locales que no puedes mover; se mueven automáticamente cuando estableces conmunicacion en la red. Funcionan como marcadores, para recordar en que estado se encontraba tu repositorio remoto la ultima vez que te conectaste con el.

**Clonar repositorio**

- `git clone https://github.com/user/repo` **Clona el repositorio de la direccion estrablecida, tambien con esta direccion git marcara el origin**

---

- `git remote add origin https://github.com/user/repo` **Set a new remot, agregar repositorio**
- `git remote -v` **Nos muestra fetch:donde obtenemos info, push: donde subimos la info**

  > Se puede tener multiples remotos, trabajando con distintos colaboradores

- `git remote add nombreRemoto url/remoto/aqui` **Añadir remotos**

  ![addRemote](img/addRemote.png)

  > A partir de ahora se podria usar el nombre sockets en vez de la url entera para traer o actualizar info para ese repositorio en especifico.<br>
  > Ej: git fetch sockets

- `git remote prune origin` **Si tienes ramas en local que en el remoto (repositorio en github) ya no existen actualizara estas referencias**
- `git fetch` **Comprobar si hay actualizaciones en la original despues del ultimo pull en la segundaria**

  > Git fetch localiza el servidor de la rama origen y actualiza tu base de datos local moviendo el puntero de la rama local para que apunte a la posicion mas reciente del remoto, lo que hace es obtener los metadatos del repositorio remoto u original y comprueba con tu repositorio local (sin descargar nada) y te muestra si en el repositorio original existen cambios, por decir algo seria comprobar cambios de una forma meramente informativa.<br>En cambio Git pull sincroniza el repositorio original con tu repositorio local transfiriendo los meta datos y los archivos si es que existiese algún cambio.<br>En resumen: git fetch comprueba los meta datos si hay cambios se movera un puntero no editable a la ultima version del remoto, git pull sincroniza el repo original y el local teniendo una copia local editable de la misma.

- `git pull` **Actualizar repositorio desde el origin main**
- `git pull repRemoto` **Actualizar repositorio desde el remoto especificado**
  > Es como un git fetch + git merge, sincronizando asi nuestro repositorio local con el remoto, teniendo una copia editable.

## **PUSH**

Permite compartir los cambios a un remoto donde tengamos permiso de escritura.

- `git push` **Subir cambios**
- `git push nombreRemoto nombreRamaRemoto` **Subir cambios especificando el repositorio y la rama del repositorio**
- `git push origin -d nombreRama` **elimina apuntador nombreRama del repositorio remoto**
  > Git suele mantener los datos por un tiempo es decir que se puede recuperar facilmente, hasta que el recolector de basura se ejecute.
- `git push --tag` **Sube los tags a github**

---

<center><h2>Markdown</h2></center>

<div align='center'>
<img src='https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/1920px-Markdown-mark.svg.png'>
</div>

[Guia Markdown](https://tutorialmarkdown.com/guia)
