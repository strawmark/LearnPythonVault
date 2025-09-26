---
tags:
  - Teoria
---
# Operatori aritmetici

I seguenti operatori sono in ordine di precedenza:

| Operatore | Operazione       | Esempio   |        |
| :-------: | ---------------- | --------- | ------ |
|   `**`    | Esponente        | `2**3`    | `8`    |
|    `%`    | Modulo/Resto     | `22 % 8`  | `6`    |
|   `//`    | Divisione intera | `22 // 8` | `2`    |
|    `/`    | Divisione        | `22 / 8`  | `2.75` |
|    `*`    | Moltiplicazione  | `3 * 5`   | `15`   |
|    `-`    | Sottrazione      | `5 - 2`   | `3`    |
|    `+`    | Addizione        | `2 + 2`   | `4`    |

## Operatori di assegnazione

`+=`,`-=`,`/=`, `*=` si usano come ultime operazioni, servono per aggiungere/sottrarre ecc. un valore a una variabile e aggiornarla nello stesso passaggio. Il più noto esempio è l'incremento di un contatore:

```python title:"Uso di +="
count = 0

count = count+1
print(count)

count+=1
print(count)
```

# Operatori logici

Utili per deviare il flusso del codice a seconda della presenza di condizioni particolari. Questi sono `and`,`or` e `not`.

| Operatore | Significato                            |     Esempio      | Risultato |
| :-------: | -------------------------------------- | :--------------: | :-------: |
|   `and`   | Tutte le condizioni devono essere vere | `True and False` |  `False`  |
|   `or`    | Almeno una condizione deve essere vera | `True or False`  |  `True`   |
|   `not`   | Inverte il valore booleano             |    `not True`    |  `False`  |
## Operatori bitwise

|  Operatore   | Nome        | Simbolo | Funzione                                                                 |
| :----------: | ----------- | ------- | ------------------------------------------------------------------------ |
|   **AND**    | Bitwise AND | `&`     | Restituisce 1 solo se entrambi i bit sono 1                              |
|    **OR**    | Bitwise OR  | `       | Restituisce 1 se almeno uno dei bit è 1                                  |
|   **XOR**    | Bitwise XOR | `^`     | Restituisce 1 se i bit sono diversi                                      |
|   **NOT**    | Bitwise NOT | `~`     | Inverte tutti i bit (attenzione ai numeri negativi in complemento a due) |
| **SHIFT SX** | Shift left  | `<<`    | Sposta i bit a sinistra (moltiplica per potenze di 2)                    |
| **SHIFT DX** | Shift right | `>>`    | Sposta i bit a destra (divide per potenze di 2)                          |
# Operatori di confronto

| Operatore | Nome                |
| :-------: | ------------------- |
|  **==**   | uguale a            |
|    !=     | diverso da          |
|     >     | maggiore di         |
|     <     | minore di           |
|    >=     | maggiore o uguale a |
|    <=     | minore o uguale a   |
# Operatori di identità

| Operatore  | Funzione                                                            |
| :--------: | ------------------------------------------------------------------- |
|   **is**   | Verifica se le due variabili sono lo stesso elemento in memoria     |
| **is not** | Verifica se le due variabili non sono lo stesso elemento in memoria |
# Operatori di appartenenza
| Operatore  | Funzione                                                                                                 |
| :--------: | -------------------------------------------------------------------------------------------------------- |
|   **in**   | Verifica se l'elemento è dentro una sequenza ([[Liste\|lista]], [[Stringhe\|stringa]], [[Array\|array]]) |
| **not in** | Verifica se l'elemento non è presente in una sequenza                                                    |
# Concatenazione delle stringhe

L'operatore `+` viene utilizzato per [[Stringhe#Concatenazione|concatenare due stringhe tra loro]].

