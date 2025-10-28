---
tags:
  - Teoria
---
## Descrizione e utilizzo

I **moduli** sono collezioni di [[Funzioni|funzioni]], [[Variabili|variabili]] e [[Classi e Oggetti|classi]] che possono essere importati nel codice per essere utilizzati, generando una dipendenza in fase di compilazione:

>[!info] Attenzione
> L'esecuzione del codice in questa pagina non funziona

```python title:"my_module.py"
pi = 3.1415
```

```python title:"main.py"
import my_module

print(my_module.pi)
```

Se si vuole importare solo **parti** di un file si può scrivere ad esempio:

```python
from module import variable1,variable2
```

Per importare **tutto** un modulo:

```python
from module import *
```

## Attributi speciali

Sono degli attributi di sola lettura per certi tipi di oggetti. Alcuni di questi sono riportati dalla funzione `dir()`:

|                              |                                                                                                                                                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `definition.__name__`        | The name of the class, function, method, descriptor, or generator instance.                                                                                                                                                                                                            |
| `definition.__qualname__`    | The [qualified name](https://devdocs.io/python~3.13/glossary#term-qualified-name) of the class, function, method, descriptor, or generator instance.                                                                                                                                   |
| `definition.__module__`      | The name of the module in which a class or function was defined.                                                                                                                                                                                                                       |
| `definition.__doc__`         | The documentation string of a class or function, or `None` if undefined.                                                                                                                                                                                                               |
| `definition.__type_params__` | The [type parameters](https://devdocs.io/python~3.13/reference/compound_stmts#type-params) of generic classes, functions, and [type aliases](https://devdocs.io/python~3.13/library/typing#type-aliases). For classes and functions that are not generic, this will be an empty tuple. |
### `__main__`

In Python, il nome speciale `__main__` è usato per due costrutti legati all'utilizzo dei moduli:

1. Il nome dell'ambiente top-level del programma, che può essere controllato con l'[[Operatori#Operatori di confronto|espressione]] `__name__ == '__main__'`, ovvero l'ambiente specificato dall'utente che importa tutti gli altri moduli necessari al programma
2. Il file `__main__.py` nei pacchetti Python.

Quando un modulo o un pacchetto Python vengono importati, `__name__` coincide con il nome del modulo, usualmente il nome del file Python senza l'estensione `.py`.

In sostanza, se scrivo:

~~~
if __name__ == '__main__':
    ...
~~~

Il codice sotto la `if`, viene eseguito solo se il modulo non è stato importato in un altro programma, ovvero solo se è il file principale del programma.

