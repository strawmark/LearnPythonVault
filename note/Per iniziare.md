---
tags:
  - Teoria
---
## Hello World

Il primo "programma" in Python, utile per verificare la corretta [[Setup dell'ambiente di sviluppo|installazione dell'ambiente]], dato che è impossibile sbagliarne la compilazione.

Per scriverlo, crea un nuovo file `hello.py` e scrivi il seguente codice:

```Python python icon title:hello.py
print('Hello World!') ## Hello World!
```

- `print()` è una [[Funzioni|funzione]] che stampa su schermo una stringa o il valore di una [[Variabili|variabile]]
- Usare due cancelletti `##` ti permette di scrivere un **commento di riga**.
## Guida allo stile
Il codice scritto in Python segue comunemente uno stile di scrittura per i nomi di funzioni, variabili e classi. A seconda di cosa si sta per scrivere, si utilizzerà lo snake case o il pascal case:
### Snake case
Tutte le lettere sono minuscole, e se si ha necessità di usare più parole, queste vanno separate da simboli di *underscore* (`_`). Un esempio di uso di snake case per il nome di una variabile è:

`{python icon title:}user_name='Marco'`

Lo snake case è utilizzato per nomi di [[Variabili|variabili]] e [[Funzioni|funzioni]], ma anche per nomi di file e di database collegati al programma.
### Pascal case
Ogni parola inizia con lettera maiuscola e non si usano simboli per collegare parole fra loro. Un esempio di pascal case è:

`{python icon title:}class UserData:`

Il pascal case è utilizzato per i nomi delle [[Classi e Oggetti|classi]].

