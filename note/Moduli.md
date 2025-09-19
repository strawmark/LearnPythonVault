---
tags:
  - Teoria
---
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