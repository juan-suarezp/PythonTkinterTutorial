# Tkinter Entry
Es un widget que permite agregar una sola línea de texto al usuario.
- Si quiere permitir agregar varias líneas de texto usar el widget [Text](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/text/text.md).
- Si quiere mostrar pero no permitir editar varias líneas de texto usar el widget [Label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/label.md) o [Message](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/message/message.md).

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con entry

"""
#Importamos las librerías necesarias
import tkinter as tk

def accion():
    #Comprueba texto del label y del entry
    if variable1.get() == variable.get():
        print("Correcto")
    else:
        print("Incorrecto")

ventana = tk.Tk() #Crea la ventana principal
ventana.geometry("250x100")

variable1 = tk.StringVar() #Variable que guarda el texto del label
variable1.set("Er54xsW") #Cambia el texto de la variable
#Se crea el label y se conecta con variable1
label = tk.Label(ventana,textvariable=variable1)
label.pack()

variable = tk.StringVar() #Variable que guarda el texto del entry
#Se crea el entry y se conecta con variable
entrada = tk.Entry(ventana,textvariable=variable,bd = 5,width=20)
entrada.pack()

#Crea el botón y lo conecta con la función
boton = tk.Button(ventana,text="Verificar",command=accion)
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana entry](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/entry/ventanaentry.png)

El botón está conectado a la función `accion` (Ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)), la cual comprueba si el texto en el label (Ver [Tkinter Label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/label.md)) es igual al texto en el entry, mostrando en la terminal "correcto" o "incorrecto".

![funcion entry](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/entry/funcionentry.png)

Primero se crea la `tk.Tk`, luego se define el label, el entry, la función y el botón. Para el entry se usan las opciones `textvariable`, `bd` y `width`. `textvariable` es para indicar la variable que guarda el texto que contiene el entry, `bd` crea un borde en el widget y `width` define el ancho.

[Aquí](https://www.tutorialspoint.com/python3/tk_entry.htm) para ver más opciones de Entry.
