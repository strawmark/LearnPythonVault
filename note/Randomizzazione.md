---
tags:
  - Teoria
---

Per generare numeri casuali posso utilizzare il [[Moduli|modulo]] random. Per utilizzarlo:

```python
import random
```

```python title:"Esempio di uso del modulo 'random'"
import random

random_integer = random.randint(1, 10) # int [1,10]
print(random_integer)

random_float = random.random() # float [0,1)
print(random_float)

random_float = random.random() * 5 # float [0,5)
print(random_float)
```

