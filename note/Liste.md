---
tags:
  - Teoria
---
# Definizione

Il linguaggio Python non supporta direttamente gli array (che sono introducibili usando la [[Moduli|libreria]] [NumPy](https://numpy.org/) o [Pandas](https://pandas.pydata.org/docs/index.html)) contiene solo la struttura dati **list**. Le liste sono insiemi di oggetti ordinati in base alla loro posizione al suo interno, alle quali si possono applicare dei metodi:

~~~python title:"Sintassi per la definizione di una lista" ln:false
list_name = [item1,item2]
~~~

Il linguaggio Python ha array (liste) *zero-based* :

~~~python title:"Esempio di numerazione degli elementi di una lista"
us_states = ["Delaware","Pennsylvania"]
print(us_states[0])
~~~

>[!abstract] Nota
Utilizzando  indici negativi sceglierò elementi della lista dal verso opposto

Per aggiungere un elemento alla fine della lista uso il metodo **append**, mentre se voglio aggiungere una lista alla fine di un'altra userò il metodo **extend**

~~~python title:"Metodi .append() ed .extend()"
us_states = ["Delaware","Pennsylvania"]
us_states.append("Ohio")
print(us_states)

countries = ["France","England"]
countries.extend(us_states)
print(countries)
~~~

### Metodi 
| Metodo | Descrizione | Esempio |
| ---- | ---- | ---- |
| `append()` | Aggiunge un elemento al termine della lista | `list.append(element)` |
| `clear()` | Rimuove ogni elemento dalla lista | `list.clear()` |
| `copy()` | Ritorna una copia della lista | `x = list.copy()` |
| `count()` | Ritorna il numero di elementi di un valore specifico | `x = list.count(element)` |
| `extend()` | Aggiunge gli elementi di una lista al termine della lista corrente | `list.extend(["item1","item2"])`<br>oppure<br>`list.extend(list2)` |
| `index()` | Ritorna l'indice del primo elemento che corrisponde al valore specificato | `x = list.index(item_in_list)` |
| `insert()` | Aggiunge un elemento alla posizione specificata | `list.insert(position,item)` |
| `pop()` | Rimuove l'elemento alla posizione specificata | `list.pop(position)` |
| `remove()` | Rimuove il primo elemento che corrisponde al valore specificato | `list.remove(item)` |
| `reverse()` | Capovolge l'ordine della lista | `list.reverse()` |
| `sort()` | Ordina la lista | `list.sort()` |
## Liste annidate

Tra gli oggetti inseribili all'interno di una lista ci sono anche altre liste. Inserendo liste dentro una lista creeremo una *nested list*. Questa funzione è in comune con i [[Dizionari|dizionari]].

~~~python title:"Esempio liste annidate 1"
fruits = ["Strawberries", "Nectarines", "Apples", "Grapes", "Peaches", "Cherries", "Pears"]
vegetables = ["Spinach", "Kale", "Tomatoes", "Celery", "Potatoes"]

dirty_dozen = [fruits, vegetables]

print(dirty_dozen[0])
print(dirty_dozen[1][1])
~~~

```python title:"Esempio liste annidate 2"
line1=['0','0','0']
line2=['0','0','0']
line3=['0','0','0']
game_map = [line1, line2, line3]

print("Hiding your treasure! X marks the spot.")
position = input("Enter position (e.g., a1, b2, c3): ").lower()

abc = ["a", "b", "c"]

if len(position) == 2 and position[0] in abc and position[1].isdigit():
    letter_index = abc.index(position[0])
    number_index = int(position[1]) - 1

    if 0 <= number_index < 3:
        game_map[number_index][letter_index] = "X"
    else:
        print("Invalid number. Use 1, 2, or 3.")
else:
    print("Invalid input format. Use a letter (a–c) followed by a number (1–3).")

print(f"{line1}\n{line2}\n{line3}")
```

## Slicing

Il **list slicing** in Python è una tecnica comune per accedere a una serie di elementi in una lista. Per farlo, utilizziamo l’operatore di **slicing** (due punti `:`). Questo operatore ci permette di specificare da dove iniziare lo slicing, dove terminare e quale passo utilizzare. Il risultato è una nuova lista ottenuta dalla lista originale.

~~~python title:"Sintassi per lo slicing" ln:false
Lst[Inizio : Fine : Passo]
~~~

Dove:

- `Lst` è la lista di cui vogliamo fare lo slicing.
- `Inizio` è l’indice da cui iniziare lo slicing.
- `Fine` è l’indice fino al quale effettuare lo slicing.
- `Passo` rappresenta l’incremento tra gli indici.

Ecco alcuni esempi di list slicing:

### Slicing con indici positivi

Se utilizziamo indici positivi, il primo elemento della lista ha indice 0 e l’ultimo elemento ha indice N-1, dove N è il numero totale di elementi nella lista.

```python title:"Esempio di slicing con indici positivi"
lista = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(lista[3:9:2])  #  Da indice 3 fino a indice 9, ogni 2 -> Output: [4, 6, 8]
```

### Slicing con indici negativi
 
Gli indici negativi rappresentano gli elementi dalla fine della lista. Basta considerare che dalla fine della lista verso l'inizio è come se gli indici partissero da 1

```python title:"Esempio slicing con indici negativi"
Lst = [1, 2, 3, 4, 5, 6, 7]  # 7 elementi, indice da 0 a 6
print(Lst[-1::1])  # Dalla fine della lista -> [7]
print(Lst[-7::1])  # Dall'inizio della lista -> [1, 2, 3, 4, 5, 6, 7]
print(Lst[-1::-1])  # Dalla fine all'inizio -> [7, 6, 5, 4, 3, 2, 1]
print(Lst[-2::-1])  # Dal penultimo all'inizio -> [6, 5, 4, 3, 2, 1]
```

### Campi vuoti nel list slicing:

Lasciando vuoti gli argomenti di inizio, fine o passo, verranno utilizzati i valori predefiniti (0 come inizio, lunghezza della lista come fine e 1 come passo).

```python title:"Esempio slicing con argomenti vuoti"
Lista = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(Lista[::])  # Tutta la lista -> [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(Lista[2::])  # Dal terzo elemento (indice 2) alla fine -> [3, 4, 5, 6, 7, 8, 9]
print(Lista[::2])  # Dall'inizio alla fine, un elemento ogni 2 -> [1, 3, 5, 7, 9]
print(Lista[::-1])  # Tutta la lista, al contrario -> [9, 8, 7, 6, 5, 4, 3, 2, 1]
```

 