# Tkinter Frame
El frame es un widget que permite agregar otros widgets dentro de él. Se usa cuando se va a realizar una ventana con muchos widgets, permitiendo organizarlos fácilmente.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con frame

"""
#Un frame permite organizar otros widgets dentro de él
#Importamos las librerías necesarias
import tkinter as tk

ventana = tk.Tk() #Crea la ventana principal

#Se crean dos frames, uno sobre el otro
frame1 = tk.Frame(ventana)
frame1.pack()

frame2 = tk.Frame(ventana)
frame2.pack(side = "bottom")

#Botones en el frame que está arriba
redbutton = tk.Button(frame1, text = "Red", fg = "red")
redbutton.pack( side = "left")

greenbutton = tk.Button(frame1, text = "Green", fg="green")
greenbutton.pack( side = "bottom")

bluebutton = tk.Button(frame1, text = "Blue", fg = "blue")
bluebutton.pack( side = "left")

#Botón en el frame que está debajo
blackbutton = tk.Button(frame2, text = "Black", fg = "black")
blackbutton.pack( side = "bottom")

ventana.mainloop()
```
El resultado es el siguiente:

![ventana frame](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/frame/ventanaframe.png)

En este ejemplo se crea la `tk.Tk` y se agregan dos frames indicando el widget que los va a contener, dentro del primer frame se agregan tres botones y en el segundo frame se agrega solo uno. Lo más importante en este ejemplo es que al definir los botones se indica que van a estar en el frame y no en la `tk.Tk`. También, se debe resaltar que los tres mecanismos para gestionar la geometría de los widgets funcionan para ubicarlos dentro de los frames.

[Aquí](https://www.tutorialspoint.com/python3/tk_frame.htm) para ver más opciones de Frame.
