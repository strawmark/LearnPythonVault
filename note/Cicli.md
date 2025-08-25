---
tags:
  - Loop
---
# For Loop

~~~python ln:false title:"Sintassi del ciclo for"
for item in list_of_items:
    # do something to each item
~~~

```python title:"Esempio ciclo for" fold
fruits = ["Apple", "Peach", "Pear"]

for fruit in fruits: # fruit è l'indice
    print(fruit)
    print(fruit + " Pie")
```

Se non sto usando liste uso `range()` per eseguire il ciclo per un certo numero di volte:

```python title:"Utilizzo della funzione range() tra due variabili"
for number in range(a,b):
    # do something
```

```python title:"Utilizzo della funzione range tra due numeri fissati"
for number in range(1,10):
    print(number)
```

Posso scegliere lo step della funzione `range()` aggiungendo un argomento:

```python title:"Uso dell'argomento per il passo dell'incremento della funzione range()"
for number in range(1,11,3): # ogni 2
    print(number)
```

# While Loop

~~~python title:"Sintassi del ciclo while"
while condition_is_true:
    # do something
~~~

#todo