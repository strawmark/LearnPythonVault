---
tags:
  - Funzioni
  - Variabili
---
# Definizione

Le conversioni di [[Variabili#Tipi di dato|tipo]] in Python sono simili al ***casting*** visto in altri linguaggi. Può avere natura **implicita** o **esplicita**, ma quest'ultima deve essere fatta attraverso delle [[Funzioni|funzioni]]:

| Funzione  | Esempi                          | Output |
| --------- | ------------------------------- | :----: |
| `int()`   | `int('2')`, `int(float('2.5'))` |   2    |
| `float()` | `float('2.5')`, `float(2)`      |  2.0   |
| `str()`   | `str(24)`                       |  '24'  |
# Controllo del tipo

In fase di [[Input da utente|acquisizione di input]] o per motivi di controllo del flusso potrei aver bisogno di controllare il tipo di una variabile, posso farlo utilizzando la funzione `type()`:

```python title:"Esempio di controllo del tipo di una variabile"
num = 2
print(type(float(num)))
```
