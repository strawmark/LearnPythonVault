---
tags:
  - Teoria
---
# Usare una funzione

Per **richiamare** l'uso di una funzione:

~~~Python title:"Chiamata di una funzione"
my_function(argument1,argument2)
~~~

Posso anche richiamarla usando i nomi dei parametri, per evitare errori:

~~~ Python title:"Chiamata di una funzione (con keyword)"
my_function(argument1=parameter1, argument2=parameter2)
~~~

# Creare una funzione

Per **definire** una funzione diversa da quelle built-in nell'interprete Python:

~~~python title:"Definzione di una funzione"
def my_function(parameter1, parameter2):
    #code
~~~

C'è da notare che il codice all'interno della funzione ha un'indentazione (generalmente ottenuta premendo il tasto **TAB**) rispetto alla prima riga, questo perché Python usa le indentazioni al posto delle parentesi per delimitare i blocchi di codice come funzioni, classi, ecc. .

Per **ritornare** un output utilizzo la keyword `return`:

~~~Python hl:3
def my_function(parameter1, parameter2):
    #code
    return out
~~~

Possiamo fornire dei cosiddetti ***type hints*** per indicare il tipo dei parametri e il tipo di ritorno della funzione:

~~~Python title:"Definizione con type hints" hl:1
def my_function(parameter1:int, parameter2:float) -> str:
    #code
    return out # out sarà di tipo stringa
~~~

Python normalmente riesce a capire quali tipi di dato stiamo per chiedere o ritornare con una funzione, usare i type hints permette di risalire più facilmente all'origine di eventuali bug, documentare implicitamente il codice e aiutare i tool degli IDE per la rilevazione di errori. Se il progetto diventa complesso, passare ai type hint è la mossa più indicata, benché non obbligatoria.
## Docstrings

Una *docstring* è una stringa a inizio del codice di una funzione che ne spiega il funzionamento in breve. Per crearne una uso i tripli apici `"""`. Una docstring può essere anche su più linee. In questi casi si sceglie per una prima linea breve di descrizione, una vuota, e poi una descrizione più esaustiva, o con informazioni sui [[Variabili|parametri]] e sulle [[Eccezioni|eccezioni]].


```python title:"Esempio di docstring" {label='docstring1'}
def is_leap(year):
    """ Ritorna True se year è bisestile """
    return year % 400 == 0 or (year % 100 != 0 and year % 4 == 0)
```

```run-python ln:false {import='docstring1'}
res = is_leap(2025)
print(res)
```

```python title:"Docstring su più linee" {label='docstring2'}
def average(values: list[float]) -> float:
    """
    Calcola la media aritmetica di una lista di numeri.

    Args:
        values (list[float]): Lista di numeri decimali.

    Returns:
        float: La media dei valori forniti.

    Raises:
        ValueError: Se la lista è vuota.
    """
    if not values:
        raise ValueError("La lista non può essere vuota.")
    return sum(values) / len(values)
```

```run-python ln:false {import='docstring2'}
values=[1.0,2.0,3.0]
print(average(values))
```

Le *docstring* sono molto utili per documentare il codice. Molti IDE le riconoscono le mostrano al passaggio del mouse sul nome della funzione.
## Funzioni come input (Higher Order Functions)

È possibile definire funzioni che operano utilizzando altre funzioni come input. Tra i possibili parametri in ingresso a una funzione infatti può anche esserci un'altra funzione:

```python {label='hof'}
def calc(num1, num2, func): # High Order Function
    return func(num1, num2)

def add(num1, num2):
    return num1+num2

def multiply(num1, num2):
    return num1*num2
```

```run-python ln:false {import='hof'}
res = calc(1, 2, add)
print(res) # 1+2 = 3
```

## Argomenti di default

Posso avere argomenti di default in modo da poter specificare solo gli argomenti che andranno modificati. Utile per funzioni con molti argomenti.

```python title:"Definizione di una funzione con argomenti di default" hl:1 {label='defaultargs'}
def foo(num1=0, num2=1, num3=2): 
    print(num1,num2,num3)
```

Quindi ho impostato di default `num1 = 0`, `num2 = 1` e `num3 = 2`.

```run-python ln:false {import='defaultargs'}
foo() # 0 1 2
foo(1) # 1 1 2
foo(num2=3) # 0 3 2
```

> [!Warning] Attenzione
> Se do un nuovo valore usando un argomento posizionale dopo uno con nome ottengo un errore di sintassi:

```run-python ln:false error:1 title:"Errore tipico" {import='defaultargs'}
foo(num2=3,1) # 0 3 1 ?? 
```

Ho almeno tre modi per risolvere:

1. Passare gli argomenti con nome **dopo** quelli posizionali  
2. Passare tutti gli argomenti come *argomenti posizionali*
3. Passare tutti gli argomenti come *argomenti con nome* 
## Argomenti infiniti

### Argomenti posizionali (`*args`)
Posso usare la keyword `*` (solitamente `*args`) per rendere indefinito il numero di argomenti in ingresso:

```python title:"Definizione con argomenti posizionali infiniti (*args)" {label='infargs1'}
def add(*args):
    res = 0
    for n in args:
        res+=n
    print(res)
```

```run-python ln:false {import='infargs1'}
add() # 0
add(1) # 1 
add(1, 2) # 3
add(3,1) # 4
```

Da notare c'è anche che `args` non è una parola riservata, al suo posto posso ad esempio usare `numbers` per indicare il nome della [[tupla]] dove voglio raccogliere tutti i numeri in ingresso.

### Keyword arguments (`**kwargs`)

Con la keyword `**` (solitamente `**kwargs`) verrà creato un [[Dizionari|dizionario]] degli argomenti con nome (keyword arguments) in input alla funzione, molto utile per creare i [[Classi e Oggetti#Metodo costruttore|costruttori di una classe]]:

```python title:"Definizione di una funzione con keyword argument infiniti" {label='infargs2'}
def calculate(**kwargs):
    print(kwargs)
```

```run-python ln:false {import='infargs2'}
calculate(add=2,multiply=4) # {'add':2,'multiply':4}
```

Posso anche usare argomenti posizionali assieme agli argomenti infiniti:

```python {label:'infargs3'}
def calculate(n,**kwargs):
    n+=kwargs["add"]
    n*=kwargs["multiply"]
    print(n)
```

```run-python ln:false {import='infargs3'}    
calculate(1,add=4,multiply=5) # 25
```

In questo caso, l'ordine di inserimento conta:

1. Argomenti standard
2. `*args`
3. `**kwargs`

**Esempio di funzione corretta**

```python {label:'correct_func'}
def my_function(a, b, *args, **kwargs):
    print(f"{a}, {b}")
    
    for arg in args:
        print(arg)
    
    for arg in kwargs.items():
        print(f"{arg}")
    
    print("pass")
```

```run-python {import:'correct_func'}
my_function(1, 2, 3, 4, 5, k=1, c=2)
```

**Esempio di funzione errata**

```python {label:'wrong_func'}
def my_function(a, b, **kwargs, *args):
    print("pass")
    pass
```

```run-python {import:'wrong_func'}
my_function(1, 2, k=1, c=2, 3,4,5)
```