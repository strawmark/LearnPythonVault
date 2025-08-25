---
tags:
  - "#VSCode"
  - Obsidian
  - Windows
---
# Learn Python Vault

Questo vault Obsidian permette di eseguire il codice scritto nei codeblocks in modalità lettura. Una volta installato Python, il percorso dell'eseguibile va indicato nelle impostazioni del plugin *Execute Code* nella sezione:

**Impostazioni** (⚙️) → **Execute Code** → **Language-Specific Settings** → **Python**

Il percorso di default, `python`, normalmente non viene riconosciuto su Windows, quindi andrà messo un percorso diretto, ad esempio:

`C:/Users/Marco/AppData/Local/Programs/Python/Python313/python.exe`
# Python su Windows

1. Installare Python da [sito ufficiale](https://www.python.org/)
2. Verifica la corretta installazione aprendo un [[Aprire un terminale|terminale]] e inviando i comandi:
    - `{sh icon}python --version` 
    - `{sh icon}pip --version`
3. Se ho errori, le variabili da aggiungere al `PATH` sono:
	   - `C:\Users\Username\AppData\Local\Programs\Python\Python3XX`
	   - `C:\Users\Username\AppData\Local\Programs\Python\Python3XX\Scripts`
    Sostituendo **Username** e **Python3xx** con i dati corretti
# Visual Studio Code (alias VSCode o Code)

1. Installare [Visual Studio Code](https://code.visualstudio.com/Download);
2. Installare l'estensione Python per VS Code;
3. Selezionare un interprete Python aprendo il **riquadro comandi** (**CTRL+MAIUSC+P**), iniziare a digitare il comando **Python: Selezionare interprete** da cercare e quindi selezionare il comando. È anche possibile usare l'opzione **Seleziona ambiente Python** nella barra di stato inferiore, se disponibile.