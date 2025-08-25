---
tags:
  - Dizionari
  - Variabili
  - Liste
---
# Definizione

I dizionari sono un tipo di dato complesso che associa *chiavi* a *valori*. È rappresentabile facilmente attraverso una tabella:

>[!example] Esempio tabulare di un dizionario
> 
>
>
> | Chiave   | Valore                                        |
> | -------- | --------------------------------------------- |
> | Bug      | Un errore in un programma                     |
> | Funzione | Un pezzo di programma facilmente richiamabile |
> | Ciclo    | Una serie di azioni ripetute                  |

Che diventa:

```python title:"Sintassi per la dichiarazione di un dizionario"
dictionary = {key:value, key2:value}
```

Ogni chiave è unica, mentre i valori possono coincidere.

```python title:"Esempio di dichiarazione di un dizionario" {label='dictex'}
programming_dictionary = {"Bug": "Un errore in un programma", 
                          "Funzione": "Un pezzo di programma facilmente richiamabile",
                          "Ciclo": "Una serie di azioni ripetute"
                         }
```

```python ln:false {import='dictex'}
print(programming_dictionary)
```

Posso creare un dizionario vuoto o cancellarne uno esistente con `{}`:

```python title:"Svuotare un dizionario"
empty_dict = {}
```

Per **richiamare** un elemento del dizionario uso la **chiave** corrispondente:

```python title:"Recuperare di un dato da un dizionario" {import='dictex'}
print(programming_dictionary["Bug"])
```

Posso **aggiungere** (o **ridefinire** se già presente) un valore corrispondente alla chiave:

```python {import='dictex'}
programming_dictionary["Loop"] = "Reiterare un'azione"
print(programming_dictionary)
```

>[!abstract] Nota
>Anche i dizionari possono essere annidati, e posso annidare [[Liste|liste]] in dizionari e viceversa
>
> 
> ```python "Esempio dizionari annidati" {label="dictex2"}
> rubrica = {
>     "Marco": {"telefono": "123", "email": "marco@email.it"},
>     "Luca": {"telefono": "456", "email": "luca@email.it"}
> }
> ```
> 
> ```run-python title: {import='dictex2'}
> print(rubrica["Marco"]["telefono"]) # "123"`
> 
> ```
> 

Un dizionario può anche contenere nomi di funzioni, utilizzabile ad esempio in questo modo:

```python title:"Esempio di dizionario con funzioni"
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    return a / b

operations = {
  "+": add,
  "-": subtract,
  "*": multiply,
  "/": divide
}

num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))
operation_symbol = input("Pick an operation (+, -, *, /): ")

calculation_function = operations[operation_symbol]
answer = calculation_function(num1, num2)
print(f"{num1} {operation_symbol} {num2} = {answer}")
```
