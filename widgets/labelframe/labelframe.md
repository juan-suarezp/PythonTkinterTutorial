# Tkinter Labelframe
El labelframe es un widget que permite agregar otros widgets dentro de él al igual que los frame (ver [Tkinter Frame](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/frame/frame.md)). Además, permite mostrar texto como los label (ver [Tkinter Label](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/label/label.md)).

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con LabelFrame

"""
#Un LabelFrame permite organizar otros widgets dentro de él y mostrar texto
#Importamos las librerías necesarias
import tkinter as tk

ventana = tk.Tk() #Crea la ventana principal

#Se crean dos LabelFrames, uno sobre el otro
labelframe1 = tk.LabelFrame(ventana, text = "LabelFrame 1")
labelframe1.pack()

labelframe2 = tk.LabelFrame(ventana, text = "LabelFrame 2")
labelframe2.pack(side = "bottom")

#Botones en el LabelFrame que está arriba
redbutton = tk.Button(labelframe1, text = "Red", fg = "red")
redbutton.pack( side = "left")

greenbutton = tk.Button(labelframe1, text = "Green", fg="green")
greenbutton.pack( side = "bottom")

bluebutton = tk.Button(labelframe1, text = "Blue", fg = "blue")
bluebutton.pack( side = "left")

#Botón en el LabelFrame que está debajo
blackbutton = tk.Button(labelframe2, text = "Black", fg = "black")
blackbutton.pack( side = "bottom")

ventana.mainloop()
```
El resultado es el siguiente:

![ventana labelframe](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/labelframe/ventanalabelframe.png)

En este ejemplo se crea la tk.Tk y se agregan dos labelframes indicando el widget que los va a contener, dentro del primer labelframe se agregan tres botones y en el segundo labelframe se agrega solo uno. Lo más importante en este ejemplo es que al definir los botones se indica que van a estar en el labelframe y no en la tk.Tk. También, se debe resaltar que los tres mecanismos para gestionar la geometría de los widgets funcionan para ubicarlos dentro de los labelframes.

Al definir los labelframe, se indica el widget que los va a contener y el texto para mostrar al inicio.

[Aquí](https://www.tutorialspoint.com/python3/tk_labelframe.htm) para ver más opciones de Labelframe.
