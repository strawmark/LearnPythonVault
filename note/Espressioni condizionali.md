---
tags:
  - Teoria
---

Sono espressioni utili al controllo del flusso di un programma in base al soddisfacimento o meno di determinate [[Operatori#Operatori logici|condizioni]].
# if

Il costrutto `if` verifica la veridicità di una condizione ed esegue un blocco di codice in base al risultato. Il linguaggio Python è sensibile all'indentazione, da tenere conto mentre scriviamo questo tipo di espressioni:

```python title:'Sintassi di if' 
if condition:
    ## codice eseguito se condition == true
else:
    ## codice eseguito se condition == false
```

~~~python title:"Esempio di costrutto if"
height = int(input("What is your heigth in cm? "))

if height >= 120:
    print ("You can ride the rollercoaster")
else:
    print("Sorry, you can't ride the rollercoaster")
~~~

Più di un costrutto `if` può essere **annidato** in un altro:

~~~python title:"costrutti if annidati" 
if condition:
    if anothercondition:
        ## codice (condition e anothercondition == true)
    else:
        ## codice (condition == true, anothercondition == false)
else:
    ## codice eseguito se condition == false (anothercondition non controllata)
~~~

# elif

È un altro costrutto che aggiunge un'altra condizione da verificare se la precedente è falsa: 

~~~Python title:"Sintassi di elif" 
if condition:
    ## codice se condition == true
elif anothercondition:
    ## codice se condition == false, anothercondition == true
else:
    ## codice eseguito se tutte le condizioni precedenti sono false
~~~

Posso aggiungere ulteriori `elif`, ma non dopo il termine `else`.

~~~python title:"Esempio di costrutto elif"
height = int(input("What is your heigth in cm? "))
age = int(input("What is your age? "))

if height >= 120:
    print ("You can ride the rollercoaster")
    if age <= 12:
        print("Please pay $5")
    elif age <= 18: ## 12 < age <= 18
        print("Please pay $7")
    else:
        print("Please pay $12")
else:
    print("Sorry, you can't ride the rollercoaster")
~~~

