# Tkinter Canvas
Permite agregar espacios rectangulares para dibujar líneas, polígonos, arcos, óvalos o mostrar imágenes.

## Ejemplo

```python
# -*- coding: utf-8 -*-
"""
Ejemplo de ventana básico con canvas para dibujar

"""
#Importamos las librerías necesarias
import tkinter as tk

def accionArc():
    #Dibuja un arco
    canvas.create_arc(10,10,250,250, start = 0, extent = 150, fill = "blue")
    
def accionLine():
    #Dibuja una línea
    canvas.create_line(20,20,250,250,fill = "white")

ventana = tk.Tk() #Crea la ventana principal
ventana.geometry("500x500") #Tamaño de la ventana en pixeles

#Espacio para dibujar
canvas = tk.Canvas(ventana,bd = 10,bg ="black")
canvas.pack()

#Botones para las acciones
botonArc = tk.Button(ventana,text="Arco",command=accionArc)
botonArc.pack()

botonLine = tk.Button(ventana,text="Línea",command=accionLine)
botonLine.pack()

ventana.mainloop()
```
El resultado es el siguiente:

![ventana canvas](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/canvas/ventanacanvas.png)

Los botones (ver [Tkinter Button](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/button/button.md)) `Arco` y `Línea` están conectados respectivamente con las funciones `accionArc` y `accionLine`. Al presionar el botón `Arco` resulta:

![canvasarco](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/canvas/arcocanvas.png)

`canvas.create_arc` dibuja un arco, se debe indicar las coordenadas y es posible indicar el ángulo inicial, el ángulo final y el color del arco.

Luego se presiona el botón línea:

![canvaslinea](https://github.com/juan-suarezp/PythonTkinterTutorial/blob/master/widgets/canvas/lineacanvas.png)

`canvas.create_line` dibuja una línea, se debe indicar las coordenas de los dos puntos y es posible indicar el color.

Después de crear la ventana principal, se crea el canvas con `tk.Canvas` y se indica el widget que lo va a contener `ventana`. Además, se usaron las opciones `bd` y `bg`, la primera permite crear un borde en el canvas y la segunda permite seleccionar el color del fondo.

[Aquí](https://www.tutorialspoint.com/python3/tk_canvas.htm) para ver más opciones de Canvas.
