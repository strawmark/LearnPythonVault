---
tags:
  - Setup
  - Windows
---
# Learn Python Vault

Questo vault Obsidian permette di eseguire il codice scritto nei codeblocks in modalità lettura. Una volta installato Python, il percorso dell'eseguibile va indicato nelle impostazioni del plugin *Execute Code* nella sezione:

===**Impostazioni**=== (⚙️) → ==**Execute Code**== → ==**Language-Specific Settings**== → ==**Python**==

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
3. Selezionare un *interprete Python* aprendo il **riquadro comandi** (**CTRL+MAIUSC+P**), iniziare a digitare il comando **Python: Selezionare interprete** da cercare e quindi selezionare il comando. È anche possibile usare l'opzione **Seleziona ambiente Python** nella barra di stato inferiore, se disponibile.
# Creare un ambiente di sviluppo

Solitamente è consigliato creare ambienti virtuali per evitare di dover reinstallare Python in caso di errori nella gestione dei pacchetti, ma anche per non caricare pacchetti non utili ad un determinato progetto.

Se ho bisogno di creare un nuovo ambiente di sviluppo:

`{sh icon}python3 -m venv my_environment`

Per **attivare l'ambiente**: ^c7b2af
- **Linux/Mac**:
    `{sh icon}source my_environment/bin/activate`
- **Windows (PowerShell)**:
    `{sh icon}my_environment\Scripts\Activate`

Nel terminale apparirà "`(my_environment)`" prima della riga di comando a conferma dell'attivazione. Per **disattivare un ambiente** basta usare il comando `{sh icon}deactivate`.
## Aggiungere e rimuovere pacchetti

Se il codice ha già una lista di pacchetti indicata in un file `requirements.txt`, dopo essersi accertati di essere nel giusto ambiente di sviluppo:

`{sh icon}pip install -r requirements.txt`

In alternativa, per **installare un pacchetto**, dopo essersi accertati del nome:

`{sh icon} pip install nomepacchetto`

Mentre per **rimuovere un pacchetto**:

`{sh icon} pip uninstall nomepacchetto`

