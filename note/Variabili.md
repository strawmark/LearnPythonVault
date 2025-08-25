# Definizione di variabile

Una variabile è un’area di memoria identificata da un **dato al suo interno** ed un **indirizzo unico**. Viene utilizzata per memorizzare e [[Operatori|manipolare dati]] all’interno di un programma. Ognuna ha un nome univoco e al suo interno è presente solo un un tipo di dato specifico che ne definisce il tipo di informazione che contiene. Posso aggregare più variabili (anche di tipo diverso) in una [[Liste|lista]].
# Definire una variabile

Innanzitutto il nome: oltre a sceglierne uno comprensibile nel contesto, è **necessario** seguire alcune regole grammaticali nella scelta del nome:

* Nessun carattere "spazio"
* Composto solo da lettere, numeri e dal carattere underscore `_`
* Il primo carattere **non può** essere un numero

Si segue inoltre lo *snake case* secondo la [[Per iniziare#Guida allo stile|guida allo stile]] di Python:

`{python icon}lower_case_with_underscores = 0`

Se sto definendo una **costante**, si usa scrivere il nome completamente in maiuscolo:

`{python icon}PI = 3.14159`

A differenza di linguaggi "tipizzati" come C o Java, non posso definire una variabile senza contemporaneamente assegnare un valore, perciò la differenza tra il concetto di **dichiarazione** e **definizione** è inesistente.
# Scope delle variabili

Lo **scope** (ambito) definisce la visibilità e la durata di una variabile all'interno di un blocco di codice. A seconda di dove è definita una variabile, certe parti del codice potranno avervi accesso o meno.

Le variabili generalmente assumono lo scope della funzione che contiene la loro definizione. In Python non esiste uno scope per i blocchi di codice (*block scope*), come ad esempio nei blocchi [[Espressioni condizionali|if]] o nei [[Cicli|loop]].

```python title:"Esempio di scope di una variabile"
enemies = 1 # Variabile globale

def increase_enemies():
    enemies = 2 # Variabile locale
    enemies+=1 # incremento della variabile locale
    print(f"enemies inside: {enemies}") #La variabile locale è a 3 

increase_enemies()
print(f"enemies outside: {enemies}") #La variabile globale è rimasta a 1
```

Per modificare una **variabile globale** (ovvero una variabile definita fuori da ogni funzione) dall'interno di una certa funzione dovrò inserire la keyword `global` seguito dal nome della variabile, in modo da poter operare su quella variabile globale invece che su una nuova variabile che ha il suo stesso nome.

```python title:"Esempio di scope utilizzando "global" " hl:4-5
enemies = 1 # Variabile globale

def increase_enemies():
    global enemies
    enemies+=1 # incremento della variabile globale
    print(f"enemies inside: {enemies}") #2

increase_enemies()
print(f"enemies outside: {enemies}") #2
```

Una *best practice* è avere una funzione che esegue la modifica e ritorna il nuovo valore da assegnare alla variabile globale senza farlo in un local scope:

```python hl:3-5,7
enemies = 1 # globale

def increase_enemies():
    print(f"enemies inside: {enemies}") #1
    return enemies + 1 # modifica la variabile globale (guarda sotto)

enemies = increase_enemies() # == enemies = enemies+1
print(f"enemies outside: {enemies}") #2
```

>[!abstract] Nota
In Python e in generale in tutti i linguaggi di programmazione è sconsigliato l'uso esteso di variabili globali.
# Tipi di dato

Il tipo di dato non viene indicato al momento della dichiarazione, viene definito automaticamente appena vi si mette un valore all'interno:

| Tipo di dato                | Esempi                                        |
| --------------------------- | --------------------------------------------- |
| **Numeri interi**           | -2, -1, 0, 1, 2, 3, 4, 5                      |
| **Numeri a virgola mobile** | -1.25, -1.0, -0.5, 0.0, 0.5, 1.0, 1.25        |
| **[[Stringhe\|Stringhe]]**  | `'a'`,`'aa'`,`'aaa'`,`'Hello !'`, `'11 cats'` |
| **Boolean**                 | `True`,`False` (unici valori possibili)       |
>[!abstract] [[Stringhe|Nota]]
>Se un testo contiene un carattere `'` questo potrebbe essere confuso per il termine di fine stringa, in questo caso è utile utilizzare i doppi apici `"` per delimitare inizio e fine della stringa

>[!abstract] Nota
>Per scrivere numeri molto grandi posso usare il carattere underscore `_` per renderli più leggibili dal codice:
>
>
>```python ln:false
>universe_age = 14_000_000_000
>print(universe_age)
>```
## Assegnamento

Per inserire un valore all'interno di una variabile utilizzo l'[[Operatori|operatore]] di assegnamento `=`:

```python title:"Assegnamento di un valore per una variabile" {label='op1'}
num1 = 42 # variabile di tipo int
num2 = 2
```

```run-python {import='op1'}
print(num1)
print(num2)
```

Posso utilizzare le variabili in espressioni ed assegnare il risultato a un'ulteriore variabile:

```python title:"Assegnazione di un valore da un risultato di un'operazione tra due altre variabili" {import='op1' , label='op2'}
num3 = num1 + num2
```

```run-python {import=['op1','op2']} 
print(num3)
```

Inoltre, in Python posso dichiarare una nuova variabile con lo stesso nome di una già esistente, cambiandone anche il tipo (da non confondere con la [[Conversioni di tipo|conversione di tipo]] di una stessa variabile):

```python hl:1,3
var = 23.5
print(var)
var = "Ora sono una stringa"
print(var)

```
## Arrotondamento

### Funzione `round()`

Un modo per formattare l'output di un valore `float` è l'utilizzo di questa funzione, ad esempio se voglio solo una cifra dopo lo zero:

~~~ Python
num = 3.1415 #float
print(round(num,1))
~~~

~~~ output
3.1
~~~
### Operatore `//`

Se voglio rimuovere completamente i numeri dopo la virgola posso utilizzare la divisione intera. Da notare che questo non cambierà il tipo della variabile da `float` in `int`:

~~~ Python
num = 3.1415 #float
print(num // 1)
print(type(num // 1))
~~~