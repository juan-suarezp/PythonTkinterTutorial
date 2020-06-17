# Tkinter Label
Permite mostrar texto, es posible cambiarlo pero no directamente por el usuario.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con label

"""
#Importamos las librerías necesarias
import tkinter as tk

def accion(): #Suma 1 al valor anterior del label
    cont = int(variable.get())
    cont = cont+1
    variable.set(str(cont))

ventana = tk.Tk() #Crea la ventana principal
ventana.geometry("200x100")

#Label con mensaje inicial que no cambia
label1 = tk.Label(ventana,text="Mensaje sin cambiar")
label1.pack()

#Label con mensaje inicial que cambia
variable = tk.StringVar()
variable.set("0") #Texto inicial
label2 = tk.Label(ventana,textvariable=variable)
label2.pack()
    
#Se crea el botón y se conecta con la función
boton = tk.Button(ventana,text="Aumentar",command=accion)
boton.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/ventanalabel.png)

En la `tk.Tk` se agregan dos labels y un botón. Uno de los label tiene un mensaje inicial que no tiene posibilidad de cambio, mientras el otro label cambia cada vez que se presiona el botón. La función `acción` está conectada con el botón (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) y al ser ejecutada realiza el cambio en el label como se observa a continuación:

![funcion label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/funcionlabel.png)

Al definir los label, se indica el widget que los va a contener y el texto para mostrar al inicio. Si se desea cambiar el texto que hay en un label, se define `textvariable` que guarda el texto que hay en el label en una variable. Con esta variable se tiene la posibilidad de recuperar el texto que contiene (`variable.get`) o cambiarlo (`variable.set`).

[Aquí](https://www.tutorialspoint.com/python3/tk_label.htm) para ver más opciones de Label.
