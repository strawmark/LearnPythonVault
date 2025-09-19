---
tags:
  - Teoria
---
# Definizione

In alcuni casi bisognerà gestire situazioni particolari dove il codice porta a generare un errore durante la sua esecuzione. Per correggere il programma in caso di questi eventi, si pratica la gestione delle eccezioni con diversi tipi di blocchi di codice:

- `try`/`except`: due blocchi di codice che descrivono il codice che potrebbe generare un'eccezione e il codice che viene eseguito se questa avviene;
- `else`: blocco aggiuntivo che viene eseguito se l'eccezione non avviene;
- `finally`: blocco aggiuntivo che viene eseguito sempre, nonostante si presenti un'eccezione o meno;

È inoltre utile specificare il tipo di eccezione che si vuole gestire, per evitare comportamenti indesiderati in casi di eccezioni multiple.

>[!Warning] Nota
> Questo codice non funziona su Obsidian per la creazione/lettura di file

```python title:"Esempio di blocco try-except"
file = None
try:
    file = open("File.md",'r')
except FileNotFoundError:
    print("File not found, creating a new one")
    file = open("File.md", "w")
else:
    content = file.read()
    print(content)
finally:
    if file is not None:
        file.close()
```
# Lanciare eccezioni (`raise`)

A volte bisognerà generare un errore per segnalare una situazione inaspettata, per farlo uso la keyword `raise`:

```python
height = float(input("Height: "))
weight = int(input("Weight: "))

if height > 3:
	raise ValueError("Human height should not be over 3 meters")

bmi = weight/height **2
print(bmi)
```
