---
tags:
  - Flask
  - Framework
---
## Introduzione

Utilizzando i Python [[Funzioni decorator|decorator]] posso collegare un percorso URL ad una funzione:

~~~Python
@app.route('/')
def index()
    return 'Index page'

@app.route('path')
def foo()
    return 'Hello'
~~~

Con `path` il **percorso della pagina web** che deve essere raggiunta per chiamare la funzione.

```python fold {label='imports'}
from flask import Flask
app = Flask(__name__)
```

```python {import='imports'}
@app.route('/')
def hello_world():
    return 'Hello World'

@app.route('/greet/{name}')
def greet(name):
    return f'Hello {name}!'
```

Posso creare path dinamici, con parti delle URL che determinano il comportamento della funzione
## Regole delle variabili 

Si possono inserire sezioni variabili in un URL marcando le sezioni con `<variable_name>`. La funzione riceverà `<variable_name>` come [[Funzioni#Keyword arguments (`**kwargs`)|keyword argument]]. Opzionalmente, si può specificare una conversione per specificare il tipo dell'argomento `<converter:variable_name>`.

```python
from markupsafe import escape

@app.route('/user/<username>')
def show_user_profile(username):
    return f'User {escape(username)}'

@app.route('/post/<int:post_id>')
def show_post(post_id):
    return f'Post {post_id}'

@app.route('/path/<path:subpath>')
def show_subpath(subpath):
    return f'Subpath {escape(subpath)}'
```

Posso indicare queste conversioni:

| Converter |                                               |
| --------- | --------------------------------------------- |
| `string`  | (default) accetta qualsiasi testo senza slash |
| `int`     | accetta positivi interi                       |
| `float`   | accetta numeri in virgola mobile positivi     |
| `path`    | come `string` ma accetta anche '/'            |
| `uuid`    | Accetta stringhe UUID                         |
### URL uniche e reindirizzamento

Le due seguenti regole differiscono per un "`/`" :

```Python hl:1,5
@app.route('/projects/')
def projects():
    return 'The project page'

@app.route('/about')
def about():
    return 'The about page'
```

- L'URL canonico di `projects` ha uno slash finale: raggiungendo l'URL `/projects`, Flask farà un reindirizzamento verso l'URL canonico `/projects/`.
- L'URL canonico di `about` non ha uno slash finale: raggiungendo l'URL `/about/` si otterrà un errore *404 “Not Found”*. Questo serve per mantenere le URL uniche per questo tipo di risorse, e anche per evitare le doppie indicizzazioni da parte dei motori di ricerca.
### Metodi HTTP

Le applicazioni web utilizzano dei metodi HTTP quando accedono alle URL. Il metodo di default è `GET`, mentre tutti gli altri vanno specificati per essere utilizzati. Per specificarli, vanno listati all'interno del keyword argument `methods` della [[Funzioni decorator|decorator function]] `route()`.

```python title:"Utilizzo dei metodi nella decorator function"
from flask import request

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        return do_the_login()
    else:
        return show_the_login_form()
```

La stessa funzione può rispondere a più metodi, ma è più comune definire una funzione per ciascun metodo.

La separazione può essere fatta anche con metodi differenti da `route()`, Flask ha dei metodi scorciatoia per i metodi HTTP come `get()` o `post()` per quelli più comuni:

```python
@app.get('/login')
def login_get():
    return show_the_login_form()

@app.post('/login')
def login_post():
    return do_the_login()
```

