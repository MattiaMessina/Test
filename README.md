# GIT
https://devdev.it/guida-git-versioning/come-funziona-git-controllo-versione/

<br>

#### Per uploadare successivamente un progetto che ho in locale prima creo dentro la sua cartella la cartella .git che contiene tutti i file per operare con git:
git init

<br>

#### Per uploadare:
1. git add --all
2. git commit -m "messaggio"
3. git push

<br>

#### Per mettere o togliere il proxy:
- git config --global --unset http.proxy
- git config --global http.proxy http://proxy.ariadne.it:3128

<br>

#### Per clonare una repository online sul locale:
- git clone https://percorso/cartella.git

<br>

#### Per tracciare uno o più file e quindi farne seguire a git le future modifiche (inserisco i file nell'area di stage):
- git add file.txt
- git add --all
#### Per non tracciare più un file (la sua ultima versione tracciata viene ancora committata):
- git rm file.txt
#### Per togliere dall'area di stage un file (non viene più committato):
- git rm --cached file.txt
#### Se vogliamo mantenere e non tracciare un file, inseriamo il suo nome nel file .gitignore

<br>

#### Per salvare lo stato attuale del progetto (tutto quello che è presente nell'area di stage) e creare una uova istantanea (snapshot):
- git commit -m "messaggio con la sintesi delle modifiche"
#### Commit per modificare l'ultimo effettuato senza aggiungerne un altro nei log:
- git commit --amend

<br>

#### Per vedere le ultime modifiche ai file (opzione --stage per vedere le differenze con file nello stage):
- git diff

<br>

#### Per passare a una versione passata o ad un branch del progetto (l'id si legge quando si fa il commit):
- git checkout id_versione
#### Per tornare alla versione principale:
- git checkout master

<br>

#### Per creare un nuovo ramo e poi spostarci dentro:
- git branch nome_ramo
- git checkout nome_ramo
#### Per caricare sulla cartella remota il nuovo ramo:
- git push -u nome_server nome_ramo
#### Se facciamo un commit in questa cartella di lavoro modifichiamo solo questo branch.
#### Per vedere la lista dei rami non uniti:
- git branch --no-merged

<br>

#### Lista dei rami:
- git branch
#### Cancellare un ramo
- git branch -d nome_ramo

<br>

#### Cronologia dei commit
- git log
#### Diverse opzioni per visualizzare solo il messaggio dei commit in una riga, vedere solo gli ultimi 3 commit o cercarli per data:
- git log --pretty=onneline -3 --since=1week

<br>

#### Per sapere lo stato della mia cartella di lavoro  locale:
- git status

<br>

#### Per unire un ramo al ramo master principale prima bisogna spostarsi sul ramo principale e poi mergiarlo (l'opzione indica di inserire questo merge in un commit in modo da non perderne la cronologia):
- git checkout master
- git merge --no-ff nome_ramo

<br>

#### Per vedere la lista dei tag o per visualizzare le info di un tag:
- git tag
- git show nome_tag
#### Per dare un tag lightweight (semplice) o annotated (cioè con le informazioni sull'autore, il nome del tag, la data e un messaggio):
- git tag nome_tag
- git tag -a nome_tag -m "messaggio"
#### Per dare un tag ad un vecchio commit:
- git tag -a nome_tag id_commit

<br>

#### Per ripristinare una versione precedente:
- git revert id_commit

<br>

#### Per visualizzare il nome e l'url del server remoto (l'url può essere http o ssh a seconda del sistema; sono divisi in fetch e push, i push permettono l’invio di modifiche, mentre fetch significa che possiamo scaricare dati da quel server):
- git remote -v
#### Per aggiungere una connessione ad un server remoto e per rimuoverla:
- git remote add nome_server url_server
- git remote rm nome_server

<br>

#### Per scaricare i commit remoti (visualizzare lo stato del progetto) senza intaccare la cartella locale:
- git fetch nome_server
- git fetch nome_server nome_ramo

<br>

#### Per fare il merge nel locale di una cartella remota (scaricare e mergiare):
- git pull nome_server
- git fetch + git merge

<br>

#### Per uploadare le modifiche fatte in locale sul server remoto:
- git push nome_server nome_ramo --tags

<br>

#### Per mettere da parte le modifiche prima di un commit e riprenderle:
- git stash
- git stash pop

<br>





# GIT-FLOW
https://devdev.it/guida-gitflow/come-funziona-gitflow-branch-develop-e-master/

<br>

#### Inizializzare l'ambiente git-flow:
- git flow init

<br>

#### Per creare una nuova funzionalità (feature) parto dal ramo develop e creo un nuovo ramo con lo sviluppo della funzione:
- git checkout develop
- git checkout -b feature/nome_funzione
Oppure con git-flow:
- git flow feature start nome_funzione
#### Dopo aver creato la funzione la mergiamo col ramo develop:
- git checkout develop
- git merge feature/nuova_funzione
Oppure con git-flow:
- git flow feature finish feature/nuova_funzione

<br>

#### Quando dopo diverse funzioni siamo pronti a rilasciare la nuova versione da develop a master, primacreo un ramo release di develop per gli ultimi fix:
- git checkout develop
- git checkout -b release/1.2
Oppure con git-flow:
- git flow release start 1.2
#### Dopo i bugfix siamo pronti a rilasciare larelease sul ramo di produzione master:
- git checkout develop
- git merge release/1.2
- git checkout master
- git merge release/1.2
- git tag 1.2
- git branch -D release/1.2
Oppure con git-flow:
- git flow release finish '1.2'

<br>

#### I rami di hotfix sono creati sul ramo master per gestire i bug che sono in produzione nel minor tempo possibile:
- git checkout master
- git checkout -b hotfix/nome_bug
Oppure con git-flow:
- git flow hotfix start nome_bug
#### Dopo il fix carichiamo la versione senza bug sul ramo principale:
- git checkout master
- git merge hotfix/nome_bug
- git tag 1.2.1
- git checkout develop
- git merge hotfix/nome_bug
- git branch -D hotfix/nome_bug
Oppure con git-flow:
- git flow hotfix finish nome_bug