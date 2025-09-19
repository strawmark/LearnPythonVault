---
tags:
  - Teoria
---

# List Comprehension

Si possono creare delle [[Liste|liste]] in una maniera sintatticamente più veloce di un [[Cicli|loop]]:

```python title:Sintassi
new_list = [new_item for item in original_list]
```

Se l'operazione è alquanto complessa, l'uso dei cicli è preferibile, ma in molti casi è possibile riscrivere il loop usando una sola riga di codice. Ad esempio, per aggiungere gli elementi di `numbers` incrementati di 1 nella lista `new_list`:

```python title:"Esempio di aggiunta di elementi in una lista (senza list comprehension)"
numbers = [1, 2, 3]
new_list = []

for n in numbers:
    add_1 = n+1
    new_list.append(add_1)
    
print(new_list)   
```

Ma usando la list comprehension posso inizializzare `new_list` e aggiungere gli elementi con una sola riga:

```python title:"Esempio di aggiunta di elementi in una lista (con list comprehension)"
numbers = [1, 2, 3]
new_list = [n+1 for n in numbers]

print(new_list) 
```

La list comprehension non ha bisogno di liste come input, basta che quest'ultimo sia un oggetto *iterable*:

```python title:"Esempio di uso di list comprehension su una stringa (oggetto iterable)"
name = 'Marco'

letters = [letter for letter in name]

print(letters)
```
## Conditional Comprehension

Possiamo aggiungere delle [[Espressioni condizionali|espressioni condizionali]] all'interno della comprehension per selezionare solo alcuni elementi della lista originale:

```python title:"Sintassi di una list comprehension con espressione condizionale"
new_list = [new_item for item in original_list if test]
```

```python title:"Esempio di conditional comprehension"
odd_list = [n for n in range(1,10) if n%2!=0]

even_list = [n+1 for n in range(1,10) if n%2!=0]

print(odd_list)
print(even_list)
```
# Dictionary Comprehension

La comprehension si può applicare anche ai [[Dizionari|dizionari]].

Da una [[Liste|lista]]:

```python title:"Sintassi dictionary comprehension da una lista"
new_dict = {new_key:new_value for item in original_list}
```

Da un altro dizionario:

```python title:"Sintassi dictionary comprehension da un dizionario"
new_dict = {new_key:new_value for (key,value) in original_dict.items()}
```

>[!abstract] Nota
>Ricorda di usare il metodo `items()` sul dizionario per fare la comprehension

Anche per i dizionari vale la possibilità di aggiungere [[Espressioni condizionali|espressioni condizionali]] allo stesso modo di come avviene nelle liste.

>[!abstract] Iterazione in Pandas
>In pandas possiamo utilizzare il metodo `iterrows()` per iterare un dataframe:
>~~~
nato_dict = {row.letter: row.code for (index, row) in df.iterrows()}
>~~~
