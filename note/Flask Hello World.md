---
tags:
  - Flask
  - Framework
  - Setup
---
Per aggiungere Flask al [[Setup dell'ambiente di sviluppo#Creare un ambiente di sviluppo|proprio ambiente di sviluppo]], basta [[Setup dell'ambiente di sviluppo#^c7b2af|attivare l'ambiente]] in cui si vuole installare il pacchetto del framework e avviare l'installazione con `pip`:

~~~sh
pip install flask
~~~

Creiamo un file `main.py` e:

- [[Moduli|Importiamo]] la [[Classi e Oggetti|classe]] `Flask`
- [[Classi e Oggetti#Metodo costruttore|Instanziamo]] la classe in `app`. Il primo argomento è il nome del pacchetto o del modulo dell'applicazione. In questo caso, `__name__` è sufficiente
- Usiamo il *decorator* ``route(`/`)`` per indicare la root come URL che avvia la funzione `hello_world`
- Ritorniamo una semplice stringa come risultato della funzione

~~~Python title:"Hello world con Flask" 
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World'
~~~

Per avviare un server di test raggiungibile solo da locale:

- Si può usare il comando use the `{sh icon}flask --app main run`
- In alternativa si può usare il comando `{sh icon}python -m flask --app main run`

Di norma basterà puntare il browser della macchina su http://127.0.0.1:5000 o http://localhost:5000 per vedere la pagina HTML generata da Flask.

~~~
 * Serving Flask app 'main'
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
~~~

Per avere un server di test visibile da qualsiasi IP, bisogna aggiungere `--host=0.0.0.0` alla linea di comando:

`{sh icon}flask --app main run --host=0.0.0.0`

Posso anche attivare una **debug mode**, che ricarica il server già avviato non appena il codice viene cambiato. Per avviare un server in modalità debug basta aggiungere l'opzione `--debug` alla linea di comando:

`{sh icon}flask --app main run --host=0.0.0.0 --debug`


