---
tags:
  - GIT
---
# Tabella rapida comandi

| Comando                              | Descrizione                         |
| ------------------------------------ | ----------------------------------- |
| init                                 | Avvia repository                    |
| config --global --edit               | Edita configurazione                |
| config --global user.name            | Mostra username                     |
| config --global user.name "username" | Cambia username                     |
| config --global user.email           | Mostra mail                         |
| config --global user.email "email"   | Cambia mail                         |
| commit -m "messaggio"                | Esegui commit                       |
| status                               | Mostra status dei commit            |
| add .                                | Aggiunge tutti i file al commit     |
| branch                               | Mostra nomi branch e branch attuale |
| branch -m nome                       | Cambia nome branch                  |
| checkout -b nuova_branch             | Nuova branch da quella attuale      |
| checkout branch                      | Cambia branch                       |
| checkout -- .                        | Resetta la branch all'ultimo commit |
| checkout -- nomefile                 | Resetta il file all'ultimo commit   |
## Init
Per avviare un versione control e controllare il suo status attuale:

```bash title:"Inizializzare una repository"
git init
git status
```

## Commit
Per aggiungere tutti i file al commit e avviare:

```bash
git add .
git commit -m "messaggio"
```
## Merge

Per il merge bisogna passare al branch al quale vogliamo aggiungere i contenuti di un altro branch:

```bash
git checkout master
git merge feature
```
## Reset

```bash
git reset --hard HEAD~1
```
## Delete

Bisogna cambiare branch rispetto a quella che bisogna cancellare

```bash
git checkout master
git branch -D feature
```

## Github e simili

```bash
git remote add origin URL
git push -u origin nomebranch
```

- `remote add` aggiunge una connessione remota alla repository online
- `origin` sarà il nostro URL, in modo da usarlo nel comando `push` senza riscriverlo tutto.

>[!abstract] Nota
>In case you want to delete this token from your machine (e.g. to add a new one), please run the following command in the integrated command prompt in VS Code:
>
>1. `git credential reject` ➡ **ENTER**
>2. `host=github.com` ➡ **ENTER**
>3. `protocol=https` ➡ **ENTER**

### Clone

```bash
git clone URL
cd cartella_repository
```

### Push

Per aggiungere il commit alla repository esterna:

```bash
git push origin main
```

Sarà necessario aggiungere le credenziali per confermare.

Per **Gitea**:

```bash
git remote set-url origin http://strawmark:<token>@stream.iliadboxos.it/gitea/<user>/<repo>.git`
```
### Pull

Per portare cambiamenti della repository remota all'interno della repository locale:

```bash
git pull
```

# Altro

#### Errore: refusing to merge unrelated histories

Si verifica quando i due repository (locale e remoto) hanno storie diverse e non correlabili. Per risolverlo, posso aggiungere a `git pull` il flag `--allow-unrelated-histories`:

```bash
git pull origin master --allow-unrelated-histories
git add <file_conflittato>
git commit -m "Risolti conflitti da storie non correlate"
git push origin master
```

#### Rimozione file non più tracciati

Per rimuovere dal repository remoto i file che ora sono ignorati dal tuo `.gitignore`, posso seguire questi passaggi:

```bash
git rm --cached <file_o_cartella>
git commit -m "Rimosso file ignorati dal remote"
git push origin nomebranch
```

Questi file verranno rimossi dal repository remoto, ma rimarranno localmente sul computer. Il file `.gitignore` garantirà che Git non li tracci più.

#### Cherry-pick

Se ho due branch: quella principale (`main`) e una dove ho fatto un commit da riportare sulla principale (`new-feature`). Il commit di `new-feature` avrà un hash, ad esempio `abc123`.

```bash
git checkout main
git cherry-pick abc123
```

- `checkout main` sposta git verso `main`
- `cherry-pick abc123` Applica il commit `abc123`, generato su `new-feature`, alla branch `main`
- Git crea una nuova commit su `main` con gli stessi cambiamenti

Se ci sono conflitti Git crea un avviso e bisognerà risolverli manualmente. Dopo averli risolti:

```bash
git add .
git cherry-pick --continue
```
