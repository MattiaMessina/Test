# Test

### Per uplodare:
1. git add --all
2. git commit -m "messaggio"
3. git push

<br><br>

### Per mettere o togliere il proxy:
- git config --global --unset http.proxy
- git config --global http.proxy http://proxy.ariadne.it:3128

<br><br>

### Per aggiungere i cambiamenti effettuati alla cartella:
- git add file.txt
- git add --all

<br><br>

### Commit con parametro messaggio:
- git commit -m "inserisco il mio messaggio"
### Commit per modificare l'ultimo effettuato senza aggiungerne un altro nei log:
- git commit --amend

<br><br>

### Per sapere lo stato del sistema e il log dei commit:
- git status
- git log

<br><br>

### Per mettere da parte le modifiche prima di un commit e riprenderle:
- git stash
- git stash pop

<br><br>

### Per uplodare le modifiche fatte in locale:
- git push <remote> <branch>

<br><br>

### Per scaricare la cartella remota
- git pull
- git fetch + git merge