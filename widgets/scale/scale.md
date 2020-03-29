# Tkinter Scale
Permite agregar una barra de desplazamiento que se mueve entre unos valores inicial y final determinados.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con scale

"""
#Importamos las librerías necesarias
import tkinter as tk

#Encuentra el valor del scale y cambia el tamaño de la ventana principal
def sel():
   selection = "Value = " + str(variable.get())
   label.config(text = selection)
   root.geometry(str(int(variable.get()))+"x"+str(int(variable.get())))

root = tk.Tk() #Ventana principal

variable = tk.DoubleVar() #Variable que guarda el valor del scale

scale = tk.Scale( root, variable = variable ,to=0,from_=540 ) #Se crea el scale
scale.pack(anchor = "center")

#Botón para ejecutar la función
button = tk.Button(root, text = "Get Scale Value", command = sel)
button.pack(anchor = "center")

#Label para mostrar el valor del scale
label = tk.Label(root)
label.pack()

root.mainloop()
```
El resultado es el siguiente:

![ventana scale](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/scale/ventanascale.png)

El botón (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) está conectado a la función `sel`, la cual muestra el valor del scale en un label (ver [Tkinter Label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/label.md)) y cambia el tamaño de la ventana principal a un cuadrado de lado igual al valor del scale, como se muestra a continuación:

![funcion scale](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/scale/funcionscale.png)

Después de definir la función y la `tk.Tk`, se define el scale, el botón y el label. Para el scale, además de indicar el widget que lo va a contener, se indican las opciones `variable`, `to` y `from_`. `variable` indica donde se va a guardar el valor del scale, las otras dos opciones indican los límites del scale.

[Aquí](https://www.tutorialspoint.com/python3/tk_scale.htm) para ver más opciones de Scale.
