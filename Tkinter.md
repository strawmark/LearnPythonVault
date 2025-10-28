#todo

Libreria scritta in diversi linguaggi per gestire un'interfaccia grafica.
## Setup

**Importazione**:

~~~ Python
from tkinter import *
~~~

Non sarà necessario apporre `tkinter.` per richiamare un elemento della libreria

**Creare una finestra**:

~~~ Python
# Finestra principale
window = Tk()
window.title("Titolo finestra")
window.config(padx=50,pady=50) # configurazioni aggiuntive
~~~

Come ultima istruzione del programma, va avviato il loop dell'interfaccia:

~~~ Python
# Ultima istruzione
window.mainloop()
~~~
## Elementi

Per usare correttamente la libreria, ogni elemento andrà creato e assegnato ad una variabile
~~~ Python
label = tkinter.Label(window,text="Nome label")
~~~

Per modificare un'opzione uso `configure()`/`config()`:

~~~ Python
label.configure(font='Arial 12 bold')
~~~

Un modo per collegare controlli agli elementi è l'uso del metodo `bind()`
TODO esempio
### Label

~~~ Python
label = tkinter.Label(window,
					  text="Nome label",
					  font=('Arial',16,'bold'),
					  background='brown',
					  foreground='#FF0'
					  )
~~~

Opzioni comuni:

| Argument       | Values                          | Description                                                     |
| -------------- | ------------------------------- | --------------------------------------------------------------- |
| `text`         | String                          | The text content of the label                                   |
| `textvariable` | StringVar                       | The variable to bind to the contents of the label               |
| `anchor`       | Cardinal direction              | The position of the text relative to the inner<br>margins       |
| `justify`      | `left`, `right`, or<br>`center` | The alignment of the lines of text relative to one<br>another   |
| `foreground`   | Color string                    | The color of the text                                           |
| `wraplength`   | Integer                         | Number of pixels before the text is wrapped to the<br>next line |
| `underline`    | Integer                         | The index of a character in text to underline                   |
| `font`         | Font string or tuple            | The font to be used                                             |
### Button

~~~ Python
def on_button_click():
	print("Click")

button = Button(window, text="Nome tasto", command=on_button_click)
~~~

Posso aggiungere un immagine al tasto usando `PhotoImage`:

~~~ Python
img = PhotoImage(file="image.png")
button = Button(window, image=img, text="Nome tasto", command=on_button_click)
~~~

| Argument       | Values                            | Description                                                                                                                                                                                            |
| -------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `text`         | String                            | The text content of the label on the button                                                                                                                                                            |
| `textvariable` | StringVar                         | The variable to bind to the contents of the label                                                                                                                                                      |
| `font`         | Font string or tuple              | The font to be used                                                                                                                                                                                    |
| `underline`    | Integer                           | The index of a character in text to underline                                                                                                                                                          |
| `command`      | Python function                   | Callback to be executed when the button is clicked.                                                                                                                                                    |
| `default`      | `normal`, `active`,<br>`disabled` | If the button executes when Enter is pushed. active<br>means it will execute in response to Enter, normal<br>means it will only if selected first, and disabled<br>means it will not respond to Enter. |
| `state`        | `normal`, `active`,<br>`disabled` |                                                                                                                                                                                                        |
#### Tasto stile moderno

**Classe**
~~~ Python
class HoverButton(Button):  
    def __init__(self, master, **kwargs):  
        Button.__init__(self, master=master, **kwargs)  
        self.default_background = self['background']  
        self.bind("<Enter>", self.__on_enter)  
        self.bind("<Leave>", self.__on_leave)  
         
    def __on_enter(self, event):  
        self['background'] = self['activebackground']  
        
    def __on_leave(self, event):  
        self['background'] = self.default_background
~~~

**Oggetto**
~~~ Python
start_button = HoverButton(  
    master=window,  
    background=GREEN,  
    foreground=YELLOW,  
    activebackground=RED,  
    activeforeground=PINK,  
    highlightthickness=0,  
    highlightbackground=PINK,  
    highlightcolor=RED,  
    border=0,  
    width=8,  
    height=1,  
    cursor='hand2',  
    font=('Arial', 12, 'bold'),  
    text='Avvia',  
    command=on_button_click  
)
~~~

### Entry

Per far inserire un valore all'utente possiamo creare un entry

~~~ Python
myentry = ttk.Entry(root, textvariable=my_string_var, width=20)
~~~

Per prendere il valore di un entry (in formato stringa) uso `get()`

~~~ Python
def get_entry_value():
    value = entry.get()
    print("Entry value:", value)

entry = tk.Entry(window)
button = Button(window, text="Get Entry Value", command=get_entry_value)

entry.pack()
button.pack()
~~~

Opzioni più comuni:

| Argument       | Values                          | Description                                                                                  |
| -------------- | ------------------------------- | -------------------------------------------------------------------------------------------- |
| `textvariable` | StringVar                       | Tkinter control variable to bind.                                                            |
| `show`         | String                          | Character or string to show when the user types. Useful<br>for password fields, for example. |
| `justify`      | `left`, `right`, or<br>`center` | The alignment of the lines of text relative to one<br>another                                |
| `foreground`   | Color string                    | The color of the text                                                                        |
### Canvas
Per avere finestre più interessanti posso utilizzare un canvas e disegnare forme, scrivere testo

~~~ Python
canvas = Canvas(width=300, height=414)  
background_img = PhotoImage(file="background.png")  
canvas.create_image(150, 207, image=background_img)  
quote_text = canvas.create_text(150,
								207,
								text='Testo',
								width=250,
								font=("Arial", 18, "bold"),
								fill="white"
								)  
canvas.grid(row=0, column=0)
~~~

Per cambiare un elemento di canvas, va usato `canvas.itemconfig()`.
## Posizionamento elementi con grid

Grid posiziona gli elementi in base ad una posizione riga-colonna. Gli indici partono da 0.

~~~ Python
button.grid(row=0,column=0) 
~~~

>[!abstract] Nota
>Non sovrapporre diversi metodi di posizionamento degli elementi

