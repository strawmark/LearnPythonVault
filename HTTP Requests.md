
~~~ Python
import requests
~~~

Ho diversi tipi di richieste:

- **GET**: legge un dato
- **POST**: aggiunge un dato
- **PUT**: aggiorna un dato
- **DELETE**: cancella un dato
## GET

A seconda della API che si vuole usare, bisognerà trovare un **endpoint url** ed eventuali parametri aggiuntivi, solitamente documentati.

```Python title:"Esempio di requests.get()"
payload = {
	"apiKey": news_api_key,
	"q": COMPANY_NAME,
	"sortBy": 'publishedAt'	   
}

r = requests.get(url="https://newsapi.org/v2/everything", params=payload)
```

Altra cosa utile da fare è verificare la presenza di errori nella richiesta, per questo si può utilizzare un metodo che lancerà una eccezione nel caso se ne verifichi uno:

~~~ Python
r.raise_for_status()
~~~

Per ottenere i dati richiesti, solitamente in formato *\*.json* richiamerò il metodo:

~~~ Python
data = r.json()
~~~

Da ora in poi il reperimento delle informazioni dipende da come il file *\*.json* è strutturato.
## POST

~~~ Python
payload = {
	"apiKey": news_api_key,
	"q": COMPANY_NAME,
	"sortBy": 'publishedAt'	   
}

headers = {
    
}

requests.post(url, json=payload, headers= headers)
~~~

## PUT

~~~ Python
requests.put(url, params={key: value}, args)
~~~

## DELETE

~~~ Python
requests.delete(url, params={key: value}, args)
~~~