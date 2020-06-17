# Tkinter Combobox
Permite agregar un menú desplegable a la GUI. Solo es posible seleccionar una opción de las que se encuentren en el combobox, o si está permitido, es posible agregar otra opción diferente a las que ya están.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con combobox

"""
#Importamos las librerías necesarias
import tkinter as tk
from tkinter import ttk

def mostrar():
    #Verifica si hay algún elemento seleccionado y lo muestra
    if combobox.get() != "":
        print(combobox.get())

ventana = tk.Tk() #Crea la ventana principal

#Insertar 20 elementos
lista = []
for i in range(20):
    lista.append("Elemento {}".format(i))

#Crear el widget combobox
#State controla si se puede ingresar valores al combobox por teclado
combobox = ttk.Combobox(ventana, values=lista, state="readonly")
combobox.pack()
        
#Se crea un botón y se conecta con la función
boton = tk.Button(ventana,text="Mostrar selección",command=mostrar)
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana combobox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/combobox/ventanacombobox.png)

El combobox permite seleccionar alguna de las opciones, el botón está conectado a la función `mostrar` (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) que al ser ejecutada muestra en la terminal el elemento que está seleccionado en el combobox así:

![funcion combobox](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/combobox/funcioncombobox.png)

En este ejemplo, después de crear la ventana principal `tk.Tk`, se crea la lista con los elementos que estarán en el menú. Luego se define el combobox, indicando el widget en el que estará con las opciones `values` y `state`; la primera permite ingresar la lista de opciones que mostrará el combobox y la última es para indicar si se permite o no ingresar más opciones de las que están en `values`.
