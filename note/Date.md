---
tags:
  - Moduli
  - Funzioni
  - Variabili
---

La gestione delle date/orari in Python è gestita tramite la libreria `datetime`.
## Inizializzazione 


```python {label='datetimeex'}
import datetime as dt
```

Dopo aver creato l'oggetto, posso accedere ai campi `year`,`month`, `day` per le date:

```python title:"Esempio di utilizzo di datetime" {import='datetimeex'}
x = dt.datetime.now() # creo un oggetto datetime con ora corrente
print(x) # Stampa tutti i dati
print(x.day)
```

Oppure `hour`,`minute`,`second`,`microsecond` e `tzinfo` per gli orari.

Posso inizializzare un oggetto *date* con un costruttore:

```python title:"Esempio di date" {label='dateex'}
from datetime import date
date = date(2025,1,1)

print(date)
```
## Formattazione

Per formattare una data utilizzo il metodo `strftime()`. Ad esempio, per avere un [[Date#Tabella formati|formato]] del tipo '`gg-mm-aaaa`':

```python title:"Formattazione di un oggetto date" {import='dateex'}
format = "%d-%m-%Y"
date_formatted = date.strftime(format)

print(date_formatted)
```

## Tabella formati

| Directive | Description                                                         | Example                  |
| --------- | ------------------------------------------------------------------- | ------------------------ |
| `%a`      | Giorno della settimana, versione corta                              | Wed                      |
| `%w`      | Giorno della settimana come numero da 0 a 6, 0 è Domenica           | 3                        |
| `%d`      | Giorno del mese (01-31)                                             | 31                       |
| `%b`      | Nome del mese, versione corta                                       | Dec                      |
| `%B`      | Nome del mese                                                       | December                 |
| `%m`      | Mese come numero da 1 a 12                                          | 12                       |
| `%y`      | Anno, versione corta senza secolo                                   | 18                       |
| `%Y`      | Anno                                                                | 2018                     |
| `%H`      | Ora 00-23                                                           | 17                       |
| `%I`      | Ora 00-12                                                           | 05                       |
| `%p`      | AM/PM                                                               | PM                       |
| `%M`      | Minuti 00-59                                                        | 41                       |
| `%S`      | Secondi 00-59                                                       | 08                       |
| `%f`      | Microsecondi 000000-999999                                          | 548513                   |
| `%z`      | UTC offset                                                          | +0100                    |
| `%Z`      | Timezone                                                            | CST                      |
| `%j`      | Numero del giorno nell'anno 1-366                                   | 365                      |
| `%U`      | Numero della settimana nell'anno (Domenica come primo giorno) 00-53 | 52                       |
| `%W`      | Numero della settimana nell'anno (Lunedì come primo giorno) 00-53   | 52                       |
| `%c`      | Versione localte di data e ora                                      | Mon Dec 31 17:41:00 2018 |
| `%C`      | Secolo                                                              | 20                       |
| `%x`      | Versione locale della data                                          | 12/31/18                 |
| `%X`      | Versione locale dell'ora                                            | 17:41:00                 |
| `%%`      | Il carattere %                                                      | %                        |
| `%G`      | Anno secondo ISO 8601                                               | 2018                     |
| `%u`      | Giorno della settimana secondo ISO 8601 (1-7)                       | 1                        |
| `%V`      | Numero di settimana secondo ISO 8601 (01-53)                        | 01                       |
