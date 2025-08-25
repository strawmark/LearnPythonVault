---
tags:
  - Classi
  - Oggetti
  - Funzioni
  - Metodi
  - Variabili
---
# Definizione

#todo 

```python title:"Sintassi della definizione di una classe"
class ClassName:
    # code
```
# Metodo costruttore

~~~python title:"Sintassi definizione di un metodo costruttore"
def __init__(self, parameter1, parameter2):
    # constructor code
~~~

```python title:"Esempio di metodo costruttore di una classe" {label:'classex'}
class Car:
    def __init__(self, seats):
        self.seats = seats      
```

```run-python ln:false {import='classex'}
c = Car(4) # inizializzazione
print(c.seats)

```

Posso anche utilizzare i [[Funzioni#Keyword arguments (`**kwargs`)|kwargs]]:

```python title:"Utilizzare kwargs nel metodo costruttore" {label='kwargsex'}
class Car:
    def __init__(self,**kwargs):
        self.seats = kwargs.get('seats') # get() ritorna None se la chiave non esiste
        self.model = kwargs.get('model')      
```

```python ln:false {import='kwargsex'}
c = Car(model='Nissan', seats = 4)

print(c.model)
```
## Metodi

Per definire le funzioni (dette metodi) di una classe, useremo la sintassi:

```python title:"Sintassi per la definizione di un metodo di una classe" 
def method_name(self, parameter1, parameter2):
    # method code
```

```python {label:'methodex'}
class User:
    def __init__(self, user_id, user_name):
        self.id = user_id
        self.username = user_name
        self.followers = 0
        self.following = 0
    
    def follow(self, user):
        self.following += 1
        user.followers += 1
```

```run-python {import:'methodex'}
user1 = User('001','marco')
user2 = User('002','fabio')

user1.follow(user2)

print(user1.username)
print(user1.followers)
print(user1.following)

print(user2.username)
print(user2.followers)
print(user2.following)
```
