---
tags:
  - Teoria
---
# Definizione

Una stringa è un solitamente un [[Array|array]] di caratteri, ma in Python il concetto di stringa è realizzato a partire dalle [[Liste|liste]], con le dovute differenze.

Per delimitare una stringa posso usare gli apici `'`, i doppi apici `"`, o tripli doppi apici `"""` :

~~~python title:"Esempio della stessa stringa con delimitatori differenti"
print("Hello")  
print('Hello')
print ("""Hello""")
~~~

Il discrimine tra un sistema e l'altro è la presenza o meno di apici/doppi apici che potrebbero essere considerati come fine stringa:

~~~run-python
# errore  su ''
print('I'm here')  
~~~

~~~run-python
# errore  su ""
print("I'm reading "Moby Dick"")
~~~

Anche se scomodo, come ultima spiaggia l'uso dei tripli doppi apici risolverà entrambi i problemi sopra citati.
# Caratteristiche notevoli

Le stringhe sono [[Classi e Oggetti|oggetti]] **immutabili**, ovvero non possono essere modificate in memoria dopo averle create, **omogenei**, ovvero contengono solo un tipo di dato (caratteri alfanumerici) e sono **compatte**, ovvero la memoria viene utilizzata in modo più efficiente attraverso lo *string interning*.

```python title:"Immutabilità di una stringa" hl:2
s = "ciao"
s[0] = 'C' # Errore, non posso modificare una stringa
print(s)
```
```python hl:2
s = "ciao"
s = 'C'+s[1:] # OK, ma in realtà è stata una nuova stringa
print(s)
```

Allo stesso modo degli oggetti, la comparazione errata fra stringhe può generare degli errori concettuali nel codice.

Ad esempio, dichiarando la stessa stringa due volte, Python sta in effetti allocando memoria una sola volta, quindi `s1` ed `s2` sono puntatori alla stessa variabile:

```python title:"String interning" hl:7-8
s1 = "ciao"
s2 = "ciao"

print("s1: " + s1)
print("s2: " + s2)

print(s1 is s2) # True
print(s1 == s2) # True
```

Mentre se queste stringhe fossero state create in modo dinamico, quindi se fossero state allocate in fasi diverse nonostante il loro contenuto sia lo stesso, allora l'eguaglianza fallisce:

>[!Warning] Nota
> In alcune implementazioni di Python come CPython, questo comportamento occorre in casi più limitati

```python title:"Controesempio di string interning" hl:7-8
s1 = input() # Scrivi "ciao"
s2 = str("ciao")

print("s1: " + s1)
print("s2: " + s2)

print(s3 is s4) # False
print(s3 == s4) # True
```

In questi casi, come con l'eguaglianza tra [[Classi e Oggetti|oggetti]], occorre usare il confronto del *contenuto* con l'operatore `==` e non usare `is`, che indica solo se due variabili stanno puntando allo stesso oggetto.
# Manipolazione delle stringhe

Tutte le  [[Liste#Slicing|interazioni tipiche delle liste]] sono possibili con le stringhe, ma con quest'ultime posso eseguire qualche operazione in più grazie all'uso di operatori, [[Funzioni|funzioni]] e metodi specifici: 
## Concatenazione

L'[[Operatori|operatore]] `+` nel campo delle stringhe ne esegue la concatenazione:

~~~Python title:"Concatenazione di stringhe"
age = int(input())
ageString = 'I am ' + str(age) + ' years old.'
print(ageString)
~~~
## Funzioni e metodi

Le funzioni e i metodi utilizzabili sulle stringhe sono molteplici, ecco una tabella di quelli più utili e un [link](https://www.digitalocean.com/community/tutorials/python-string-functions) ad una lista più completa:

| Funzione        | Descrizione                                 | Esempio                              |
| --------------- | ------------------------------------------- | ------------------------------------ |
| `len()`         | Lunghezza della stringa                     | `len("Marco") → 5`                   |
| `.lower()`      | Tutto minuscolo                             | `"CIAO".lower() → "ciao"`            |
| `.upper()`      | Tutto maiuscolo                             | `"ciao".upper() → "CIAO"`            |
| `.strip()`      | Rimuove spazi iniziali/finali               | `" ciao ".strip() → "ciao"`          |
| `.replace()`    | Sostituisce parti di stringa                | `"ciao".replace("a", "e") → "cieo"`  |
| `.split()`      | Divide la stringa in lista                  | `"a,b,c".split(",") → ['a','b','c']` |
| `.join()`       | Unisce elementi di una lista in una stringa | `",".join(['a','b','c']) → "a,b,c"`  |
| `.find()`       | Trova la posizione di una sottostringa      | `"ciao".find("a") → 2`               |
| `.startswith()` | Controlla se inizia con una certa stringa   | `"ciao".startswith("c") → True`      |
| `.endswith()`   | Controlla se finisce con una certa stringa  | `"ciao".endswith("o") → True`        |
### Funzione `len()`
Una funzione (non un [[Classi e Oggetti#Metodi|metodo]]!) che ritorna un valore intero con la lunghezza della stringa:

```python title:"Funzione len()"
myName = 'Marco'
length = len(myName)
print(length)
```

### Metodi `upper()` e `lower()` e `title()`

```python title:"Metodo .lower()"
name = "Ada Lovelace"
print(name.lower()) ## ada lovelace
```

```python title:"Metodo .upper()" fold:fold
name = "Ada Lovelace"
print(name.upper()) ## ADA LOVELACE
```

```python title:"Metodo .title()" fold:fold
name = 'ada lovelace'
print(name.title()) ## Ada Lovelace
```

## Formattare le stringhe (*f string*)
Per ottenere più facilmente delle stringhe formattate posso ricorrere a questo strumento:

~~~python title:'Esempio di f-string'
age = 20
print(f"I'm {age} years old")
~~~

Utilizzando alcune sequenze di caratteri all'interno di una stringa possiamo modificarne il formato durante la stampa su schermo.

[String minilanguage](https://docs.python.org/3/library/string.html#format-specification-mini-language)
