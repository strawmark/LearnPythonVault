---
tags:
  - Teoria
---
# Definizione

Una stringa è un array di caratteri. Per delimitare una stringa posso usare gli apici `'`, i doppi apici `"`, o tripli doppi apici `"""` :

~~~python title:"Esempio della stessa stringa"
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
# Manipolazione delle stringhe

Tutte le interazioni tipiche degli array sono possibili con le stringhe, ma con quest'ultime posso eseguire qualche operazione in più grazie all'uso di operatori, [[Funzioni|funzioni]] e metodi specifici: 
## Concatenazione

L'[[Operatori|operatore]] `+` nel campo delle stringhe ne esegue la concatenazione:

~~~Python title:"Concatenazione di stringhe"
age = int(input())
ageString = 'I am ' + str(age) + ' years old.'
print(ageString)
~~~
## Funzioni e metodi

Le funzioni e i metodi utilizzabili sulle stringhe sono molteplici, ecco una tabella di quelli più utili e un [link](https://www.digitalocean.com/community/tutorials/python-string-functions) ad una lista più completa:

|Funzione|Descrizione|Esempio|
|---|---|---|
|`len()`|Lunghezza della stringa|`len("Marco") → 5`|
|`.lower()`|Tutto minuscolo|`"CIAO".lower() → "ciao"`|
|`.upper()`|Tutto maiuscolo|`"ciao".upper() → "CIAO"`|
|`.strip()`|Rimuove spazi iniziali/finali|`" ciao ".strip() → "ciao"`|
|`.replace()`|Sostituisce parti di stringa|`"ciao".replace("a", "e") → "cieo"`|
|`.split()`|Divide la stringa in lista|`"a,b,c".split(",") → ['a','b','c']`|
|`.join()`|Unisce elementi di una lista in una stringa|`",".join(['a','b','c']) → "a,b,c"`|
|`.find()`|Trova la posizione di una sottostringa|`"ciao".find("a") → 2`|
|`.startswith()`|Controlla se inizia con una certa stringa|`"ciao".startswith("c") → True`|
|`.endswith()`|Controlla se finisce con una certa stringa||
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
