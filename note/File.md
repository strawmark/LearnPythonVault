---
tags:
  - Teoria
---

È possibile gestire i file in più modi con [[Python]].

# Aprire e leggere/scrivere file
### `open()`

```python title:"Esempio di apertura di un file"
filename="File.md"
open(filename, mode='r', buffering=-1, encoding=None, newline=None, opener= None)
```

**Argomenti obbligatori**:
- `filename` è una stringa con il **percorso relativo** e nome del file da aprire
- `mode` è una stringa che indica la modalità di accesso al file, al quale si può aggiungere anche uno specificatore per indicare come andrà maneggiato il file

| Simbolo | Descrizione                                  |
| ------- | -------------------------------------------- |
| `'r'`   | lettura (default)                            |
| `'w'`   | scrittura, prima tronca il file              |
| `'x'`   | creazione, da errore se il file già esiste   |
| `'a'`   | scrittura, scrive in fondo al file se esiste |
| `'b'`   | binary mode                                  |
| `'t'`   | text mode (default)                          |
| `'+'`   | apre per aggiornamento (lettura e scrittura) |

**Argomenti opzionali**:
- `buffering` è un intero che indica la grandezzabuffer utilizzato
	- `0`: buffering off (modalità binary)
	- `1`: line buffer in (modalità testo)
	- >`1` : grandezza buffer in byte scelta (modalità binary)
- `encoding` è una stringa che indica la codifica dei caratteri nel file, usato in modalità testo
- `errors` è una stringa che indica come vanno gestiti gli errori di codifica

| error                 | Descrizione                                                                                                                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `'strict'`            | (identico al default `'None'`) lancia una eccezione [`ValueError`](https://devdocs.io/python~3.12/library/exceptions#ValueError "ValueError")                                                                |
| `'ignore'`            | ignora gli errori, potrebbe generare perdita di dati                                                                                                                                                         |
| `'replace'`           | Usa un carattere dove si trova un errore nel dato                                                                                                                                                            |
| `'surrogateescape'`   | Utile per file con codifica sconosciuta, rappresenta i byte errati con low surrogate code unit tra U+DC80 e U+DCFF. Verrano ritornati ai vecchi valori quando il `surrogateescape` error handler verrà usato |
| `'xmlcharrefreplace'` | (Solo in modalità scrittura). Caratteri non supportati verranno rimpiazzati con un carattere XML appropriato                                                                                                 |
| `'backslashreplace'`  | Rimpiazza con sequenze di escape                                                                                                                                                                             |
| `'namereplace'`       | (Solo in modalità scrittura) rimpiazza con sequenze di escape `\N{...}`                                                                                                                                      |
- `newline` determina come trattare i caratteri newline


~~~python title:"Apertura di un file usando argomenti opzionali"
open("file1.txt",'rt', encoding='utf8')
~~~

Per evitare [[Eccezioni|eccezioni]] in caso di apertura di un file posso scrivere:

~~~ Python
import os
import sys

filename = 'file1.txt'

try:
	f = open(filename,'rb')
	with f:
		data = f.read()
		
except OSError:
	print(f'Could not read/open file: {filename}')
	sys.exit()
~~~

### `with`

Un modo più semplice ed elegante di aprire i file è usare `with`:

~~~python title:"Uso di with per l'apertura di un file"
with open(filename,'rb') as f:
	data = f.read()
~~~

Aprendo così un file non dovrò aggiungere il metodo `f.close()` alla fine delle operazioni, dato che `with` farà questo lavoro automaticamente.
### Lettura con `read()`
Usare il metodo `read()` su un oggetto file ritornato da `open()` permette di leggere l'intero file. Specificando un intero indico il **numero di caratteri o di byte** da leggere.

~~~python title:"Esempio di lettura con read() specificando il numero di caratteri/byte da leggere"
file.read(2) # Legge 2 caratteri (byte in byte mode) del file
file.read(-1) # Legge l'intero file (comportamento di default)
~~~

### Scrittura con `write()`

~~~python title:"Esempio di scrittura di testo su un file"
file.write('Testo')
~~~

Aggiunge il contenuto al file. In caso di apertura con `'w'`,  anche non mettendo `file.write()` si eliminerà tutto il contenuto scritto in precedenza. `file.write()` successivi metteranno in coda nuovi dati, quindi non andrà aggiunto il contenuto tutto assieme.
# Rimuovere file

Importando il modulo `os` è possibile fare più operazioni con i file, come ad esempio cestinarli:

~~~python title:"Rimozione di un file con os.remove()"
import os
os.remove('file1.txt')
~~~
