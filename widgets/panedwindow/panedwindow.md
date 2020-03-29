# Tkinter Panedwindow
Es un widget que permite agregar y organizar otros widgets en él. Hay dos posibilidades, orientación vertical y horizontal; en la primera se agrega un widget sobre otro, en la segunda se agrega uno al lado de otro. Entre cada widget hay un separador que permite aumentar o disminuir el tamaño del widget respectivo.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con panedwindow

"""
#Importamos las librerías necesarias
import tkinter as tk
  
ventana = tk.Tk() #Ventana principal
  
pw = tk.PanedWindow(orient ='vertical') #Crea el widget panedwindow
  
boton = tk.Button(pw, text ="Botón") #Botón
#Agrega el botón al widget panedwindow
pw.add(boton) 
  
checkbutton = tk.Checkbutton(pw, text ="Checkbutton")  #Chexkbutton
#Agrega el chexbutton al widget panedwindow
pw.add(checkbutton) 
  
label = tk.Label(pw, text ="Label") #Label
#Agrega el label al widget panedwindow
pw.add(label) 
  
#Entry
variable = tk.StringVar() #Variable que guarda el texto del entry
entry = tk.Entry(pw, textvariable=variable, font =('arial', 15, 'bold')) 
variable.set("Entry")
#Agrega el entry al widget panedwindow
pw.add(entry) 
  
# expand se usa para que pueda ampliar el widget
# fill se usa para dejar los widgets ajustarse al tamaño de la ventana principal
pw.pack(fill = tk.BOTH, expand = True) 
  
pw.configure(sashrelief = tk.RAISED) 
  
ventana.mainloop()
```
El resultado es el siguiente:

![ventana panedwindow](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/panedwindow/ventanapanedwindow.png)

Al mover los separadores de los widgets cambia el tamaño así:

![cambio panedwindow](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/panedwindow/cambiopanedwindow.png)

Primero se define la `tk.Tk`, luego se define el panedwindow indicando su orientación. Después, se definen algunos widgets cualquiera para agregar al panedwindow con `pw.add`. Finalmente, se agrega el panedwindow con `pack` y se configura `sashrelief` que modifica el aspecto de los separadores del panedwindow.

[Aquí](https://www.tutorialspoint.com/python3/tk_panedwindow.htm) para ver más opciones de Panedwindow.
