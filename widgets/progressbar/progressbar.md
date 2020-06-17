# Tkinter Progressbar
Permite agregar una barra de progreso, puede conectarse con el progreso de una operación.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con progressbar

"""
#Importamos las librerías necesarias
import tkinter as tk
from tkinter import ttk

def aumentar(): #Aumenta 20% de la barra de progreso
    progressbar.step(19.99999999)

ventana = tk.Tk() #Ventana principal

progressbar = ttk.Progressbar(orient=tk.HORIZONTAL) #Barra de progreso
progressbar.pack()
#Cuando llega al 100% se reinicia
    
boton = tk.Button(text = "Aumentar", command = aumentar) #Botón
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana progressbar](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/progressbar/ventanaprogressbar.png)

El botón (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) está conectado con la función `aumentar`, la cual aumenta el 20% de la barra de progreso cada vez que es llamada. Esta es una manera simple de ver el funcionamiento del widget progressbar.

![funcion progressbar](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/progressbar/funcionprogressbar.png)

Primero se define la `tk.Tk`, luego se define la progressbar indicando su orientación. Al final se define la función y el botón.
