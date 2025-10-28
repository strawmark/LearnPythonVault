---
tags:
---
## Descrizione

È una funzione che ne contiene un'altra come argomento di ingresso e ne aggiunge funzionalità.

~~~python title:"Struttura di una funzione decorator"
def decorator_function(function):
    
    def wrapper_function():
        #code
        function()
        #code
     
    return wrapper_function
~~~

Un decorator può avere la sola funzione in ingresso:

```python title="Esempio di decorator che rallenta l'esecuzione della funzione" {label='decorator_code'}
import time

def delay(function):
    def wrapper_function():
        time.sleep(2)
        function()
    return wrapper_function
```

```python title:"Funzione con applicato un decorator" {import='decorator_code'}
@delay
def say_hello():
    print("Hello")

say_hello() # Hello, dopo 2 secondi
```

```python title:"Altro esempio" fold
import time

def speed_calc_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"{func.__name__} run speed: {end_time - start_time}s")
        return result
    return wrapper

@speed_calc_decorator
def fast_function():
    for i in range(1000000):
        i * i
 
@speed_calc_decorator
def slow_function():
    for i in range(10000000):
        i * i


fast_function()
slow_function()
```

