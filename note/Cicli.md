---
tags:
  - Teoria
---
# For Loop

Il ciclo for ripete l'esecuzione di un blocco di codice per un numero di volte finito:

~~~python ln:false title:"Sintassi del ciclo for per iterare una lista"
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

```python title:"Sisntassi di un ciclo for con uso della funzione range() tra due variabili"
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

> [!Warning] Attenzione
> La funzione `range()` crea un intervallo di numeri il cui estremo finale non è incluso:
> 
> ```python title:"Limiti della funzione range()"
> numbers = range(1,10)
> print(*numbers)
> ```
> 
> 

# While Loop

Il ciclo `while` viene utilizzato per ripetere un blocco di codice fino a quando non si verifica una certa [[Operatori#Operatori logici|condizione]].

~~~python title:"Sintassi del ciclo while"
while condition_is_true:
    # do something
~~~

```python title:"Esempio di ciclo while" fold
count = 1

while count <= 5:
    print("num:", count)
    count += 1
```

# Modifica del flusso

Capita di dover controllare più direttamente il flusso di un loop, come ad esempio uscire prematuramente per risparmiare cicli o saltare alcuni valori della variabile iteratrice. Per casi di questo tipo è possibile usare `break` o `continue`:
## Break
Serve per uscire immediatamente da un ciclo anche se la condizione di uscita dal ciclo non è si è ancora verificata.

```python title:"Esempio di break di un loop"
for num in range(10):
    if num == 7: # appena arriverà a 7, chiuderà il loop non stampando nulla
        break
    print(num)
```
## Continue
Se voglio saltare l'iterazione corrente, posso usare la keyword `continue`:

```python title:"Esempio di continue in un loop"
for num in range(10):
    if num %2 == 0: # Il ciclo eviterà tutti i numeri pari di range()
        continue
    print(num)
```