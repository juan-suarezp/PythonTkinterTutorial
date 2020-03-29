# Tkinter Menu
Permite crear un menú en una ventana, ya sea una `tk.Tk` o una ventana `Toplevel`.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con widget menu para crear un menú en una ventana
principal

"""
#Importamos lo necesario
import tkinter as tk

def donothing(): #Función para ilustrar cómo conectar las opciones del menú
   filewin = tk.Toplevel(root)
   button = tk.Button(filewin, text="Do nothing button")
   button.pack()
   
root = tk.Tk() #Ventana principal

menubar = tk.Menu(root) #Barra principal menú

#Menú file
filemenu = tk.Menu(menubar, tearoff = 0)
#Se agregan las opciones para el primer menú de la barra
filemenu.add_command(label="New", command = donothing)
filemenu.add_command(label = "Open", command = donothing)
filemenu.add_command(label = "Save", command = donothing)
filemenu.add_command(label = "Save as...", command = donothing)
filemenu.add_command(label = "Close", command = donothing)

filemenu.add_separator() #Separador

filemenu.add_command(label = "Exit", command = root.destroy)
#Agregar menú file a la barra principal
menubar.add_cascade(label = "File", menu = filemenu)

#Menú edit
editmenu = tk.Menu(menubar, tearoff=0)
#Se agregan las opciones para el segundo menú de la barra
editmenu.add_command(label = "Undo", command = donothing)

editmenu.add_separator() #Separador

editmenu.add_command(label = "Cut", command = donothing)
editmenu.add_command(label = "Copy", command = donothing)
editmenu.add_command(label = "Paste", command = donothing)
editmenu.add_command(label = "Delete", command = donothing)
editmenu.add_command(label = "Select All", command = donothing)
#Agregar menú edit a la barra principal
menubar.add_cascade(label = "Edit", menu = editmenu)

#Menú help
helpmenu = tk.Menu(menubar, tearoff=0)
helpmenu.add_command(label = "Help Index", command = donothing)
helpmenu.add_command(label = "About...", command = donothing)
#Agregar menú edit a la barra principal
menubar.add_cascade(label = "Help", menu = helpmenu)

root.config(menu = menubar) #Agregar barra principal menú a ventana principal
root.mainloop()
```
El resultado es el siguiente:

![ventana menu](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menu/ventanamenu.png)

La función `donothing` se ejecuta al seleccionar cualquier opción del menú y muestra la siguiente ventana:

![funcion menu](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/menu/funcionmenu.png)

El ejemplo muestra cómo agregar un menú a una ventana principal y cómo agregar pestañas a ese menú. Así mismo, muestra cómo agregar las opciones a cada pestaña.

Se define la función y se crea la `tk.Tk`, luego se crea el menú principal `menubar` indicando que va a estar en la ventana `root`. Después, se crea la primera pestaña llamada `filemenu` indicando que va a estar en el menú `menubar`. Por medio de `filemenu.add_command` se agregan las opciones indicando `label` y `command`. `label` es el texto que mostrará la opción en la pestaña y `command` es la función que ejecutará al ser seleccionada. Además, se usa `filemenu.add_separator` para agregar una línea entre las opciones de la pestaña. Finalmente, se usa `menubar.add_cascade` para agregar la pestaña al menú principal, indicando el texto que va a mostrar con `label` y el menú que se va a agregar con `menu`; en este caso, `File` y `filemenu`. El proceso se repite para las otras dos pestañas agregando diferentes elementos a cada una de ellas.

[Aquí](https://www.tutorialspoint.com/python3/tk_menu.htm) para ver más opciones de Menu.
